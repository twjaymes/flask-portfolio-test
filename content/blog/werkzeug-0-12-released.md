~~~~toml
title = "Werkzeug 0.12 released"
author_name = "Markus Unterwaditzer"
published = 2017-03-10
tags = ["releases"]
~~~~

We just released Werkzeug 0.12. Highlights from the changelog:

## Further deprecation of Werkzeug's `script` module

Werkzeug's script module was deprecated since 2011. Deprecation slipped through
the cracks, so we now additionally show large warnings at runtime. [Head over
to the bugtracker](https://github.com/pallets/werkzeug/issues/1079) for the
rest of the plan.

## Defaults for password hashing changed

Password hashing now [uses `sha256` by default instead of
`sha1`](https://github.com/pallets/werkzeug/pull/753). On a related note,
certificates generated with the dev server are now [signed with `sha256`
instead of `md5`](https://github.com/pallets/werkzeug/pull/1004).
