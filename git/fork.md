# Git Fork

- allows developers to make a copy (and contribute updates, if they wish)
- each repository that is forked by a developer, will have a copy in their namespace with the same name as the forked repo

## How to Keep Up with the original repo

- setup a new remote with the original repo link as the git link in the new remote:

```git
git remote add upstream <link>
```

- in this case, the author has decided to call the remote `upstream`, which represents the original repo link
- ensure that you are on the `master` branch locally
- also **important, do not have any uncommitted local changes**
- the following command will remove any uncommitted local changes:

```git
git checkout master
git clean -fd
```

- the command above `git clean -fd` removes any untracked files AND directories
- now, pulling the `upstream master` branch brings in new files

```git
git pull upstream master
```

- then push any new updates to your `master` branch

```git
git push
```

[source](https://dev.to/jacobherrington/a-fool-proof-way-to-keep-your-fork-caught-up-in-git-2e2e)

---
