~~~~toml
title = "Werkzeug 0.14 Released"
author_name = "Armin Ronacher"
published = 2017-12-31
tags = ["releases"]
~~~~

The Pallets team is pleased to release [Werkzeug](https://werkzeug.palletsprojects.com)
0.14. Changes include:

- Improved the usefulness of `Request.application` by automatically handling HTTP
  exceptions.
- Added support for platforms that lack `SpooledTemporaryFile`. This primarily affects
  GAE users which were unable to use 0.13 due to this missing API.
- Add support for etag handling through if-match
- Added support for the SameSite cookie attribute along with better support for invalid
  cookies.
- Added a HTTP proxying middleware (`werkzeug.wsgi.ProxyMiddleware`)
- Various improvements for the reloader.
- The built-in HTTP server will no longer close a connection in cases
  where no HTTP body is expected (204, 204, HEAD requests etc.)
- Werkzeug will no longer send the content-length header on 1xx or
  204/304 responses.
- Added support for static weights in URL rules.
- Better handle some more complex reloader scenarios where sys.path
  contained non directory paths.

[Read the full changelog.](https://werkzeug.palletsprojects.com/page/changes/#version-0-14)

### Install or upgrade

Install from [PyPI](https://pypi.org/project/Werkzeug/0.14/) with pip:

```
pip install -U Werkzeug
```

### Get Involved

Werkzeug and the Pallets team depends on you, the community. Whether you report issues,
write documentation, create patches, or answer questions, we appreciate all the help you
provide. We updated
the [contributing guide](https://github.com/pallets/werkzeug/blob/master/CONTRIBUTING.rst)
to help make it easier to get started.
