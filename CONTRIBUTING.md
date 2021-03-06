# How to contribute

## Pull Requests Guidlines

* Fork the repository
* Make changes to the files in `src/` not dc.js
* Add tests to `test/`. Feel free to create a new file if needed.
* Run `grunt test` and fix your patch or other tests as needed
* Run `grunt lint` and fix your patch as needed
* Commit your changes to `src/*` and `test/*` but not any build
  artifacts
* Submit a pull request
* If you merge master or another branch into your patchset, please rebase against master.
* The DC maintainer team will review and build the artifacts when
  merging

## Issue Submission Guidlines

* If you have a problem with your code, please ask your question on stackoverflow.com or the [user group](https://groups.google.com/forum/?fromgroups#!forum/dc-js-user-group)
  * Please try to include an example of your issue on http://jsfiddle.net/ or on http://bl.ocks.org/
* For bugs and feature requests submit a [github issue](http://github.com/NickQiZhu/dc.js/issues)
  * Please include the version of DC you are using
  * If you can, please try the latest version of DC on the [master](https://raw.github.com/NickQiZhu/dc.js/master/dc.js) branch to see if your issue has already been addressed or is otherwise affected by recent changes.

# Merging Pull Requests

_for maintainers_

Ensure origin looks like this in `.git/config`. The key element here is the second fetch statement
```
[remote "origin"]
  url = git@github.com:NickQiZhu/dc.js.git
  fetch = +refs/heads/*:refs/remotes/origin/*
  fetch = +refs/pull/*/head:refs/remotes/origin/pr/*
```

Run these commands (or their approximation):
```
# clean master branch
git stash

# double check your aren't going to blow away local commits
git fetch origin
git checkout master
git diff origin/master

# Merge - subsitute the PR number for $PR. Warning this runs git reset --hard, ensure you are ready
grunt merge:$PR

# manually verify the changes and review the demos/examples

# deploy
git push origin master
grunt web
```
