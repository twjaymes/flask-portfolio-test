~~~~toml
title = "Ending Python 2 Support"
author_name = "David Lord"
published = 2019-12-17
tags = ["meta"]
~~~~

Upstream support for Python 2.7 is ending on [January 1, 2020][pep].
Pallets is joining the [community of open source projects][community]
ending support for Python 2 at that time. Our statement and support plan
are based on [PyTest's announcement][pytest].

We will be dropping support for Python 2.7 as well as Python 3.5 and
below, as their support windows have ended or will end around the same
time. Future releases of each Pallets project will only support Python
versions still supported upstream, which can be found in the
[Python Developer's Guide][devguide].

The last version branch of each core project to support Python 2.7
and Python 3.5 are:

* Flask 1.1.x
* Werkzeug 1.0.x
* Click 7.x
* Jinja 2.11.x
* ItsDangerous 1.1.x
* MarkupSafe 1.1.x

Each project will receive a major version bump to indicate support
for only 3.6+:

* Flask 2.0
* Werkzeug 2.0
* Click 8.0
* Jinja 3.0
* ItsDangerous 2.0
* MarkupSafe 2.0

Thanks to the `python_requires` package metadata, Python 2.7 and
3.5 users with a modern pip version will install the last supported
version automatically even if later versions are available.

The team will no longer backport patches for unsupported versions, but
the branches will continue to exist. The team will be happy to
accept patches contributed by the community for any severe security and
usability issues until mid-2020.

We made this decision based on multiple factors. Foremost is ease of
community contribution and maintainer availability. As time goes on,
fewer contributors have used or are familiar with the differences
between Python 2 and 3. Contributors and maintainers must keep track of
an ever growing list of obscure compatibility issues and workarounds,
and cannot use many modern features.

Over the last two years, we've talked to many developers and teams at
conferences and meetups and heard overwhelming support for the move to
Python 3. This is backed up by data collected from our community in a
survey we ran during January 2019, with 92% of respondents already using
or actively upgrading to Python 3. The [PSF developer survey][psf] and
PyPI statistics report similar majorities and show adoption continuing
to increase.

Thank you to everyone in the community for your support, and to everyone
who has made this transition a reality. We look forward to continuing
to develop the Pallets projects with you!

[pep]: https://www.python.org/dev/peps/pep-0373/

[community]: https://python3statement.org/

[pytest]: https://docs.pytest.org/en/5.3.2/py27-py34-deprecation.html

[devguide]: https://devguide.python.org/#status-of-python-branches

[psf]: https://www.jetbrains.com/research/python-developers-survey-2018/#python-3-adoption
