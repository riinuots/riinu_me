---
title: My bash aliases
author: Riinu Ots
date: '2014-05-29'
categories:
  - Unix
tags:
  - alias
  - bash
  - qsub
  - unix
slug: my-bash-aliases
---

If you find yourself using some commands always with the same flags, then it would make sense to define them as alieses, by putting them into your .bashrc file like this (log out and back in for it to take effect):

```
# .bashrc

# Put user specific aliases and functions here
alias ls='ls -al --color=auto'
alias qstat='qstat -a'
alias qsub='qsub -m abe -M myemail@email.com'

alias disk="du * -sh | sort -h"

```

-a for ls shows hidden files (files that start with a dot, like .bashrc) and -l displays more information than just the file/folder names (permissions for example).

_--color=auto _colours folders, executables and symbolic links.

-a for qstat displays more information.

Both -m and -M for qsub mean messages. For -m:

b - Mail is sent at the beginning of the job.

e - Mail is sent at the end of the job.

a - Mail is sent when the job is aborted or rescheduled.

And -M is the flag before the email address(es).

The last one (I call it disk) displays the sizes of one level of subfolders and orders them too (correct ordering is done by the really cool -h option, as apposed to the numeric sort -n, which would think that 1.4GB>1.4TB).
