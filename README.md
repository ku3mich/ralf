## RALF - Recursive ALF

A small try to extend [ALF](https://github.com/DannyBen/alf)

files:

-   `alf.conf` contains a small example of usage more advanced aliasing for kubectl
-   `.ralf` helper functions

## Install

-   install [ALF](https://github.com/DannyBen/alf)
-   put your(or sample `alf.conf`) into your `$HOME`
-   put `.ralf` into your `$HOME`
-   add to `.profile`

```
. $HOME/.ralf
```

-   run

```
. .profile
alf save 1>/dev/null
. .bash_aliases
```

## Settings

-   `RALF_VERBOSE_ALIAS_EXEC` when set to not empty output to `STDERR` a final command
-   `RALF_SHALL_EXEC` when set to not empty allows `ralf` to execute a final command

## Examples

```

k g p
executing: |kubectl get pod|

k sys g d
executing: |kubectl -n kube-system get deployment|

k sys g s
executing: |kubectl -n kube-system get service|

```
