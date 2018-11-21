
# _git fetch_ vs _git pull_
https://hackmd.io/fY4B0kPjQuabPx5wYq1mXw?view

When you need to work on a branch other than master that a colleague has pushed to GitHub, you'll most probably want to `git fetch`, rather than `git pull` that branch. Fetching a branch (or all pushed branches) from the remote *will not merge anything* into your local repo, so you won't be obliged to commit or stash your own work before fetching (though it's always a good idea to commit chunks of code that you've tested and know that work and you need).
## git fetch
* When you `git fetch` a branch, `git checkout` to it in order to work on the local copy.
* To fetch all remote branches:
 `$ git fetch origin`
* To fetch a specific branch (e.g a branch named 'someBranch'):
 `$ git fetch origin someBranch`
 You can also fetch master, but if it's been updated, the changes won't become integrated in your local master:
 `$ git fetch origin master`
## git pull
* When you `git pull` a remote branch, you download the code contained in the branch that's stored in a GitHub server and, unless there are conflicts, merge it into your local branch, i.e. into the identically named branch that's on your machine.
* In theory, you could achieve the same result with `git fetch` followed by `git merge`. In practice, it may be more complicated, so `git pull` when you need to merge the remote's code into your own.
* If there are merge conflicts, i.e. differences between the code on your machine and the code you want to download that GitHub cannot resolve automatically, it won't let you merge the two sets of code until you have resolved those conflicts manually.
* If GitHub prevents you from pulling a branch into your local repo and you get stuck, aborting the merge should allow you to restore the branch to the state it was before you pulled the conflicting code.
`$ git merge --abort`

### Sources
* https://help.github.com/articles/fetching-a-remote/
* https://help.github.com/articles/fetching-a-remote/
