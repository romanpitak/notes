# nodejs / iojs #

## `nvm` - node version manager ##

Checkout the git repo into `~/.nvm`:

```bash
git clone https://github.com/creationix/nvm.git ~/.nvm
```

Set to latest version

```bash
cd ~/.nvm
git checkout \
    "$(git describe --abbrev=0 --tags)"
```

Install some `node`

```bash
source ~/.nvm/nvm.sh
nvm install 0.10
nvm install 0.11
nvm install 0.12
nvm install iojs
node --version
```

Load `nvm` in `~/.bashrc`

```bash
# NVM
if test -d "${HOME}/.nvm"; then
    if test -f "${HOME}/.nvm/nvm.sh"; then
        . "${HOME}/.nvm/nvm.sh"
    fi
    if test -r "${HOME}/.nvm/bash_completion"; then
        . "${HOME}/.nvm/bash_completion"
    fi
    nvm use iojs
fi
```

## `npm` - node package manager ##

```bash
npm install bower --global
```
