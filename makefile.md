# Makefile

### Special Macros

- `$@` name of the target
- `$?` list of dependents more recent than the target
- `$^` all dependencies (without duplicates)
- `$+` all dependencies with duplicates in original order
- `$<` first dependency only
