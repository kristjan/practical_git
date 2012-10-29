!SLIDE

# `git checkout` moves `HEAD` #

## `git checkout testing` ##

![Head](head-switched-branch.png)

!SLIDE commandline incremental

.notes .
`git checkout foo` has the implicit argument `HEAD`
`git checkout` actually updates files in your working tree to match the version
in the tree you specify. If you give no paths (ie, update everything), you're in
a state indistinguishable from that tree.
This is one of the few things that can destroy data

## `git checkout` **sometimes** moves `HEAD` ##

    $ git status
      # On branch master
      # Changes not staged for commit:
      #   (use "git add <file>..." to update what will be committed)
      #   (use "git checkout -- <file>..." to discard changes in working directory)
      #
      # modified:   foo
      #
      no changes added to commit (use "git add" and/or "git commit -a")

    $ git checkout foo

    $ git status
        On branch master
      nothing to commit (working directory clean)

