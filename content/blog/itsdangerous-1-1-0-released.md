~~~~toml
title = "itsdangerous 1.1.0 Released"
author_name = "David Lord"
published = 2018-10-26
tags = ["releases"]
~~~~

itsdangerous 1.1.0 has been released to fix compatibility issues that were
affecting projects while upgrading. Due to these issues, we had to make a quick
decision and pull itsdangerous 1.0.0 from PyPI earlier today to prevent more
projects from being affected. We appologize for the difficulty this caused, and
the changes in this release should address compatibilty going forward.

1.0.0 changed the default digest algorithm from SHA-1 to SHA-512. SHA-1 as used
by itsdangerous was never suceptible to the collision issue published last year,
but the change was made for peace of mind. However, this change invalidated
existing signatures that were in use.

To address this, 1.1.0 reverts the default digest to SHA-1. It also adds a
fallback mechanism to try other algorithms when unsigning. This gives projects a
safe way to upgrade signing parameters in the future, while still supporting
existing signatures during the upgrade period. A default fallback for SHA-512
was added to support projects that were already affected by the 1.0.0 version.
1.1.0 is therefore compatible with both 0.24 and 1.0.0, so upgrading should be
safe in either case.

Additionally, we reverted a change to the project name in setup.py. 1.0.0
changed the capitalization from "itsdangerous" to "ItsDangerous", but this
caused issues with some systems. The name will remain as "itsdangerous".

We appologize again for the issues and thank everyone in the community who
contributed to the discussion.

## Upgrade

Install from [PyPI](https://pypi.org/project/itsdangerous) with pip:

    pip install -U itsdangerous
