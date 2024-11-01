~~~~toml
title = "Jinja 2.10.1 Security Release"
author_name = "David Lord"
published = 2019-04-06
tags = ["releases", "security"]
~~~~

Jinja 2.10.1 has been released and includes a security-related fix. If
you are using the Jinja [sandboxed environment][] you are encouraged to
upgrade.

MITRE has assigned [CVE-2019-10906][] to this issue.

Thank you to [Brian Welch][] for responsibly reporting the issue, and to
[Armin Ronacher][] for writing the fix.

The sandbox is used to restrict what code can be evaluated when
rendering untrusted, user-provided templates. Due to the way string
formatting works in Python, the `str.format_map` method could be used to
escape the sandbox.

This issue was previously addressed for the `str.format` method in
[Jinja 2.8.1][], which discusses the issue in detail. However, the
less-common `str.format_map` method was overlooked. This release applies
the same sandboxing to both methods.

If you cannot upgrade Jinja, you can override the `is_safe_attribute`
method on the sandbox and explicitly disallow the `format_map`
method on string objects.

## Reporting Security Issues

If you think you have discovered a security issue in Jinja or another of
the Pallets projects, please email <security@palletsprojects.com> with
details.

[sandboxed environment]: http://jinja.pocoo.org/docs/2.10/sandbox/

[CVE-2019-10906]: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-10906

[Brian Welch]: https://brianwel.ch

[Armin Ronacher]: https://twitter.com/mitsuhiko

[Jinja 2.8.1]: ../jinja-281-released/
