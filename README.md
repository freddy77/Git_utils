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

