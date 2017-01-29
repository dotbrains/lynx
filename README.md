Lynx (WIP)
======

Lynx is a script to set up an Linux laptop for web development.

It can be run multiple times on the same machine safely.
It installs, upgrades, or skips packages
based on what is already installed on the machine.

![Build Status](https://travis-ci.org/NicholasAdamou/Lynx.svg?branch=master)
![license](https://img.shields.io/apm/l/vim-mode.svg)

Install
-------

Download, review, then execute the script:

```sh
curl --remote-name https://raw.githubusercontent.com/nicholasadamou/lynx/master/lynx
less lynx
sh lynx 2>&1 | tee ~/lynx.log
```

Optionally, [install nicholasadamou/dotfiles][dotfiles].

[dotfiles]: https://github.com/nicholasadamou/dotfiles

Debugging
---------

Your last lynx run will be saved to `~/lynx.log`.
Read through it to see if you can debug the issue yourself.
If not, copy the lines where the script failed into a
[new GitHub Issue](https://github.com/nicholasadamou/lynx/issues/new) for me.
Or, attach the whole log file as an attachment.

What it sets up
---------------

Linux tools:

* [Linuxbrew] for managing operating system libraries.

[Linuxbrew]: http://linuxbrew.sh/

Unix tools:

* [Exuberant Ctags] for indexing files for vim tab completion
* [Git] for version control
* [OpenSSL] for Transport Layer Security (TLS)
* [RCM] for managing company and personal dotfiles
* [The Silver Searcher] for finding things in files
* [Tmux] for saving project state and switching between projects
* [Zsh] as your shell

[Exuberant Ctags]: http://ctags.sourceforge.net/
[Git]: https://git-scm.com/
[OpenSSL]: https://www.openssl.org/
[RCM]: https://github.com/thoughtbot/rcm
[The Silver Searcher]: https://github.com/ggreer/the_silver_searcher
[Tmux]: http://tmux.github.io/
[Zsh]: http://www.zsh.org/

Heroku tools:

* [Heroku Toolbelt] and [Parity] for interacting with the Heroku API

[Heroku Toolbelt]: https://toolbelt.heroku.com/
[Parity]: https://github.com/thoughtbot/parity

GitHub tools:

* [Hub] for interacting with the GitHub API

[Hub]: http://hub.github.com/

Image tools:

* [ImageMagick] for cropping and resizing images

Testing tools:

* [Qt] for headless JavaScript testing via Capybara Webkit

[Qt]: http://qt-project.org/

Programming languages and configuration:

* [Bundler] for managing Ruby libraries
* [Node.js] and [NPM], for running apps and installing JavaScript packages
* [Rbenv] for managing versions of Ruby
* [Ruby Build] for installing Rubies
* [Ruby] stable for writing general-purpose code

[Bundler]: http://bundler.io/
[ImageMagick]: http://www.imagemagick.org/
[Node.js]: http://nodejs.org/
[NPM]: https://www.npmjs.org/
[Rbenv]: https://github.com/sstephenson/rbenv
[Ruby Build]: https://github.com/sstephenson/ruby-build
[Ruby]: https://www.ruby-lang.org/en/

Databases:

* [Postgres] for storing relational data
* [Redis] for storing key-value data

[Postgres]: http://www.postgresql.org/
[Redis]: http://redis.io/

It should take less than 15 minutes to install (depends on your machine).

Inspiration
-------
[Thoughtbot](https://github.com/thoughtbot)

License
-------

Lynx is © 2017 Nicholas Adamou.
It is free software,
and may be redistributed under the terms specified in the [LICENSE] file.

[LICENSE]: LICENSE
