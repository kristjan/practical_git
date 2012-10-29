!SLIDE commandline incremental small

# `git reset` moves `HEAD` #

    $ git log --oneline
      53524cf Change foo's content  # "Bar"
      101ba32 Give Foo content      # "Foo"
      6e62099 Committing Foo        # Empty

    $ git reset 101ba32
      Unstaged changes after reset:
      M foo                         # "Bar"

    $ git log --oneline
      101ba32 Give Foo content      # "Foo"
      6e62099 Committing Foo        # Empty

    $ git diff
      diff --git a/foo b/foo
      index bc56c4d..ebd7525 100644
      --- a/foo
      +++ b/foo
      @@ -1 +1 @@
      -Foo
      +Bar

!SLIDE commandline incremental

# `git reset` is dangerous #

    $ git reset --hard 101ba32
      HEAD is now at 101ba32 Give Foo content

    $ git log --oneline
      101ba32 Give Foo content      # "Foo"
      6e62099 Committing Foo        # Empty

    $ git status
      # On branch master
      nothing to commit (working directory clean)


!SLIDE commandline incremental small

# `git reset` **sometimes** moves `HEAD`

    $ git log --oneline
      53524cf Change foo's content  # "Bar"
      101ba32 Give Foo content      # "Foo"
      6e62099 Committing Foo        # Empty

    $ cat foo
      Bar

    $ git reset 101ba32 foo
      Unstaged changes after reset:
      M foo                         # "Bar"

    $ git log --oneline
      53524cf Change foo's content  # "Bar"
      101ba32 Give Foo content      # "Foo"
      6e62099 Committing Foo        # Empty

    $ cat foo
      Bar

!SLIDE commandline incremental small

# `git reset` can also change the Index

    $ git status
      # On branch master
      # Changes to be committed:
      #
      # modified:   foo
      #
      # Changes not staged for commit:
      #
      # modified:   foo

    $ git diff --cached
      diff --git a/foo b/foo
      index ebd7525..bc56c4d 100644
      --- a/foo
      +++ b/foo
      @@ -1 +1 @@
      -Bar
      +Foo

    $ git diff
      diff --git a/foo b/foo
      index bc56c4d..ebd7525 100644
      --- a/foo
      +++ b/foo
      @@ -1 +1 @@
      -Foo
      +Bar

