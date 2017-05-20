* Title: drdoogie.rb - Vote Trail Bot
* Tags: radiator ruby steem steemdev curation
* Notes: 

#### Features

* YAML config.
  * `scale_votes` - scale votes in %
  * `max_age` - only vote if the post is under this number in minutes
  * `allow_upvote` - trail upvotes
  * `allow_downvote` - trail downvotes
  * `enable_comments` - vote for comments
  * `skip_tags` - do not vote if the post contains any of these tags
  * `only_tags` - only vote if the post includes at least one of these tags

#### Overview

Dr. Doogie (`drdoogie.rb`) is a voting bot that will trail the votes of other accounts in order to then mirror their voting pattern.

---

#### Install

To use this [Radiator](https://steemit.com/steem/@inertia/radiator-steem-ruby-api-client) script:

##### Linux

```bash
$ sudo apt-get install ruby-full git openssl libssl1.0.0 libssl-dev
$ gem install bundler
```

##### macOS

```bash
$ gem install bundler
```

I've tested it on various versions of ruby.  The oldest one I got it to work was:

`ruby 2.0.0p645 (2015-04-13 revision 50299) [x86_64-darwin14.4.0]`

First, clone this gist and install the dependencies:

```bash
$ git clone https://gist.github.com/d57c9bc744f05ada01d173521c01df8a.git drdoogie
$ cd drdoogie
$ bundle install
```

Then run it:

```bash
$ ruby drdoogie.rb
```

Check here to see an updated version of this script:

https://gist.github.com/inertia186/d57c9bc744f05ada01d173521c01df8a

---

#### Upgrade

Typically, you can upgrade to the latest version by this command, from the original directory you cloned into:

```bash
$ git pull
```

Usually, this works fine as long as you haven't modified anything.  If you get an error, try this:

```
$ git stash --all
$ git pull --rebase
$ git stash pop
```

If you're still having problems, I suggest starting a new clone.

---

#### Troubleshooting

##### Problem: What does this error mean?

```
drdoogie.yml:1: syntax error, unexpected ':', expecting end-of-input
```

##### Solution: You ran `ruby drdoogie.yml` but you should run `ruby drdoogie.rb`.

---

##### Problem: Everything looks ok, but every time drdoogie tries to post, I get this error:

```
`from_base58': Invalid version (RuntimeError)
```

##### Solution: You're trying to vote with an invalid key.

Make sure the `.yml` file `voters` item have the correct account name and WIF posting key.

##### Problem: The node I'm using is down.

Is there a list of nodes?

##### Solution: Yes, special thanks to @ripplerm.

https://ripplerm.github.io/steem-servers/

---

<center>
  <img src="http://i.imgur.com/NPRdGlr.jpg" />
</center>

See my previous Ruby How To posts in: [#radiator](https://steemit.com/created/radiator) [#ruby](https://steemit.com/created/ruby)

## Get in touch!

If you're using drdoogie, I'd love to hear from you.  Drop me a line and tell me what you think!  I'm @inertia on STEEM and [SteemSpeak](http://discord.steemspeak.com).
  
## License

I don't believe in intellectual "property".  If you do, consider drdoogie as licensed under a Creative Commons [![CC0](http://i.creativecommons.org/p/zero/1.0/80x15.png)](http://creativecommons.org/publicdomain/zero/1.0/) License.
