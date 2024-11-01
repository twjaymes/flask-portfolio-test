~~~~toml
title = "Werkzeug 0.11.6 Security Release"
author_name = "Armin Ronacher"
published = 2016-04-14
tags = ["releases", "security"]
~~~~

Today we pushed out a [Werkzeug](https://werkzeug.palletsprojects.com) bugfix release
which contains a security relevant fix. It has come to our attention (reported
by [Jordan Milne](https://github.com/JordanMilne/)) that the PIN brute-force protection
in the Werkzeug debugger could be bypassed
by attacking the cookie rather than the PIN. While this is generally not easily
fixable we improved the situation by mixing in higher quality secret data into the
cookie name and made it more complex. We now include a UUID of the machine
the code is running on.

This should make it significantly more complex to bypass the PIN check. That said
we want to reiterate that the PIN protection for the debugger is *not a suitable
protection to run the debugger in production*. It's a basic security feature to make
it less likely to use an accidentally enabled debugger. Please ensure that you never
enable the debugger in production environments regardless of this feature.
