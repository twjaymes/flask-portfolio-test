~~~~toml
title = "Jinja 2.8.1 Security Release"
author_name = "Armin Ronacher"
published = 2016-12-29
tags = ["releases", "security"]
~~~~

We just pushed out a new release for Jinja (2.8.1) which includes a security related
fix. If you are using the Jinja2 sandbox you are encouraged to upgrade or alternatively
manually further lock down the sandbox.

The core of the issue is that Python's string format method that was added to strings
can be used to discover potentially dangerous values including configuration values:

```pycon
>>> config = {'SECRET_KEY': '12345'}
>>> class User(object):
...  def __init__(self, name):
...   self.name = name
...
>>> user = User('joe')
>>> '{0.__class__.__init__.__globals__[config]}'.format(user)
"{'SECRET_KEY': '12345'}"
```

For this reason *you must never let user supply format strings* in raw Python as its
too easy to escape them. However specifically for the Jinja2 sandbox we changed the
behavior now that we're using the same sandboxing functionality that Jinja2 uses
for its own runtime also for Python string formatting.

This means that with 2.8.1 and higher templates from sandboxed environments will
intercept format strings the same way as with normal cases:

```pycon
>>> from jinja2.sandbox import SandboxedEnvironment
>>> env = SandboxedEnvironment()
>>> class User(object):
...  def __init__(self, name):
...   self.name = name
...
>>> t = env.from_string(
...  '{{ "{0.__class__.__init__.__globals__}".format(user) }}')
>>> t.render(user=User('joe'))
Traceback (most recent call last):
  ...
jinja2.exceptions.SecurityError: ...
```

If you don't want or you cannot upgrade Jinja2, you can override the `is_safe_attribute`
method on the sandbox and explicitly disallow all `format` attributes on strings.

Thank you to [Olivier Dony](https://twitter.com/odony) for reporting the issue.
