# Git_utils
Utilities for git SCM

This project provides some utilities for [git](https://git-scm.com/).
The name of the package is intentionally capital case as in Unix commands
are mostly lower case. This avoid having these command in the way when
normal git command are completed and is a way to say that these tools
are quite experimental and not official.

## Git_go_child

This utility just move HEAD to the direct child (if any) child of HEAD.

Syntax: `Git_go_child` *tag/branch*

On error or if HEAD is already at the commit specified by *tag/branch* the script
returns failure.

This is useful for instance if you want to check that all commits in a given
branch compile

```bash
$ git checkout origin/master # move to initial branch
$ while Git_go_child master && make clean && make; do echo ok; done
```

## Git_merge

The idea of this utility is to manage rebased branches removing commit
with the same **exact** content.

Syntax: `Git_merge` *branch_old* *branch_new*

The script try to recreate the tree of commits merging commits with same
content and reuse available commits if possible. The script will prefer
to reuse commits in the *branch_new* as should be the most updated.

The script wants to be robust and instead of changing your branches add
two new tags named *branch_old*`_merged` *branch_new*`_merged. This to
make sure you don't lose your work.

Currently todo/problems:

* the code is quite messy and the classes are not defined properly.

I use it to make clear where changes happened on the two branches and
manually and incrementally remove the differences.

