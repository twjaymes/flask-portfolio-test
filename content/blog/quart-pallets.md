~~~~toml
title = "Quart is now a Pallets project"
author_name = "P G Jones"
published = 2022-07-06
tags = ["meta"]
~~~~

Quart, an ASGI re-implementation of the Flask API has joined the
Pallets organization. This means that future development will be under
the Pallets governance by the Pallets maintainers.

Our long term aim is to merge Quart and Flask to bring ASGI support
directly to Flask. This aim has significant technical obstacles, as
outlined in this
[post](https://pgjones.dev/blog/flask-async-quart-sync-2019/) or this
[talk](https://youtu.be/bw1qeMoFBmw). However, this change clears
governance obstacles and brings the Quart and Flask maintainers closer
together.

# Introduction to Quart

Quart was developed from a desire to use asyncio and the async/await
keywords in Flask. Which at the time of Quart's inception was not
possible in Flask nor was it possible to add support. Instead Quart
was developed as a reimplementation of Flask's API using async/await
(learn more from this
[talk](https://www.youtube.com/watch?v=EgpQcLy1kf0)). Later Quart
adopted the [ASGI](https://asgi.readthedocs.io) standard and is now a
compliant ASGI framework.

The Quart API is a superset's of Flask in that it matches Flask's
whilst including ASGI specific features such as websockets, for
example:

```python
from quart import Quart, render_template, websocket

app = Quart(__name__)


@app.route("/")
async def hello():
    return await render_template("index.html")


@app.route("/api")
async def json():
    return {"hello": "world"}


@app.websocket("/ws")
async def ws():
    while True:
        await websocket.send("hello")
        await websocket.send_json({"hello": "world"})
```

You can read more about Quart at
[quart.palletsprojects.com](https://quart.palletsprojects.com)
including a guide to
[migrating](https://quart.palletsprojects.com/page/how_to_guides/flask_migration.html)
from Flask to Quart.

## When to use Quart

Quart is an ASGI framework utilising async IO throughout, whereas
Flask is a WSGI framework utilising sync IO. It is therefore best to
use Quart if you intend to use async IO (i.e. async/await libraries)
and Flask if not. Don't worry if you choose the 'wrong' framework
though, as Quart supports sync IO and Flask supports async IO,
although less efficiently.

# What's next

The large ecosystem of Flask extensions is a real strength but
unfortunately these extensions only work with Flask, and vice versa
for Quart extensions. Therefore we plan to enable extensions to
support both Flask and Quart in the future.

We expect to keep developing features for both Flask and Quart, in
fact a number of features now present in Flask were developed in Quart
or from knowledge gained from Quart. This includes typing, async/await
support (in Flask), faster routing, and more.

With the closer relationship now possible both Flask and Quart should
benefit from new features, shared bug fixes, and more. Please join our
[discord](https://discord.gg/pallets) if you'd like to get involved.
