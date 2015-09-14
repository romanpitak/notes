# PHP

## Tools

### `composer`

```bash
curl 'https://getcomposer.org/composer.phar' --output "${HOME}/bin/composer"
chmod u+x "${HOME}/bin/composer"
```

### `phpunit`

```bash
curl 'https://phar.phpunit.de/phpunit.phar' --output "${HOME}/bin/phpunit"
chmod u+x "${HOME}/bin/phpunit"
```

### `phpenv`

There is a [phpenv/phpenv](https://github.com/phpenv/phpenv) version,
but it looks unmaintained at the time of writing (2015-09-14)
so I'm using [CHH/phpenv](https://github.com/CHH/phpenv).
Also - Travis CI uses the CCH version.

The `PHPENV_ROOT` (temporary (for now)) variable
specifies the installation destination.

```bash
cd ~/var/src  # or any other temporary location
git clone https://github.com/CHH/phpenv.git
cd phpenv
PHPENV_ROOT="${HOME}/.phpenv" ./bin/phpenv-install.sh
# cleanup
cd ..
rm -rf phpenv
```

This will install the `phpenv` and `rbenv` commands into `${HOME}/.phpenv/bin`.

Init from `~/.bashrc`:

```bash
export PHPENV_ROOT="${HOME}/.phpenv"
bashrc::prefix_path "${PHPENV_ROOT}/bin"
eval "$(phpenv init -)"
```

Notes:
1. Setting `PHPENV_ROOT` is *probably* optional.
2. **For rbenv users:** Make sure that `~/.rbenv/bin` takes precedence
in the `PATH` over `~/.phpenv/bin`
by placing it before, so `rbenv` gets used from `~/.rbenv`.

#### `phpenv install` support

In this case [CHH/php-build](https://github.com/CHH/php-build) redirects to [php-build/php-build](https://github.com/php-build/php-build)
(CHH is a member of the [php-build](https://github.com/php-build) group).

```bash
git clone git://github.com/php-build/php-build.git "${PHPENV_ROOT}/plugins/php-build"
```
