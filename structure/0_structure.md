!SLIDE subsection

# Structure #

!SLIDE commandline incremental

# Git is a tree #

.notes Actually a collection of `tree`s with a lot of metadata; not going to go
into that

    $ git log --all --graph --pretty=format:'%s'
      * Leaf
      * Branch
      | * Leaf
      | * Branch
      | * Branch
      | | * Leaf
      | |/
      |/|
      * | Branch
      |/
      * Trunk
      | * Leaf
      | * Branch
      | * Branch
      |/
      * Trunk
      * Dirt

!SLIDE small

.notes Contains Tree, author/committer, timestamp, message

# Your tree is made of Commits #

    @@@ diff
    commit f1e97a5d20564f66ad6d27befa5573f7760f85f8
    Author: Kristján Pétursson <kristjan@gmail.com>
    Date:   Mon Oct 29 02:37:24 2012 -0700

        Recommended Reading section

    diff --git a/recommended/recommended.md
               b/recommended/recommended.md
    new file mode 100644
    index 0000000..3b5433a
    --- /dev/null
    +++ b/presentation/recommended/recommended.md
    @@ -0,0 +1,39 @@
    +!SLIDE
    +
    +# Recommended Reading #
    +
                           ...

!SLIDE commandline incremental

.notes Demonstrate the commit lifecycle: Unstaged -> Staged -> Committed

# Committing #

    $ touch foo
    $ git add foo
    $ git status
      # On branch master
      #
      # Initial commit
      #
      # Changes to be committed:
      #   (use "git rm --cached <file>..." to unstage)
      #
      # new file:   foo

    $ git commit
      ".git/COMMIT_EDITMSG" 12L, 288C written
      [master 6e62099] Committing Foo
       0 files changed
       create mode 100644 foo

    $ git status
      # On branch master
      nothing to commit (working directory clean)

!SLIDE

# Committing #

![Commit Lifecycle](commit-lifecycle.png)

!SLIDE commandline small

# Where does this stuff go? #

    $ tree -L 2 .git
      .git
      ├── COMMIT_EDITMSG
      ├── HEAD
      ├── ORIG_HEAD
      ├── config
      ├── description
      ├── hooks
      │   ├── ...
      ├── index
      ├── info
      │   └── exclude
      ├── logs
      │   ├── HEAD
      │   └── refs
      ├── objects
      │   ├── 02
      │   ├── 03
      │   ├── ...
      │   ├── info
      │   └── pack
      ├── refs
      │   ├── heads
      │   ├── remotes
      │   └── tags
      └── rr-cache
