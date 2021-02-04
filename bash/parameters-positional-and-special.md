#### Parameters: positional and special

Date: 02/03/2021

---

**Positional parameters** are the passed to a script from a function or the command line.

Example:

```
#!/bin/bash
echo "$1"
echo "$2"
# ... until echo "$n" where n is the nth parameter
```
Run `./test_pos_param.sh first second`, which should output:
```
first
second
```

Checking Positional Parameters on the command line:

`echo $5` right after the process

---

**Special parameters** may referenced, but not assigned to. 

Checking Special Parameters:
* `$#` number of positional parameters
* `$0` name of the shell or script
* `$!` process ID of the most recent job executed in the backgroun
* `$$` process ID of the subshell
* `$-` current option flags
* `$?` exit status of the most recently executed foreground pipeline job 

(taken from [here](https://www.gnu.org/software/bash/manual/html_node/Special-Parameters.html))

---

For example,
```
ls someDirThatDoesNotExist
echo $?
```
should output `2`, indicating a non-fatal error.

Resources:
* https://www.gnu.org/software/bash/manual/html_node/Special-Parameters.html
* https://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html#tag_18_05_02
* https://stackoverflow.com/questions/5163144/what-are-the-special-dollar-sign-shell-variables

