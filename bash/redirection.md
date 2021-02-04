#### Redirection

Date: 02/04/2021

Command inputs and outputs can be redirected before a command is executed. This works by opening, closing, and duplicating file handles.

(All open files are reffered to by a file descriptor by the kernel. A file handle is a layer on top of that.)

Inputs and outputs:
    * stdout (maps to file descriptor 0)
    * stdin (maps to file descriptor 1)
    * stderr (maps to file descriptor 2)

Redirection:
* `cmd < file` --> cmd's stdin reads from file
* `cmd > file` --> cmd's stout redirects to file
* `cmd >> file` --> appends cmd's stdout to file
* `cmd 1> file` --> cmd's stout redirects to file
* `cmd 2> file` --> cmd's stderr redirects to file
* `cmd &> file` --> cmd's stdout *and* stderr redirect to file
* `cmd1 | cmd2` --> (pipe) redirect cmd1's stdout to cmd2's stdin
---

**Notes:**

* The `&` in `ls > dirlist 2>&1`, for example, is used to indicate that the `1` following is not a file name (instead a file descriptor). This is different from the `&` in `cmd &> file` which redirects the commands stderr and stdout to a file. Additonally, `&>` is equivalent to `>&`, but the former is preferred (less ambiguity about what redirection will be applied).

* Order of redirections is significant

---

Walking through examples:

1. `ls > dirlist 2>&1`
- ls of directory contents is redirected to `dirlist`
- stderr of is also redirected to stdout (which is `dirlist` now)
- so... stdout and stderr are redirected to `dirlist`

2. `ls 2>&1 > dirlist`
- stderr is redirected to stdout (probably the console)
- stdout is redirected to `dirlist`
- so... stderr goes to the console, stdout goes to `dirlist`

3. 
```
myProgram <test1 >myOut
echo $? >>myOut
exProgram <test1 >exOut
echo $? >>exOut
```
- run myProgram on test1 input, output goes to myOut
- appends the return value of myProgram to myOut
- does the same for exProgram
- (useful for testing assignments against an example program with `diff myOut exOut`)

---

Resources:
* https://www.gnu.org/software/bash/manual/html_node/Redirections.html
* https://linux.die.net/Intro-Linux/sect_05_02.html