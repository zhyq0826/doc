## Install postgresql

```

brew install homebrew/versions/postgresql93

```

install info

```

brew install homebrew/versions/postgresql93                                                                                                                      !180
==> Tapping homebrew/versions
Cloning into '/usr/local/Library/Taps/homebrew/homebrew-versions'...
remote: Counting objects: 254, done.
remote: Compressing objects: 100% (240/240), done.
remote: Total 254 (delta 28), reused 96 (delta 14), pack-reused 0
Receiving objects: 100% (254/254), 266.74 KiB | 380.00 KiB/s, done.
Resolving deltas: 100% (28/28), done.
Checking connectivity... done.
Tapped 251 formulae (275 files, 1.6M)
==> Installing postgresql93 from homebrew/homebrew-versions
==> Installing dependencies for homebrew/versions/postgresql93: openssl, readline, ossp-uuid
==> Installing homebrew/versions/postgresql93 dependency: openssl
==> Downloading https://homebrew.bintray.com/bottles/openssl-1.0.2d_1.el_capitan.bottle.tar.gz
######################################################################## 100.0%
==> Pouring openssl-1.0.2d_1.el_capitan.bottle.tar.gz
==> Caveats
A CA file has been bootstrapped using certificates from the system
keychain. To add additional certificates, place .pem files in
 /usr/local/etc/openssl/certs

and run
 /usr/local/opt/openssl/bin/c_rehash

This formula is keg-only, which means it was not symlinked into /usr/local.

Apple has deprecated use of OpenSSL in favor of its own TLS and crypto libraries

Generally there are no consequences of this for you. If you build your
own software and it requires this formula, you'll need to add to your
build variables:

   LDFLAGS:  -L/usr/local/opt/openssl/lib
   CPPFLAGS: -I/usr/local/opt/openssl/include

==> Summary
🍺  /usr/local/Cellar/openssl/1.0.2d_1: 464 files, 17M
==> Installing homebrew/versions/postgresql93 dependency: readline
==> Downloading https://homebrew.bintray.com/bottles/readline-6.3.8.el_capitan.bottle.tar.gz
######################################################################## 100.0%
==> Pouring readline-6.3.8.el_capitan.bottle.tar.gz
==> Caveats
This formula is keg-only, which means it was not symlinked into /usr/local.

OS X provides the BSD libedit library, which shadows libreadline.
In order to prevent conflicts when programs look for libreadline we are
defaulting this GNU Readline installation to keg-only.


Generally there are no consequences of this for you. If you build your
own software and it requires this formula, you'll need to add to your
build variables:

   LDFLAGS:  -L/usr/local/opt/readline/lib
   CPPFLAGS: -I/usr/local/opt/readline/include

==> Summary
🍺  /usr/local/Cellar/readline/6.3.8: 40 files, 2.1M
==> Installing homebrew/versions/postgresql93 dependency: ossp-uuid
==> Downloading https://homebrew.bintray.com/bottles/ossp-uuid-1.6.2_1.el_capitan.bottle.tar.gz
######################################################################## 100.0%
==> Pouring ossp-uuid-1.6.2_1.el_capitan.bottle.tar.gz
🍺  /usr/local/Cellar/ossp-uuid/1.6.2_1: 16 files, 252K
==> Installing homebrew/versions/postgresql93
==> Downloading http://ftp.postgresql.org/pub/source/v9.3.9/postgresql-9.3.9.tar.bz2
######################################################################## 100.0%
==> Patching
patching file contrib/uuid-ossp/uuid-ossp.c
==> ./configure --prefix=/usr/local/Cellar/postgresql93/9.3.9 --datadir=/usr/local/Cellar/postgresql93/9.3.9/share/postgresql93 --docdir=/usr/local/Cellar/postgresql93/9.
==> make install-world
==> Caveats
initdb /usr/local/var/postgres -E utf8    # create a database
postgres -D /usr/local/var/postgres       # serve that database
PGDATA=/usr/local/var/postgres postgres   # ...alternatively

If builds of PostgreSQL 9 are failing and you have version 8.x installed,
you may need to remove the previous version first. See:
 https://github.com/Homebrew/homebrew/issues/issue/2510

To migrate existing data from a previous major version (pre-9.3) of PostgreSQL, see:
 http://www.postgresql.org/docs/9.3/static/upgrading.html

When installing the postgres gem, including ARCHFLAGS is recommended:
 ARCHFLAGS="-arch x86_64" gem install pg

To install gems without sudo, see the Homebrew documentation:
https://github.com/Homebrew/homebrew/blob/master/share/doc/homebrew/Gems,-Eggs-and-Perl-Modules.md

To have launchd start homebrew/versions/postgresql93 at login:
 ln -sfv /usr/local/opt/postgresql93/*.plist ~/Library/LaunchAgents
Then to load homebrew/versions/postgresql93 now:
 launchctl load ~/Library/LaunchAgents/homebrew.mxcl.postgresql93.plist
Or, if you don't want/need launchctl, you can just run:
 postgres -D /usr/local/var/postgres
==> Summary
🍺  /usr/local/Cellar/postgresql93/9.3.9: 2950 files, 38M, built in 112 seconds


```


## install redis

```

± % brew install redis                                                     !100
==> Downloading https://homebrew.bintray.com/bottles/redis-3.0.5.el_capitan.bott
######################################################################## 100.0%
==> Pouring redis-3.0.5.el_capitan.bottle.tar.gz
==> Caveats
To have launchd start redis at login:
  ln -sfv /usr/local/opt/redis/*.plist ~/Library/LaunchAgents
Then to load redis now:
  launchctl load ~/Library/LaunchAgents/homebrew.mxcl.redis.plist
Or, if you don't want/need launchctl, you can just run:
  redis-server /usr/local/etc/redis.conf
==> Summary
🍺  /usr/local/Cellar/redis/3.0.5: 9 files, 892K

```

## install oh my zsh

```
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

```


vi .zshrc

theme = blinks, ys

```
ZSH_THEME="blinks"

```
