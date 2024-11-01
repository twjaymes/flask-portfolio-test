~~~~toml
title = "Hello Pallets Users"
author_name = "Armin Ronacher"
published = 2016-04-01
tags = ["meta"]
~~~~

On the first of April 2010, I released a joke microframework called denied
which made fun of the fact that all microframeworks at the time decided to
forgo with dependencies and bundle up everything they need in a single Python
file. What I did was embed all of Jinja2 and Werkzeug in a base64 encoded
zip file within the framework's only Python file. The response to it was
interesting in a few ways because on the one hand quite a few people did not
really understand that it was an April fools joke to begin with and on the
other, there was a discussion where there were no microframeworks that actually
did use dependencies and encouraged it.

One month later there was a new project by the name of "Flask" which actually
gave this concept a real shot. It launched with the tagline "a microframework
for Python based on Werkzeug, Jinja 2 and good intentions" and six years later
it's the most starred Python framework on GitHub.

What's interesting about Flask is that its success just happened. There are
no conferences about it, no society or foundation and still today much of it
heavily depends on me directly. I'm not even sure why it became this
successful but I attribute a lot of it to the fact that it's easy to get
started and the full footprint of the framework is small enough that it becomes
easy enough to understand.

So what's changing now? Today we launch the Pallets Projects. What is it?
Primarily it's a GitHub organization which will be the home of Flask and all
the associated projects. It will be a new home for those libraries and the
first step to give the community more impact on the development of Flask and
all libraries. In addition there will be a new release of Flask very soon
after a thorough check that we do not break anything.

The people behind the Pallets Projects are [me](../people/mitsuhiko.toml),
[Markus Unterwaditzer](../people/untitaker.toml), [David Lord](../people/davidism.toml)
and [Adrian Mönnich](../people/ThiefMaster.toml) with the organization
being open for newcomers to help and drive the projects forward.

We will spend the next few weeks adding as much organizational information on
the project's website to ensure that what often currently only exists in my
head is brought down to text.

I'm amazed how many people use and love Flask and my libraries and I hope that
this organization will be a good step towards making this scale past me. It's
humbling how big all of this became.
