~~~~toml
title = "Werkzeug 0.15.5 Released"
author_name = "David Lord"
published = 2019-07-17
tags = ["releases", "security"]
~~~~

Werkzeug 0.15.5 has been released, containing bug and security fixes.
The [changelog][] lists the changes in detail, which include:

* `SharedDataMiddleware` safely handles drive names in paths on Windows.
* The reloader no longer causes an `Exec format error` in many common
  situations.
* The reloader works around an issue when using the pydev debugger.

[changelog]: https://werkzeug.palletsprojects.com/page/changes/#version-0-15-5

## Security fix for `SharedDataMiddleware` on Windows

Prior to 0.15.5, it was possible for a third party to potentially access
arbitrary files when the application used `SharedDataMiddleware` on
Windows. This issue was
assigned [CVE-2019-14322](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-14322).

Due to the way Python's `os.path.join()` function works on Windows, a
path segment with a drive name will change the drive of the final path.
This was [previously addressed][pa] in the `safe_join()` function in
[Werkzeug 0.12.2][pa], but `SharedDataMiddleware` used a separate
implementation and so was not secured by the previous fix.

`SharedDataMiddlware` now uses `safe_join()` when fetching requested
files. Projects using `SharedDataMiddleware` on Windows should update
as soon as possible to receive the fix.

Thank you to [Emre Övünç][c1] and [Olivier Dony][c2] for responsibly
reporting the issue. If you think you have discovered a security issue
in Werkzeug or another of the Pallets projects, please email
<security@palletsprojects.com> with details.

[pa]: flask-werkzeug-0-12-2-security-release.md

[c1]: mailto:byemre.ovunc@gmail.com

[c2]: mailto:security@odoo.com

## Install or Upgrade

Install from [PyPI](https://pypi.org/project/Werkzeug/) with pip:

    pip install -U Werkzeug
