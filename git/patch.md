# Git Patch

- using `git add` to stage changes works
- however, a commit can be broken up into hunks and committed separately
- `git add config.ts --patch`
- this would go through each change in the `config.ts` file and ask if you want to commit that change or move on to the next one
- provides explicit option to skip, edit or stage the change
- the following message will be displayed upon a patch:

`Stage this hunk [y,n,q,a,d,j,J,g,/,e,?]?`

- y: yes, stage the hunk
- n: no, do not stage the hunk
- q: quit; do not stage this hunk or the remaining hunks
- a: all; stage this hunk and all remaining hunks
- d: do not stage this hunk or any of the later hunks
- g: go; select a hunk to go to
- /: search for a hunk (via a regex)
- j: leave this hunk undecided, go to next **undecided** hunk
- J: leave this hunk undecided, go to next hunk
- e: edit the current hunk
- ?: help

[source](https://dev.to/jacobherrington/a-quick-guide-to-hunky-git-49no)
