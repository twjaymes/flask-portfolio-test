~~~~toml
title = "Werkzeug 0.15.0 Released"
author_name = "David Lord"
published = 2019-03-19
tags = ["releases"]
~~~~

The Pallets team is pleased to release Werkzeug 0.15.0. This represents
over a year of work from the community and maintainers, and as such
there is an unusually long list of changes. Some of the notable ones
are listed below, but there are many more throughout the framework.
[Read the full changelog](https://werkzeug.palletsprojects.com/page/changes/)
to understand what changes may affect your code when upgrading.

* Building URLs is ~7x faster.
* Redirects now use HTTP code 308 by default. This preserves the method
  and form data.
* `int` and `float` URL converters can handle negative numbers.
* The debugger saw a number of improvements. Python 3's chained
  exceptions are correctly displayed and logged. Frames of user code
  are highlighted to make it easier to read tracebacks.
* The reloader is much better at detecting how to re-run itself. It
  handles `python -m` as well as non-Python executable scripts.
* The test client takes a `json` parameter, and the response class has
  a `get_json` method. This makes testing JSON APIs much more
  straightforward.
* URLs with Unicode or percent-escapes are handled better. Quoting when
  converting between URIs and IRIs is more consistent, and the unquoted
  URL is logged by the dev server rather than showing percent escapes.
* Deprecation warnings have been added throughout the code in
  preparation for version 1.0.
* Werkzeug now uses [pre-commit][], [black][], [reorder-python-imports][],
  and [flake8][] to provide consistent code formatting. The code also
  moved to a `src` directory layout.
* And much more!

[pre-commit]: https://pre-commit.com/

[black]: https://black.readthedocs.io/en/stable/

[reorder-python-imports]: https://github.com/asottile/reorder_python_imports

[flake8]: http://flake8.pycqa.org/en/latest/

## `werkzeug.contrib` has been deprecated

The code under the `werkzeug.contrib` package has been deprecated. In
version 1.0, code will either be moved into `werkzeug` core, or will be
removed completely. Contrib started as a place to put code that wasn't
clear where it belonged. In the 12 years since Werkzeug started, the
packaging ecosystem and Werkzeug's codebase have evolved. The contrib
code has not been widely maintained, often having better implementations
elsewhere or no longer being required.

* `ProxyFix`, `LintMiddleware`, and `ProfilerMiddleware` have moved into
  `werkzeug.middleware`.
* `securecookie` and `sessions` have been extracted to the
  [pallets/secure-cookie](https://github.com/pallets/secure-cookie)
  repository.
* `cache` has been extracted to the
  [pallets/cachelib](https://github.com/pallets/cachelib) repository.
* Everything else is deprecated.

## Deprecation Warnings

Besides contrib, many other parts of Werkzeug have been marked, either
explicitly or implicitly, as deprecated, for many years. This release
ensures that every occurrence issues a clear deprecation warning that
mentions when the code will be removed. Currently, everything marked
deprecated is slated to be removed in version 1.0.

* Unused compatibility imports for code that was moved to another module
  within Werkzeug. This code is still available, but should be imported
  from the correct location.
* Middleware in `werkzeug.wsgi` has moved to `werkzeug.middleware`.
* The `werkzeug.wrappers` module was converted to a package of more
  specific modules. Imports for classes that were publicly documented in
  the previous version will work without change.

## Install or Upgrade

Install from [PyPI](https://pypi.org/project/Werkzeug/) with pip:

    pip install -U Werkzeug

## Donate

The Pallets organization has joined the Python Software Foundation. We
now accept donations through the PSF in order to support our efforts to
maintain the projects and grow the community.
[Click here to donate.](../donate.md)
