~~~~toml
title = "Flask 0.11 Released"
author_name = "Armin Ronacher"
published = 2016-05-29
tags = ["releases"]
~~~~

After a very long, long waiting time Flask finally got a new release. There
really was no good reason that there has not been a release in such a long time
but unfortunately once things are postponed for too long a certain release
anxiety kicks in.

In this case this was long tagged as 1.0 but we decided for renaming it to
0.11 and back out some of the more controversial changes. In particular the
new command line interface for Flask was modified a bit to not depend on some
specific functionality in the supporting Click library.

Highlights of this release are the improved development experience which now
stalls the browser on reload instead of bringing up a "connection reset"
page and the new command line support.

## Future Plans

This is also the first Flask release under the new pallets organization and
from now on we hope to bring you releases more frequently. Ideally with the
next release we also update the website to find a new home for the showcase,
flask extension list as well as the snippet section to allow the community to
take care of those things themselves.

## Changelog

- Added support to serializing top-level arrays to `flask.jsonify`. This
  introduces a security risk in ancient browsers. See
  [json-security](https://flask.palletsprojects.com/page/web-security/#json-security)
  for details.
- Added before_render_template signal.
- Added `**kwargs` to `flask.Test.test_client` to support passing
  additional keyword arguments to the constructor of
  `flask.Flask.test_client_class`.
- Added `SESSION_REFRESH_EACH_REQUEST` config key that controls the
  set-cookie behavior. If set to `True` a permanent session will be
  refreshed each request and get their lifetime extended, if set to
  `False` it will only be modified if the session actually modifies.
  Non permanent sessions are not affected by this and will always
  expire if the browser window closes.
- Made Flask support custom JSON mimetypes for incoming data.
- Added support for returning tuples in the form `(response, headers)`
  from a view function.
- Added `flask.Config.from_json`.
- Added `flask.Flask.config_class`.
- Added `flask.config.Config.get_namespace`.
- Templates are no longer automatically reloaded outside of debug mode. This
  can be configured with the new `TEMPLATES_AUTO_RELOAD` config key.
- Added a workaround for a limitation in Python 3.3's namespace loader.
- Added support for explicit root paths when using Python 3.3's namespace
  packages.
- Added the `flask` command and the `flask.cli` module to start the local
  debug server through the click CLI system. This is recommended over the old
  `flask.run()` method as it works faster and more reliable due to a
  different design and also replaces `Flask-Script`.
- Error handlers that match specific classes are now checked first,
  thereby allowing catching exceptions that are subclasses of HTTP
  exceptions (in `werkzeug.exceptions`). This makes it possible
  for an extension author to create exceptions that will by default
  result in the HTTP error of their choosing, but may be caught with
  a custom error handler if desired.
- Added `flask.Config.from_mapping`.
- Flask will now log by default even if debug is disabled. The log format is
  now hardcoded but the default log handling can be disabled through the
  `LOGGER_HANDLER_POLICY` configuration key.
- Removed deprecated module functionality.
- Added the `EXPLAIN_TEMPLATE_LOADING` config flag which when enabled will
  instruct Flask to explain how it locates templates. This should help
  users debug when the wrong templates are loaded.
- Enforce blueprint handling in the order they were registered for template
  loading.
- Ported test suite to py.test.
- Deprecated `request.json` in favour of `request.get_json()`.
- Add "pretty" and "compressed" separators definitions in jsonify() method.
  Reduces JSON response size when JSONIFY_PRETTYPRINT_REGULAR=False by removing
  unnecessary white space included by default after separators.
- JSON responses are now terminated with a newline character, because it is a
  convention that UNIX text files end with a newline and some clients don't
  deal well when this newline is missing. See
  https://github.com/pallets/flask/pull/1262 -- this came up originally as a
  part of https://github.com/kennethreitz/httpbin/issues/168
- The automatically provided `OPTIONS` method is now correctly disabled if
  the user registered an overriding rule with the lowercase-version
  `options` (issue [`#1288`](https://github.com/pallets/flask/issues/1288)).
- [`flask.json.jsonify`](https://flask.palletsprojects.com/page/api/#flask.json.jsonify)
  now supports the `datetime.date` type (pull request
  [`#1326`](https://github.com/pallets/flask/pull/1326)).
- Don't leak exception info of already caught exceptions to context teardown
  handlers (pull request [`#1393`](https://github.com/pallets/flask/pull/1393)).
- Allow custom Jinja environment subclasses (pull
  request [`#1422`](https://github.com/pallets/flask/pull/1422)).
- [`flask.g`](https://flask.palletsprojects.com/page/api/#flask.g) now has `pop()`
  and `setdefault` methods.
- Turn on autoescape for `flask.templating.render_template_string` by default
  (pull request [`#1515`](https://github.com/pallets/flask/pull/1515)).
- `flask.ext` is now deprecated (pull
  request [`#1484`](https://github.com/pallets/flask/pull/1484)).
- [`send_from_directory`](https://flask.palletsprojects.com/page/api/#flask.send_from_directory)
  now raises BadRequest if the filename is invalid on
  the server OS (pull request [`#1763`](https://github.com/pallets/flask/pull/1763)).
- Added the `JSONIFY_MIMETYPE` configuration variable (pull
  request [`#1728`](https://github.com/pallets/flask/pull/1728)).
- Exceptions during teardown handling will no longer leave bad application
  contexts lingering around.
