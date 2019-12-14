# Squashing Commits Together

## Without Using Rebase

```bash
git reset HEAD~n
# for example squash the last three commits
git reset HEAD~3
git commit -am "Merged three commits together"
```

## Using Rebase

```bash
git rebase -i master
```

- this will open an interactive menu to select which commits you wish to `pick` and/or `squash`
- by selecting `pick`, you are committing that update
- by selecting `squash`, the commit is merged into the current commit

- for example:

```bash
pick 1eabc17a8 Add data-attributes for styling checkout
squash 90c58b487 Fix react-dom warning; non-critical, but annoying
```
