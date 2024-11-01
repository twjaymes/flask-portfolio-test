~~~~toml
title = "Jinja 2.11.0 Released"
author_name = "David Lord"
published = 2020-01-27
tags = ["releases"]
~~~~

The Pallets team is pleased to release [Jinja](https://jinja.palletsprojects.com) 2.11.0.
[Read the changelog](https://jinja.palletsprojects.com/page/changes#version-2-11-0)
for the full list of changes. Some of the bigger changes include:

* Drop support for Python 2.6, 3.3, and 3.4. This will be the last
  version to support Python 2.7 and 3.5.
* A new `jinja2.ext.debug` extension adds a ``{% debug %}`` tag to
  quickly dump the current template context.
* A new `ChainableUndefined` type allows silently ignoring attribute
  access on undefined variables.
* Loop context variables like `loop.length` and `loop.nextitem` work
  better in both sync and async environments.
* Improved compile and runtime performance.

## Version 3.0 Coming Soon

As outlined in [Ending Python 2 Support](ending-python2-support.md),
2.11.x will be the last version to support Python 2.7 and 3.5. The next
version will be 3.0 and will support Python 3.6 and newer.

The package name will remain "Jinja2" and imports will remain `jinja2`.
"Jinja2 3.0" looks a little weird, but given the years of community
momentum behind the name, we concluded it was less disruptive to keep it
as-is.

## Install or Upgrade

Install from [PyPI](https://pypi.org/project/Jinja2/) with pip:

    pip install -U Jinja2

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

[Learn more.](https://tidelift.com/subscription/pkg/pypi-jinja2?utm_source=pypi-jinja2&utm_medium=referral&utm_campaign=enterprise)
