~~~~toml
title = "Werkzeug 1.0.0 Released"
author_name = "David Lord"
published = 2020-02-06
tags = ["releases"]
~~~~

The Pallets team is pleased to release Werkzeug 1.0. Werkzeug is the
low-level WSGI and HTTP toolkit that powers Flask. It's been almost 13
years since the first commit, and this milestone for the project brings
many fixes and
changes. [Read the full changelog](https://werkzeug.palletsprojects.com/page/changes/#version-1-0-0)
to understand what may affect your code when upgrading.

- Drop support for Python 3.4. This will be the last version to
  support Python 2.7 and 3.5.
- Remove most top-level attributes provided by the `werkzeug` module
  in favor of direct imports. If you haven't already, use
  [version 0.16](werkzeug-0-16-0-released.md) first to see
  deprecation warnings while upgrading.
- Cookies support the ``samesite='None'`` option. Cookies are parsed
  as a `MultiDict` instead of overwriting repeated keys.
- The development server supports 2-way TLS, making it easier to
  develop applications that inspect client certificates.
- When building URLs with host matching, the current host is accounted
  for when deciding what rule to build.
- When defining and matching URL rules, consecutive slashes are merged
  by default to match the behavior of common HTTP servers.
- The `Accept` header preserves order for tags with equal quality and
  considers options on each value. The  `Accept-Language` header can
  match the primary tag if the specific value is not present.
- Added CORS header attributes to `Request` and `Response`.
- A URL rule can be marked as a `websocket`, in which case it will
  only match for `wss://` requests. This allows async web frameworks
  to use Werkzeug for routing.

## Version 2.0 Coming Soon

As outlined in [Ending Python 2 Support](ending-python2-support.md),
1.0.x will be the last version to support Python 2.7 and 3.5. The next
version will be 2.0 and will support Python 3.6 and newer.

## Install or Upgrade

Install from [PyPI](https://pypi.org/project/Werkzeug/) with pip:

    pip install -U Werkzeug

## Donate to Support Pallets

The Pallets organization accepts donations as part of the non-profit
Python Software Foundation (PSF). Donations through the PSF support our
efforts to maintain the projects and grow the community.

[Click here to donate. ❤](../donate.md)

## For Enterprise

The Pallets team and thousands of other packages are working with
Tidelift to deliver commercial support and maintenance for the open
source dependencies you use to build your applications. Save time,
reduce risk, and improve code health, while paying the maintainers of
the exact dependencies you use.

[Learn more.](https://tidelift.com/subscription/pkg/pypi-werkzeug?utm_source=pypi-werkzeug&utm_medium=referral&utm_campaign=enterprise)
