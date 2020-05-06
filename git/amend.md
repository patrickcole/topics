# Git Amend

- provides the ability to amend a previous commit with new changes and an updated message

```bash
git add README.md
git commit --amend
```

- also hast the ability to add forgotten files to a commit without having to post a new commit message:

```bash
# assume this is after a commit
# and forgotten file has been staged
# via git add <<file>>
git commit --amend --no-edit
```
