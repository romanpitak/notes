# GIT

[git man page generator](http://git-man-page-generator.lokaltog.net/)

- Do
    - **Add only part of a file** - `git add <file> --patch`
        - `y` stage this hunk for the next commit
        - `n` do not stage this hunk the next commit
        - `s` split the current hunk into smaller hunks
        - `?` print help
- Undo
    - **`git add <file>`** - `git reset <file>`
    - **Last `commit`** - `git reset --soft HEAD~1`
        - Pro tip: `git commit -c ORIG_HEAD` will open an editor with he log message from the old commit.
    - **Last `merge`** - `git reset --hard HEAD~1`
    - **Last `merge --sqash`**
        - *before `commit`* - `git merge --abort`
        - *after `commit`* - `git reset --hard HEAD~1`
    **On remote** - Don't. Just don't. It can't be that bad.

## Sources

- SO
    - [Commit only part of a file](http://stackoverflow.com/questions/1085162/commit-only-part-of-a-file-in-git)
    - [Undo 'git add' before commit](http://stackoverflow.com/questions/348170/undo-git-add-before-commit)
    - [How do you undo the last commit?](http://stackoverflow.com/questions/927358/how-do-you-undo-the-last-commit)
    - [Undo a Git merge?](http://stackoverflow.com/questions/2389361/undo-a-git-merge)

[`git add` interactive_mode](http://git-scm.com/docs/git-add#_interactive_mode)

[How to undo (almost) anything with Git](https://github.com/blog/2019-how-to-undo-almost-anything-with-git)
