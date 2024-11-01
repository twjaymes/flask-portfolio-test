~~~~toml
title = "Flask 0.12 released"
author_name = "Markus Unterwaditzer"
published = 2016-12-21
tags = ["releases"]
~~~~

Flask 0.12 has been released. This is not as big a step as 0.11 has been, the only
intentionally backwards-incompatible change is with regards to `send_file`'s behavior,
which, when invoked as `send_file(f)` with `f` being a file-like object, no longer
guesses the MIME-type from `f.name`. You have to pass a filepath instead.

Special thanks to [Kyle Lawlor](https://github.com/wgwz) for fixing up most
documentation after the `flask` CLI got introduced.

## Changelog

- the cli command now responds to `--version`.
- Mimetype guessing and ETag generation for file-like objects in ``send_file``
  has been removed, as per issue ``#104``. See pull request ``#1849``.
- Mimetype guessing in ``send_file`` now fails loudly and doesn't fall back to
  ``application/octet-stream``. See pull request ``#1988``.
- Make ``flask.safe_join`` able to join multiple paths like ``os.path.join``
  (pull request ``#1730``).
- Revert a behavior change that made the dev server crash instead of returning
  a Internal Server Error (pull request ``#2006``).
- Correctly invoke response handlers for both regular request dispatching as
  well as error handlers.
- Disable logger propagation by default for the app logger.
- Add support for range requests in ``send_file``.
- ``app.test_client`` includes preset default environment, which can now be
  directly set, instead of per ``client.get``.
