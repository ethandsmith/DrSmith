#### Overview

Dr. Smith (`drsmith.rb`) is a voting bot that will trail the votes of other accounts in order to then mirror their voting pattern. [Based on @inertia's "Dr. Doogie" voting bot,](https://gist.github.com/inertia186/d57c9bc744f05ada01d173521c01df8a) Dr. Smith allows absolute percentage voting instead of a scaled percentage.

For example, Dr. Doogie would normally scale your account's vote to a percentage of the trailed account's vote, i.e. if you were trailing curie and it voted at 20% and your 'voting_weight' parameter was set at 5%, your account would vote at 1%.

Dr. Smith, however, would vote on each post that curie voted on with the absolute value of 'voting_weight'

* Title: drsmith.rb - Vote Trail Bot
* Tags: radiator ruby steem steemdev curation
* Notes: the original bot, Dr. Doogie, was created by @inertia186

#### Changes

* `voting_weight` - now represents your account's absolute voting percentage instead of a scaling factor based on the trailed account's voting percentage.


#### Features

* YAML config.
  * `voting_weight` - your account's voting percentage
  * `max_age` - only vote if the post is under this number in minutes
  * `allow_upvote` - trail upvotes
  * `allow_downvote` - trail downvotes
  * `enable_comments` - vote for comments
  * `skip_tags` - do not vote if the post contains any of these tags
  * `only_tags` - only vote if the post includes at least one of these tags

  * `global`
    * `mode`
      * `head` - the last block
      * `irreversible` - (default) the block that is confirmed by 2/3 of all block producers and is thus irreversible!

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

Inertia has tested it on various versions of ruby.  The oldest one he got it to work was:

`ruby 2.0.0p645 (2015-04-13 revision 50299) [x86_64-darwin14.4.0]`

First, clone this gist and install the dependencies:

```bash
$ git clone https://gist.github.com/45af1abb7eb11f87574f6c51e3a2d3a4.git drsmith
$ cd drsmith
$ bundle install
```
Open the file drsmith.yml in terminal or in your favorite text editor (I recommend [Atom](http://atom.io)).

Change "social" to the voting account username.

Add your Private active key or Private posting key in place of the included key.

Change "banjo" to the account you want to trail.

Edit `voting_weight` to your desired voting percentage

Change other settings as necessary

Return to Terminal and run it:

```bash
$ ruby drsmith.rb
```


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
drsmith.yml:1: syntax error, unexpected ':', expecting end-of-input
```

##### Solution: You ran `ruby drsmith.yml` but you should run `ruby drsmith.rb`.

---

##### Problem: Everything looks ok, but every time drsmith tries to post, I get this error:

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

See Inertia's previous Ruby How To posts in: [#radiator](https://steemit.com/created/radiator) [#ruby](https://steemit.com/created/ruby)

## Get in touch!

If you're using drsmith, I'd love to hear from you.  Drop me a line and tell me what you think!  I'm @ethandsmith on Steemit and [Discord](http://discordapp.com).

## License

Dr. Smith is licensed under a Creative Commons [![CC0](http://i.creativecommons.org/p/zero/1.0/80x15.png)](http://creativecommons.org/publicdomain/zero/1.0/) License.
