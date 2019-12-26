# Git Tips

## Checkout a File From Another Branch / Commit

```bash
# checkout from another branch
git checkout another-branch -- README.md
# checkout from another commit (using the hash)
git checkout 963396a -- README.md
```

## View A Simple Log

`git log --oneline --no-merges`

## Update Last Commit Message

`git commit -v --amend`

## Remove Last Commit

`git reset --hard HEAD^`

## Remove Last 2 Commits

`git reset --hard HEAD~2`

- replace `2` with how many commits back should be removed

## Remove Untracked Changes

`git clean -f -d`

## Show a Changelog

`git shortlog <commit-hash>..HEAD`

## Show Updates Since a Specific Date/Time

`git log --since='FEB 10 2016' --until='FEB 19 2016'`

## Search for Updates Containing a Keyword

`git log -S "keyword term or phrase"`

- [source1](https://dev.to/jacobherrington/10-git-tricks-to-save-your-time-and-sanity-289h)
- [source2](https://gist.github.com/CrookedNumber/8964442)
