~~~~toml
title = "MarkupSafe 1.1.1 Released"
author_name = "David Lord"
published = 2019-02-23
tags = ["releases"]
~~~~

This is a bugfix release. [Changelog](https://markupsafe.palletsprojects.com/page/changes/)

* If an `__html__` method raised an exception, Python would segfault when using
  MarkupSafe's C speedups. Now the exception will propagate correctly rather than
  crashing.

## Install or Upgrade

Install from [PyPI](https://pypi.org/project/MarkupSafe) with pip:

    pip install -U MarkupSafe
