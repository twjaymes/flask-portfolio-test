~~~~toml
title = "Flask 0.12.3 Released"
author_name = "David Lord"
published = 2018-04-26
tags = ["releases", "security"]
~~~~

This release includes an important security fix for JSON and a minor backport for CLI
support in PyCharm. It is provided for projects that cannot update to Flask 1.0
immediately. See the [1.0 announcement](flask-1-0-released.md) and update to it instead
if possible.

## JSON Security Fix

Flask previously decoded incoming JSON bytes using the content type of the request.
Although JSON should only be encoded as UTF-8, Flask was more lenient. However, Python
includes non-text related encodings that could result in unexpected memory use by a
request.

Flask will now detect the encoding of incoming JSON data as one of the supported UTF
encodings, and will not allow arbitrary encodings from the request.

## Upgrade

Upgrade from [PyPI](https://pypi.org/project/Flask/) with pip. Use a version identifier
if you want to stay at 0.12:

    pip install -U Flask==0.12.3

Or upgrade to 1.0:

    pip install -U Flask
