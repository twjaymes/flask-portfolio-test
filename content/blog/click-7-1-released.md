~~~~toml
title = "Click 7.1 Released"
author_name = "David Lord"
published = 2020-03-09
tags = ["releases"]
~~~~

The Pallets team is pleased to release Click 7.1.

[Read the full changelog](https://click.palletsprojects.com/page/changes/#version-7-1)
to understand what may affect your code when upgrading.

- Drop support for Python 3.4. This will be the last version to
  support Python 2.7 and 3.5.
- Multiple fixes in low-level Windows compatibility code.
- Colored output in Jupyter notebooks on Linux and Mac.
- Updated Bash and ZSH tab completion support. Add support for Fish.
- Better formatting when option help text contains newlines.

This also fixes a packaging issue from 7.0 where the project name in the
package metadata was changed to "Click" with an upper case "C". This has
been reverted, the name is now correctly reported in all lower case, "click".

## Version 8.0 Coming Soon

As outlined in [Ending Python 2 Support](ending-python2-support.md),
7.1.x will be the last version to support Python 2.7 and 3.5. The next
version will be 8.0 and will support Python 3.6 and newer.

## Install or Upgrade

Install from [PyPI](https://pypi.org/project/click/) with pip:

    pip install -U click

## Donate to Support Pallets

The Pallets organization accepts donations as part of the non-profit
Python Software Foundation (PSF). Donations through the PSF support our
efforts to maintain the projects and grow the community.

[Click here to donate. ❤](../donate.md)
