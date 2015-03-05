
# gpg cheatsheet

- `gpg --gen-key` generate key
- `gpg --export -a "User Name" > public.key` export public.key
- `gpg --export-secret-key -a "User Name" > private.key` export private.key
- `gpg --import public.key` adds the public key  to your public key ring
- `gpg --allow-secret-key-import --import private.key` adds the private key to your private key ring
- `gpg --delete-key "User Name"` delete public key
- `gpg --delete-secret-key "User Name"` delete private key
- `gpg --list-keys`
- `gpg --list-secret-keys`
- `gpg --fingerprint`
- `gpg -e -u "Sender User Name" -r "Receiver User Name" somefile`
- `gpg -d somefile.gpg`
