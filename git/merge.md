# Git Merge

- provides the ability to merge one branch into another
- for example a feature branch into a master branch
- you could also merge the master branch into a feature branch, to ensure files are up-to-date
- for each merge command, a new commit is created to describe the merge process
- the example above does bring up a potential issue: all of the updates from master could pollute the history of the feature branch
- to solve this one could use the `git rebase` command

[source](https://dev.to/molly_struve/there-is-no-right-way-git-rebase-vs-merge-2hc5)

---
