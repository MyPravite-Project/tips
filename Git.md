# GIT

## To delete all untracked files

  git clean

## Undoing in Git


### Fixing un-committed mistakes

  git reset --hard HEAD
  
[Undoing in Git - Reset, Checkout and Revert](http://book.git-scm.com/4_undoing_in_git_-_reset,_checkout_and_revert.html)

## Remote

    git remote add [some name] git://github.com/[user]/[project].git
    git fetch [some name]

### Diff
    git diff [some name]/[branch]

### Test the code in temporary read-only non-branch
    git checkout [some name]/[branch]
 
### Merge and commit
    git merge [some name]/[branch]

### Update from remote
    git fetch [some name]
