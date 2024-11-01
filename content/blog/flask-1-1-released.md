~~~~toml
title = "Flask 1.1 Released"
author_name = "David Lord"
published = 2019-07-04
tags = ["releases"]
~~~~

The Pallets team is pleased to release [Flask](https://flask.palletsprojects.com) 1.1.
The latest version is 1.1.1. Version 1.0.4 was also released.

- Drop support for Python 3.4.
- Bump minimum Werkzeug version to 0.15.
- The way error handlers for `InternalServerError` and `500` work has
  been made more consistent. See below for more information.
- `app.logger` once again takes the same name as `app.name`, reverting
  1.0.x's behavior of hard-coding `"flask.app"`. See below for more
  information.
- `jsonify` supports
  Python's [`dataclasses`](https://docs.python.org/3/library/dataclasses.html).
- Returning a `dict` from a view function will produce a JSON
  response. This makes it even easier to get started building an API.
- A clearer error message is shown when a view returns an unsupported
  type.
- URL routing is performed after the request context is pushed. This
  allows custom URL converters to access `current_app` and `request`.
  This makes it possible to implement converters such as one that
  queries the database for a model based on the ID in the URL.
- CLI commands can be registered with blueprints using the new
  `bp.cli` attribute. These will be available as nested commands, for
  example `flask user create`.

[**Read the changelog**](https://flask.palletsprojects.com/page/changes/)
for the full list of changes. Be sure to check the notes for the 1.0.x
versions as well.

## Change to Error Handling

Prior to 1.0, unhandled errors caused a generic `InternalServerError` to
be returned, but only the handler for `500` was looked up for that, and
the original error was passed to it. 1.0 made `500` an alias for
`InternalServerError`, but these inconsistencies caused confusion over
what errors were passed to what handlers.

As of 1.1, an error handler registered for `InternalServerError` or
`500` means the same thing in all cases. It will always be passed an
instance of `InternalServerError`, even if it was caused by an unhandled
error of another type. The original error is available as
`e.original_exception`.

If your project uses a `500` error handler that expects any exception to
be passed to it, it should use `e.original_exception` instead of `e`.

## Change to Logging

In 1.0, Flask's logging setup was greatly simplified. Part of that was
hard-coding the name `"flask.app"` for the logger. However, that made it
less clear whether Flask or the app was doing the logging, and made it
impossible to distinguish between multiple apps in logs.

As of 1.1, `app.logger` again takes the same name as `app.name`. Flask
will warn you if it detects logging configuration for `"flask"` or
`"flask.app"` so you can rename that configuration appropriately.

For example, if your project is named `example.py` and you initialize
your Flask app as `Flask(__name__)`, then the logger will be named
`"example"`.

## Install or Upgrade

Install from [PyPI](https://pypi.org/project/Flask/) with pip:

    pip install -U Flask

## Donate

Pallets now accepts donations through the PSF in order to support our
efforts to maintain the projects and grow the community. We greatly
appreciate any support you can provide.
[**Click here to donate.**](../donate.md)
