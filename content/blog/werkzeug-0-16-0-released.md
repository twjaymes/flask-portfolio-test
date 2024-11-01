~~~~toml
title = "Werkzeug 0.16.0 Released"
author_name = "David Lord"
published = 2019-09-19
tags = ["releases"]
~~~~

Werkzeug 0.16.0 has been released. The only change is that most of the
top-level attributes in the `werkzeug` module are now deprecated, and
will be removed in 1.0.0.

For example, instead of `import werkzeug; werkzeug.url_quote`, do
`from werkzeug.urls import url_quote`. If you are using these imports in
your project, a deprecation warning will show the correct import to use.
`werkzeug.exceptions` and `werkzeug.routing` should also be imported
instead of accessed, but for technical reasons can’t show a warning.

These imports were supported by patching the `werkzeug` module to
support lazy imports, but the implementation added complexity, and there
was no clear design reason why some things were available and some
weren't. It also masked some circular dependency issues. IDEs like
PyCharm didn't know those lazy imports existed and were already
correctly using the full imports.
