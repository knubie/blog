# Running your own Slack clone with IRC.<br><small>-270782.041</small></h1>

- `#slack`
- `#irc`
- `#shout-irc`
- `#hector`
- `#fluid`
- `#ruby`
- `#javascript`

---

[Slack](https://slack.com/) is pretty cool, but it's basically just IRC with a slick interface and some other nice features built-in. It's always been possible to get most of these features with IRC, but it's usually convoluted to set up and technically involved. For example, users looking for a persistent connection would traditionally run a command line IRC client on some remote server and ssh in to use it, or set up a BNC service which we won't even get into here.

### The server.

Setting up the back-end is pretty straight forward, we just need an IRC server. [Hector](https://github.com/sstephenson/hector) works pretty well for that and is easy to set up. If you're looking for something fully featured, there are dozens of different IRC servers that implement the full RFC and then some. I also have my own [fork of hector](https://github.com/knubie/hector) that adds some features like ops, and channel modes.

### The client.

Thanks to [Shout](http://shout-irc.com/) we can get two of Slack's best features for free, a persistent connection, and a slick interface.

Shout is a browser-based IRC client that installs on a remote server. Once you create a user and log in you've got yourself a persistent connection that'll stay connected to the IRC server even after you've closed the window.

Once you've got Shout set up and running on your server, you can turn the browser client into a desktop app with [Fluid](http://fluidapp.com/).

### Deficiencies.

There are still a few key features missing from this combo; online status, file uploads, code snippets, etc. Some of these are actually in development for Shout at the time of this writing, others could also be added without too much dificulty as well. I'll get more into the deficiencies and ways around them in part two of this post.
