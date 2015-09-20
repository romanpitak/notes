# ruby #

## `rvm` - ruby version manager #

``bash
sudo apt-get install \
    libreadline6-dev \
    libyaml-dev \
    sqlite3 \
    libgdbm-dev \
    libncurses5-dev \
    libffi-dev \
    --assume-yes
gpg --keyserver hkp://keys.gnupg.net \
    --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
curl -L https://get.rvm.io | bash -s stable --autolibs=enabled
```

### Further setup [optional]

The `rvm` install script adds `rvm` loading lines into
`~/.profile` and `~/.bash_profile` by default.

```bash
export PATH="$PATH:$HOME/.rvm/bin" # Add RVM to PATH for scripting

[[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm" # Load RVM into a shell session *as a function*
```

Depending on your current init files settings,
you may want to have a look at that.

### Ruby

```bash
rvm list known
rvm install ruby
rvm docs generate-ri # generate documentation
```

### Gems

```bash
gem update --system
gem install compass
```
