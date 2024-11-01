~~~~toml
title = "Jinja 2.9 Released"
author_name = "Armin Ronacher"
published = 2017-01-07
tags = ["releases"]
~~~~

After a long time of no changes a new release, 2.9 codename “Derivation” of the Jinja
template engine for Python is out. This change is probably the biggest release in
Jinja2's history and it requires a bit of explanation of why it happened and why it
happened now. But first let's cover the big changes in it.

## New Identifier Tracking

This appears to be an under the hood change because it effectively just changes the
internal algorithm that Jinja2 uses to map it's own scoping rules onto the Python
interpreter's scoping rules but it has wide ranging consequences. The original tracking
issue [goes back to 2011](https://github.com/pallets/jinja/issues/19) and was created as
a long running TODO item. There were a few reasons why it was implemented this way but
over the years it became clearer and clearer that the method chosen for mapping
identifiers is just causing too many issues. The reason it was not changed was that the
worries were too big that people accidentally relied on such bugs.

However with improved support for pinning to older versions of Python packages and the
fact that people no longer use linux distribution provided packages much the worries
about greater changes are heavily reduced. With Jinja 2.9 the identifier tracking was
completely changed which should squash pretty much all the weird behaviors developers
might have encountered and also enabled support for related improvements. In particular
the new identifier tracking generalized the context behavior for includes and imports.

In the ideal case you won't notice anything other than that some constructs are possible
now that caused errors in the past.

## Python 3 Feature Support

While Jinja2 supported Python 3 for years now it never really embraced functionality
that the language provides on 3.x that it does not do on 2.x. Largely that is caused by
the fact that we want templates to be compatible between 2.x and 3.x (this is true only
for as long as template variables are restricted to ASCII characters). However 3.6 now
added async generators which permits Jinja2 to fully support the `async` and `await`
keywords on 3.6 and later.

In particular it means that you can now return coroutines from functions passed to
Jinja2 templates and the template engine will automatically await them. Likewise all
filters were updated to work with iterators as well as async iterators alike.

Additionally Jinja2 now emits `generator_stop` as a future flag which means that
accidentally emitting `StopIteration` from a filter or other code will no longer cause
the template to just stop rendering silently. This was enabled
by [PEP 479](https://www.python.org/dev/peps/pep-0479/).

## Policy Framework

Jinja2 now has an internal policy configuration which permits one to centrally
reconfigure behavior of filters and other things. While so far not much can be
reconfigured it will greatly support future improvements. This also finally allows us to
provide a default `tojson` filter which previously was only available through Flask or
other frameworks. Through the policy configuration the particular form of JSON
serialization can be customized and replaced.

## Full Changelog

- Change cache key definition in environment. This fixes a performance
  regression introduced in 2.8.
- Added support for `generator_stop` on supported Python versions
  (Python 3.5 and later)
- Corrected a long standing issue with operator precedence of math operations
  not being what was expected.
- Added support for Python 3.6 async iterators through a new async mode.
- Added policies for filter defaults and similar things.
- urlize now sets "rel noopener" by default.
- Support attribute fallback for old-style classes in 2.x.
- Support toplevel set statements in extend situations.
- Restored behavior of Cycler for Python 3 users.
- Subtraction now follows the same behavior as other operators on undefined
  values.
- `map` and friends will now give better error messages if you forgot to
  quote the parameter.
- Depend on MarkupSafe 0.23 or higher.
- Improved the `truncate` filter to support better truncation in case
  the string is barely truncated at all.
- Change the logic for macro autoescaping to be based on the runtime
  autoescaping information at call time instead of macro define time.
- Ported a modified version of the `tojson` filter from Flask to Jinja2
  and hooked it up with the new policy framework.
- Block sets are now marked `safe` by default.
- On Python 2 the asciification of ASCII strings can now be disabled with
  the `compiler.ascii_str` policy.
- Tests now no longer accept an arbitrary expression as first argument but
  a restricted one. This means that you can now properly use multiple
  tests in one expression without extra parentheses. In particular you can
  now write ``foo is divisibleby 2 or foo is divisibleby 3``
  as you would expect.
- Greatly changed the scoping system to be more consistent with what template
  designers and developers expect. There is now no more magic difference
  between the different include and import constructs. Context is now always
  propagated the same way. The only remaining differences is the defaults
  for `with context` and `without context`.
- The `with` and `autoescape` tags are now built-in.
- Added the new `select_autoescape` function which helps configuring better
  autoescaping easier.

## Why an Update now?

One of the reasons Jinja2 was lying largely dormant is that it's always scary to touch
something so many people use. While bugs were known for quite some time it requires
careful changes to not change all the template code out there. In particular once salt
and ansible started using Jinja it became a big emotional burden to do changes on it.

However it turns out that emotional burden does not get smaller for as long as those
bugs are in there. Going in and cleaning up the behavior actually turns out to be
healthier in the long run. Now even if this release introduces regressions in behavior,
the internal code quality is much improved and reasoning about the runtime and compiler
is a lot easier now.

On a personal note I'm happy to see how popular Jinja has become and I hope that with
this release it becomes more enjoyable to write Jinja templates.

*Aside: if you are downloading Jinja2 you will actually pull 2.9.1 because there was a
regression in 2.9 that was only found after releasing it. In an ironic twist it was
found when this website attempted to render a complex template with Jinja 2.9 on the
build server.*
