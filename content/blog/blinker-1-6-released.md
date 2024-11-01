~~~~toml
title = "Blinker 1.6 Released"
author_name = "P G Jones"
published = 2023-04-02
tags = ["releases"]
~~~~

Signalling allows for applications to be decoupled by allowing designated
receivers to be informed when an action has taken place (the signal). Flask and
Quart both utilise the excellent [Blinker](https://github.com/pallets-eco/blinker)
library to support signals, and it is version 1.6 of this library that has been
released.

This is the second major release of Blinker since maintenance transferred to the
[Pallets-eco](pallets-community-org.md) organisation, and represents a desire to
maintain it for the benefit of Flask, Quart, and indeed Blinker users.

The [Changelog](https://blinker.readthedocs.io/page/changes/) for 1.6 is
headlined by a mondernisation of the project structure which should ensure
easier maintenance into the years to come. In addition, we've added:

- an ability to temporarily mute signals,
- support for int senders,
- support for async (coroutine) receivers,
- and we've type hinted the project.
