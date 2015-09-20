# `meteor` #

Unfortunatelly `meteor` needs to install sources into `~/.meteor`.
It provides a good install script,
but it installs itself into PATH in `/usr/local`.
We need to change the `PREFIX` variable to install into `~/bin`.

```bash
curl 'https://install.meteor.com/' | \
    sed -e 's/^PREFIX=.*/PREFIX="${HOME}"/' | \
    bash
```

**note**: It sould be possible to install it to a custom location
using the METEOR_WAREHOUSE_DIR variable.
Maybe it's worth a try.
No time now.
