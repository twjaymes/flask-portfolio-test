~~~~toml
title = "New Flask, Jinja2, Click, Werkzeug, ItsDangerous, and MarkupSafe major release candidates"
author_name = "Philip Jones"
published = 2021-04-29
tags = ["releases"]
~~~~

The Pallets team is pleased to announce that release candidates are
now available for the next major version of each project.

Check out the changelogs for every project to see what's new:

- [Flask 2.0](https://flask.palletsprojects.com/page/changes#version-2-0-0)
- [Jinja2 3.0](https://jinja.palletsprojects.com/page/changes/#version-3-0-0)
- [Click 8.0](https://click.palletsprojects.com/page/changes/#version-8-0)
- [Werkzeug 2.0](https://werkzeug.palletsprojects.com/page/changes/#version-2-0-0)
- [ItsDangerous 2.0](https://itsdangerous.palletsprojects.com/page/changes/#version-2-0-0)
- [MarkupSafe 2.0](https://markupsafe.palletsprojects.com/page/changes/#version-2-0-0)

Please help us prepare for the final release by testing the prerelease
versions and reporting any issues you have. To upgrade to pre-releases
with pip, use the `--pre` flag, e.g.:

    pip install -U --pre Flask

These new major versions all drop support for Python 2 and 3.5,
requiring Python 3.6 as the minimum supported version.

## Release highlights

These are a few highlights, see the changelogs linked above for the
full release details. More detailed posts about each project's
highlights will be made with the final releases.

- All projects (Jinja coming soon) now provide type hints.
- Flask gains limited `async`/`await` support.
- Flask supports nested blueprints.
- Flask tells the browser to cache static files more intelligently, so
  changes to CSS or images show up immediately.
- Flask introduces short form route decorators, such as `@app.post()`
  as a shortcut for `@app.route(methods=["POST"])`.
- Click's shell completion system has been rewritten.
- Click will now prompt for values where they are omitted.
- Werkzeug now provides `send_file` and `send_from_directory` helpers.
- Werkzeug's test client always returns a `Response` object.
- Werkzeug's multipart parsing performance increases by a factor of 15.

## Release date

The Pallets team is aiming to release on or before PyCon 2021, i.e. a
target release date of the 11th of May 2021.
