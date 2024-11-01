~~~~toml
title = "Introducing the Pallets Community Organization (Pallets-Eco)"
author_name = "Kara Babcock"
published = 2022-04-03
tags = ["meta"]
~~~~

Flask and many of the other Pallets projects benefit from having a diverse
ecosystem of user-maintained extensions. However, we recognize that not every
extension creator can maintain an extension indefinitely. Last year, the
Pallets team started
the [Pallets Community Organization](https://github.com/pallets-eco/),
aka Pallets-Eco, on GitHub to provide a
place where the community can work together to maintain the extensions that we
all rely on.

The popular [Flask-Caching](https://flask-caching.readthedocs.io/) and
[Flask-OpenID](http://packages.python.org/Flask-OpenID/) extensions have
already been moved to Pallets-Eco.

In time, we hope that this organization will ensure the stability of the Pallets
ecosystem and provide a great point of entry for new contributors.

## What Belongs in Pallets-Eco?

Although we expect that most extensions we take in will be for Flask, the
organization is open to extensions for *any* of the Pallets projects—Click,
Jinja, Werkzeug, etc.

It's important to note, however, that this is *not* an official extension
repository. Extensions in this organization are not guaranteed to be up to date
or maintained by the Pallets team. Rather, this is a centralized place for
members of the wider community to help maintain these extensions.

The Pallets Community Organization is not currently accepting non-extension
projects, such as documentation translations. If you are interested in such
projects, [join the Pallets Discord](https://discord.gg/pallets) and ask about
the Flask Community Working Group.

## How You Can Transfer Your Extension

First, [reach out on Discord](https://discord.gg/pallets) (in the `#pallets-eco`
channel) to express your interest. Only the current owner of a repository can
transfer it, so please don't inquire on behalf of extensions you don't own. If
there is an abandoned extension that you want to start maintaining, *fork* it,
work on it, and then ask about joining Pallets-Eco.

Second, [review the GitHub docs on transferring a repo](https://docs.github.com/en/repositories/creating-and-managing-repositories/transferring-a-repository).
We will work with you to transfer the repo into the Pallets-Eco organization.

Third, you will need to give some of our organization members access to make
releases on PyPI.

Keep in mind that transferring your extension to the Pallets Community
Organization means you're giving up the final say on how your extension
evolves. You will remain as a collaborator on your extension and can continue
to contribute, but other members will have input on pull requests and when
releases are made. If you prefer to keep your extension completely under your
control, then Pallets-Eco is not for you.

## Help With Maintenance

Whether you're interested in maintaining one extension in particular or just
contributing to the organization overall, we welcome new contributors! This is
a great starting point if you've always wanted to contribute to a Pallets
project but haven't seen an issue you are ready to tackle—most of the issues in
an extension will be smaller in scope and easier to resolve.

All extensions in the Pallets Community Organization follow the same
[contributing guidelines](https://github.com/pallets/flask/blob/main/CONTRIBUTING.rst)
as the core
Pallets projects. Different extensions will come to the organization with
different testing coverage and documentation completion. To that end, even if
an extension doesn't have open issues, it's likely you could improve its tests
and/or docs. After you have reviewed the contributing guidelines, fork the
repo, make changes, and open a pull request when you are ready.

Release permissions will be limited to trusted members of the organization
(you could become one in time). If you have questions that don't belong in a
specific extension's issues, ask in `#pallets-eco` on the Pallets Discord.
