~~~~toml
title = "It's Dangerous 1.0.0 Released"
author_name = "David Lord"
published = 2018-10-18
tags = ["releases"]
~~~~

It's Dangerous 1.0.0 has been released. See
the [changelog](https://itsdangerous.palletsprojects.com/page/changes/#version-1-0-0)
for a list of changes since the last release on 2014-03-28.

It's Dangerous provides secure message signing and serialization. Without the secret key
used to sign a message, the content cannot be changed without invalidating the
signature. This allows, for example, Flask to store information in a session cookie that
is transmitted over public networks, and be sure that the data has not been tampered
with when loading a subsequent request.

## Install or Upgrade

Install from [PyPI](https://pypi.org/project/ItsDangerous) with pip:

    pip install -U ItsDangerous

## Imports will change

Previously, It's Dangerous was a single Python module with about 1000 lines of code. The
project has been reorganized as a package with submodules, which will make the code
easier to navigate going forward.

However, this means that *everything* that It's Dangerous imported or defined used to be
importable from `itsdangerous`. With the reorganization, only the public API is
importable from `itsdangerous`. To ease transition, "public" was defined as any name
that was previously documented in the API section. These compatibility imports will be
deprecated and removed in future releases. If you were importing undocumented names,
you'll need to import them from the correct submodule now.

## Read the Docs

It's Dangerous has moved its docs to Read the Docs. The new URL for the docs
is https://itsdangerous.palletsprojects.com/.

The docs were previously hosted on PyPI's docs site (`pythonhosted.org/itsdangerous`),
but this site has been deprecated and it is no longer possible to upload new docs there.
Unfortunately, due to the deprecation, there is no way to add a redirect to the new
docs. As of this release, any URLs pointing to the old site will break.

## Get Involved

The Pallets team depends on you, the community, to help keep our projects sustainable.
Whether you report issues, write documentation, create patches, or answer questions, we
appreciate all the help you
provide. [Star the project on GitHub](https://github.com/pallets/itsdangerous) to show
support,
and [watch](https://help.github.com/articles/watching-and-unwatching-repositories/) the
repository to see discussions and pull requests as they happen.

## Donate

We accept donations through the Python Software Foundation in order to support our
efforts to maintain the projects and grow the community. [**Click here to donate.
**](../donate.md)
