# Bisect

- very useful in solving bugs (regression bugs)
- also useful if you are working in a team and someone's update caused a bug in your code
- `git bisect` essentially allows you to evaluate (via a binary search) each commit from a non-working state to a working state
- it provides a "guide" to check each commit and respond whether it was a `good` commit (code works!) or `bad` commit (code is broken)
- once you find the first commit that "breaks" the code, you know the commit hash
- from that point, running `git bisect reset` will send the checkout to the latest commit
- knowing which commit caused the issue, the code can be evaluated/compared and a bugfix can be issued in a new commit to resolve the broken code

## Steps

1. `git bisect start`
2. `git bisect bad HEAD` (this is the active commit)
3. once you've located a good commit: `git bisect good 7383asdka` (note: the random hash is made up for an example, you would include the correct commit hash)
4. Git will provide an output of how many revisions are in-between a `good` commit and `bad`
5. You can then step through each one indicating whether the code works via `git bisect good` or fails via `git bisect bad`
6. Repeating the step above, eventually Git will guide you to the first bad commit that broke the code. You could then review what code caused the issue, and provide a fix in a new commit, note move on to Step 7 before creating a new commit!
7. Return to the current revision/active working commit via `git bisect reset`
8. Provide the "fix" and commit the changes

[source1](https://flaviocopes.com/git-bisect/)
[source2](https://dev.to/jacobherrington/git-bisect-is-easy-44ol)
[video](https://www.youtube.com/watch?v=P3ZR_s3NFvM)