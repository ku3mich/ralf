# RALF - Recursive ALF

A small try to extend [ALF](https://github.com/DannyBen/alf)

files:

-   `.ralf.lib` contains alias snippets for a bunch of commands(kubectl, udocker for now)
-   `.ralf` helper functions, should be included into your `.profile` or `.bashrc`
- if your already use [ALF](https://github.com/DannyBen/alf) save your `alf.conf`, it will be overriten by `__update-ralf`

## Install

-   install [ALF](https://github.com/DannyBen/alf)
-   put links to `.conf` files into `~/.ralf.d` folder, e.g.
```
ln -s .ralf.lib/kubctl.conf .ralf.d/kubectl.conf
```
-   put `.ralf` into your `$HOME`
-   add to `.profile` (or `.bashrc`)

```
. $HOME/.ralf
```

-   execute `__update-ralf`

## Settings

-   `RALF_VERBOSE_ALIAS_EXEC` when set to non-empty output to `STDERR` a final command
- `RALF_SHALL_EXEC` when set to non-empty allows `ralf` to execute a final command
  `RALF_DEBUG` outputs some debug info to `STDERR`
- `RALF_VERSION` version of the script

## Examples


### udocker

```
> u cre container image
executing: |udocker create --name=container image|

> u pl image
executing: |udocker pull image|
```

### kubectl

```
> k g p
executing: |kubectl get pod|

# sys adds '-n kube-system'
> k sys g d
executing: |kubectl -n kube-system get deployment|

> k sys g s
executing: |kubectl -n kube-system get service|

# ln adds '-l name='
> k ln NAME g p
executing: |kubectl -l name=NAME get pod|

> k sys ln NAME g p
executing: |kubectl -n kube-system -l name=NAME get pod|

> k ln NAME gd
executing: |kubectl -l name=NAME get deployment|

> k ln host g p
executing: |kubectl -l name=host get pod|
NAME                    READY   STATUS    RESTARTS        AGE
host-86c774dbc8-h582f   1/1     Running   3 (2d22h ago)   3d22h

> k gd
executing: |kubectl get deployment|
NAME   READY   UP-TO-DATE   AVAILABLE   AGE
host   1/1     1            1           3d23h

```
