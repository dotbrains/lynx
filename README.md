Lynx [![Build Status](https://travis-ci.org/nicholasadamou/Lynx.svg?branch=master)](https://travis-ci.org/nicholasadamou/Lynx)
======

Lynx is a script to set up a Linux laptop for web development.

It can be run multiple times on the same machine safely.
It installs, upgrades, or skips packages
based on what is already installed on the machine.

[Requirements](https://github.com/nicholasadamou/Lynx/blob/master/README.md#requirements) / [Install](https://github.com/nicholasadamou/Lynx/blob/master/README.md#install) / [Debugging](https://github.com/nicholasadamou/Lynx/blob/master/README.md#debugging) / [What it sets up](https://github.com/nicholasadamou/Lynx/blob/master/README.md#what-it-sets-up) / [Customize in ~/.lynx.local](https://github.com/nicholasadamou/Lynx/blob/master/README.md#customize-in-lynxlocal) / [Inspiration](https://github.com/nicholasadamou/Lynx/blob/master/README.md#inspiration) / [License](https://github.com/nicholasadamou/Lynx/blob/master/README.md#license)

Requirements
------------

Lynx supports:

* Ubuntu 17.04

Older versions may work but aren't regularly tested. Bug reports for older
versions are welcome.

Install
-------

Download the script:

```
bash
curl --remote-name https://raw.githubusercontent.com/nicholasadamou/Lynx/master/lynx
```

Review the script (avoid running scripts you haven't read!):

```bash
less lynx
```

Execute the downloaded script:

```bash
bash lynx 2>&1 | tee ~/lynx.log
```

Optionally, review the log:

```bash
less ~/lynx.log
```


Optionally, [install nicholasadamou/dotfiles][dotfiles].

[dotfiles]: https://github.com/nicholasadamou/dotfiles#Setup

Debugging
---------

Your last Lynx run will be saved to `~/lynx.log`.
Read through it to see if you can debug the issue yourself.
If not, copy the lines where the script failed into a
[new GitHub Issue](https://github.com/nicholasadamou/Lynx/issues/new) for me.
Or, attach the whole log file as an attachment.

What it sets up
---------------

Linux tools:

* [Linuxbrew] for managing operating system libraries.

[Linuxbrew]: http://linuxbrew.bash/

Unix tools:

* [Exuberant Ctags] for indexing files for vim tab completion
* [Git] for version control
* [OpenSSL] for Transport Layer Security (TLS)
* [RCM] for managing company and personal dotfiles
* [The Silver Searcher] for finding things in files
* [Tmux] for saving project state and switching between projects
* [Watchman] for watching for filesystem events
* [zsh] as your shell

[Exuberant Ctags]: http://ctags.sourceforge.net/
[Git]: https://git-scm.com/
[OpenSSL]: https://www.openssl.org/
[RCM]: https://github.com/thoughtbot/rcm
[The Silver Searcher]: https://github.com/ggreer/the_silver_searcher
[Tmux]: http://tmux.github.io/
[Watchman]: https://facebook.github.io/watchman/
[zsh]: http://www.zsh.org/

Heroku tools:

* [Heroku CLI] and [Parity] for interacting with the Heroku API

[Heroku CLI]: https://devcenter.heroku.com/articles/heroku-cli
[Parity]: https://github.com/thoughtbot/parity

GitHub tools:

* [Hub] for interacting with the GitHub API

[Hub]: http://hub.github.com/

Image tools:

* [ImageMagick] for cropping and resizing images

Testing tools:

* [Qt 5] for headless JavaScript testing via [Capybara Webkit]

[Qt 5]: http://qt-project.org/
[Capybara Webkit]: https://github.com/thoughtbot/capybara-webkit

Programming languages, package managers, and configuration:

* [ASDF] for managing programming language versions
* [Bundler] for managing Ruby libraries
* [Node.js] and [NPM], for running apps and installing JavaScript packages
* [Ruby] stable for writing general-purpose code
* [Yarn] for managing JavaScript packages

[Bundler]: http://bundler.io/
[ImageMagick]: http://www.imagemagick.org/
[Node.js]: http://nodejs.org/
[NPM]: https://www.npmjs.org/
[ASDF]: https://github.com/asdf-vm/asdf
[Ruby]: https://www.ruby-lang.org/en/
[Yarn]: https://yarnpkg.com/en/

Databases:

* [Postgres] for storing relational data
* [Redis] for storing key-value data

[Postgres]: http://www.postgresql.org/
[Redis]: http://redis.io/

It bashould take less than 15 minutes to install (depends on your machine).

Customize in `~/.lynx.local`
------------------------------

Your `~/.lynx.local` is run at the end of the Lynx script.
Put your customizations there.
For example:

```bash
#!/bin/bash

brew bundle --file=- <<EOF
brew "Caskroom/cask/dockertoolbox"
brew "go"
brew "ngrok"
brew "watch"
EOF

default_docker_machine() {
  docker-machine ls | grep -Fq "default"
}

if ! default_docker_machine; then
  docker-machine create --driver virtualbox default
fi

default_docker_machine_running() {
  default_docker_machine | grep -Fq "Running"
}

if ! default_docker_machine_running; then
  docker-machine start default
fi

echo "Cleaning up old Homebrew formulae ..."
brew cleanup
brew cask cleanup

if [ -r "$HOME/.rcrc" ]; then
  echo "Updating dotfiles ..."
  rcup
fi
```

Write your customizations such that they can be run safely more than once.
See the `lynx` script for examples.

Lynx functions such as `gem_install_or_update`
can be used in your `~/.lynx.local`.

Inspiration
-------
[Thoughtbot](https://github.com/thoughtbot)

License
-------

Lynx is © 2017 Nicholas Adamou.

It is free software, and may be redistributed under the terms specified in the [LICENSE] file.

[LICENSE]: LICENSE
