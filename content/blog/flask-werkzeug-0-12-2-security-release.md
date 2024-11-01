~~~~toml
title = "Security bugs on Windows servers: Flask 0.12.2 and Werkzeug 0.12.2 released"
author_name = "Markus Unterwaditzer"
published = 2017-05-16
tags = ["releases", "security"]
~~~~

Flask 0.12.2 and Werkzeug 0.12.2 have been released. They contain the same
**security bugfix** for the `safe_join` function in each package.

The problem only occurs if you are running your application on a Windows
server.

## Details

[David Lord](https://github.com/davidism) initially found this bug (thanks!)
and disclosed it to the other maintainers in a private email:

> While going through PR #2059 about safe_join, I looked up Python's `ntpath.join`
> and discovered a vulnerability that `safe_join` on Windows doesn't cover.
>
> https://docs.python.org/3/library/os.path.html#os.path.join:
> "`os.path.join("c:", "foo")` represents a path relative to the current
> directory on drive C: `(c:foo)`"
>
> `safe_join('\\root\\path', 'd:', 'test.txt')` would break out of the trusted
> root directory and instead take the test file relative to the cwd on the d
> drive. This doesn't give completely arbitrary path access, since it's
> limited to the cwd, but it's still not good.

For the application developer this means that endpoints using `safe_join` could
potentially be used to disclose arbitrary files in the server processes'
current working directory on Windows.

## What happens next

We strongly recommend upgrading to Flask 0.12.2 and Werkzeug 0.12.2, as this
bug has been fixed there ([Flask](https://github.com/pallets/flask/pull/2284),
[Werkzeug](https://github.com/pallets/werkzeug/commit/2497866d7eafa64ca5eb4fb3d1747c05036bf318)).

A CVE has been requested on `Tue, 16 May 2017 06:51:09 +0000`, the CVE `CVE-2017-9088`
was assigned.
