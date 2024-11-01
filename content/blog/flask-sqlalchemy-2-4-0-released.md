~~~~toml
title = "Flask-SQLAlchemy 2.4.0 Released"
author_name = "Randy Syring"
published = 2019-04-24
tags = ["releases"]
~~~~

Flask-SQLAlchemy 2.4.0. has been released. The
[changelog](https://flask-sqlalchemy.palletsprojects.com/page/changes/#version-2-4-0)
lists the changes in detail, which include:

* Make SQLAlchemy engine configuration more flexible
* Address SQLAlchemy 1.3 deprecations

## Deprecation Warnings

New deprecation warnings have been added for configuration and `__init__` params that
are no longer needed due to the engine configuration now being more customizable. Those
options will be removed in release 3.0.

## Install or Upgrade

Install from [PyPI](https://pypi.org/project/Flask-SQLAlchemy/) with pip:

    pip install -U Flask-SQLAlchemy
