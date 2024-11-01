~~~~toml
title = "MarkupSafe 1.1.0 Released"
author_name = "David Lord"
published = 2018-11-05
tags = ["releases"]
~~~~

[Changelog](https://markupsafe.palletsprojects.com/page/changes/)

* Dropped support for Python 2.6 and 3.3.
* Using newer CPython APIs gave the C extension a 1.5x speedup on Python 3. Python 2
  will still get the same speed as before, but you should consider upgrading if
  possible.
* The `escape` function uses the `__html__` method on an object if it's available. It
  will now ensure that result is wrapped in the `Markup` class, for consistency with
  other behavior.

## Platform Wheels

Installing from PyPI with pip will now install a precompiled wheel if available. Wheels
have been compiled for supported CPython versions on Linux, Mac, and Windows.

MarkupSafe comes with a C extension that adds a significant speedup to escaping.
However, if a compiler or headers aren't available, the install will fall back to a
native Python implementation. Previously, the user would see no indication that they
didn't get the speedups, or would see confusing error messages even though the install
succeeded. Now, many more users will be able to take advantage of the speedups provided
by MarkupSafe without extra configuration.

## Documentation

Full documentation has been added in place of the previous README. It is available
through Read the Docs at https://markupsafe.palletsprojects.com/.

## Install or Upgrade

Install from [PyPI](https://pypi.org/project/MarkupSafe) with pip:

    pip install -U MarkupSafe

## Donate

We accept donations through the Python Software Foundation in order to support our
efforts to maintain the projects and grow the
community. [Click here to donate.](../donate.md)
