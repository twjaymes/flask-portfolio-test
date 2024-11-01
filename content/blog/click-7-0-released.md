~~~~toml
title = "Click 7.0 Released"
author_name = "David Lord"
published = 2018-09-25
tags = ["releases"]
~~~~

The Pallets team is pleased to release Click 7.0. Thank you to everyone who contributed
online and in person at the PyCon US 2018 sprint! With the help of the community as well
as some new maintainers, we've managed to resolve hundreds of long standing issues and
pull requests.

Due to the length of time since the last release, there are a significant number of new
features and
fixes. [Check out the changelog](https://click.palletsprojects.com/page/changes/#version-7-0)
for a list of all code changes and links to the relevant issues. Changes include:

* Shell autocompletion has improved in a number of areas.
    * Native ZSH completion was added, and supports its enhanced parameter
      documentation.
    * The choice type can be completed.
    * Completion correctly handles chained commands, spaces, defaults, and partial
      completions.
    * Parameters can provide a callback to customize completion.
* On Windows `click.echo` can now output more than 16k characters in one call. On
  Windows 7, a 64k limit on binary stream output is also worked around.
* `click.getchar` returns Unicode on Windows.
* When piping input and output, more cases of closed pipes are detected and handled
  instead of raising errors.
* The `CliRunner` used for testing separates stdout and stderr.
* New `DateTime` and `FloatRange` parameter types.
* Flags to mark a parameter as hidden or deprecated.
* Numerous improvements and fixes to i/o, help, parameters, and testing.

## Read the Docs

Click is the first Pallets project to move its docs to Read the Docs. Our projects
currently use a custom builder and hosting, but this became too difficult with limited
maintainer time. Thank you to everyone at RTD who helped with the transition!

The new URL for the docs is https://click.palletsprojects.com/. The
old `https://click.palletsprojects.com/` domain will redirect to the new one while we
continue to migrate, but will eventually go away. Please use the new URL going forward.

Click's docs use a custom Sphinx theme and extensions. As part of the move, these were
extracted to a separate Python package.
Install [Pallets-Sphinx-Themes](https://pypi.org/project/Pallets-Sphinx-Themes) to use
Click's theme when writing extensions for a more cohesive look.

## Install or Upgrade

Install from [PyPI](https://pypi.org/project/Click) with pip:

    pip install -U Click

## Get Involved

Click and the Pallets team depends on you, the community. Whether you report issues,
write documentation, create patches, or answer questions, we appreciate all the help you
provide. [Star the project on GitHub](https://github.com/pallets/click) to show support,
and [watch](https://help.github.com/articles/watching-and-unwatching-repositories/) the
repository to see discussions and pull requests as they happen.

## Donate

We now accept donations through the Python Software Foundation in order to support our
efforts to maintain the projects and grow the community. [**Click here to donate.
**](../donate.md)
