---
title: "doc/QA/bash"
---

Output
--------

**Q**: how to execute an external application `foo` in terminal such that the shell section becomes free to
use and clean? <br>
**A**: use `foo & disown` to execute the application in background and `clear` to clean the terminal. Thus,
the issue is fixed with `foo & disown && clear.`

Tests
------------

**Q**: how to check if an element `x` belongs to an array `A`?<br>
**A**: use the test
```bash
    [[ "${A[@]}" =~ "$x" ]]
```
* notice that in this case the order inside the brackets is the opposite to the other tests.

**Q**: how to check if a command `cmd` is available in the `$PATH`? <br>
**A**: use `which cmd`

**Q**: how to check if the output of a command `cmd` is executable? <br>
**A**: use the test
```bash
    [[ -x "$(command cmd)" ]]
```

**Q**: how to check if an application `app` is installed? <br>
**A**: suppose that `app_cmd` is the command that execute `app`.
1. If `app` is a shell script in the `$PATH`, use `which app_cmd`;
2. otherwise, (e.g if `app` is a shell function called in the `bashrc`), try
```bash
    [[ -x "$(command app_cmd)" ]] || 
    [[ -x "$(command app_cmd -v)" ]] ||
    [[ -x "$(command cmd -h)" ]]
```


Variables
-----------

**Q**: How to create a variable given by a random string? <br>
**A**: use `$RANDOM` to generate a random number and pass it to the hash generator `md5`, as below, where `n`
is the size of the string to be generated.
```bash
    random=$(echo $RANDOM | md5sum | head -c n; echo;)

```

**Q**: Given a full path `path=dir/file`, how to split it into two variables `var1` and `var2` such
that `var1` contains `dir` and `var2` contains `file`?<br>
**A**: Use shell parameter expansion (see [here](https://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html#Shell-Parameter-Expansion)):
```bash
    var1=${path%/*}
    var2=${path##*/}
```
* Alternatively, use
```bash
    var1=$(dirname "$path")
    var2=$(basename "$path")
```

**Q**: Given a file `file=name.ext`, how to split it into two variables `var1` and `var2` such that `var1` contains
only the file name `name` and `var2` contains its extension `.ext`? <br>
**A**: Use shell parameter expansion (see [here](https://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html#Shell-Parameter-Expansion)):
```bash
    var1=${file%.*}
    var2=${file##*.}
```
* The above works even when you don't known the extension of the file. If you already known it, you can get
  the file name using `basename`:
```bash
    var=$(basename name.ext .ext)
```

**Q**: Given a full path `path=basedir/lastdir/file.ext`, how to split it into four variables `var1`, `var2`,
`var3`, `var4` containing `basedir`, `lastdir`, `file` and `.ext`, respectively? <br>
**A**: Use shell parameter expansion twice:
1. firstly split `path` into `x=file.ext` and `y=basedir/lastdir`:
```bash
    x=${path%/*}
    y=${path##*/}

```
2. then split `x` into `var1` and `var2`, and `y` into `var3` and `var4` according to previous answers.

**Q**: How to take a variable `foo` containing spaces and replace them with other symbol as underscores?<br>
**A**: define a new variable as
```bash
    var=$(echo "${foo// /_}")
```
* similar argument works for other patterns. See [here](https://stackoverflow.com/questions/19661267/replace-spaces-with-underscores-via-bash).

**Q**: how to collect the base names of subdirectories of a directory `dir` in a variable `subdirs`?<br>
**A**: 

1. in a general case, mix `find` with `printf`:
```bash
    $(find dir -type d -printf "%f\n")
```
2. in the presence of the `basename` tool, you can also use it: 
```bash
    $(find dir -type d | xargs basename)
```
4. another alternative is:
```bash
    $(find . -type d -exec basename {} \;)
```
*  of course, same argument holds for different settings of `find`, including fixing `depth` or finding for files.

**Q**: How to call a variable `var` inside a `eval` command? <br>
**A**: Use the escape `\`:
```bash
    eval "some_command \$var"
```

**Q**: How to collect the output of a command in a variable `var` without printing its output in the terminal? <br>
**A**: pass the output to `/dev/null`:
```bash
    var=$(your_command > /dev/null)
```
* This avoid printing the output only in the case of a successful execution. In the case of an error, the
  error message is still printed. If you want to avoid even the error message, try the following:
```bash
    var=$(your_command /dev/null 2>&1)
```

Arrays
---------

**Q**: Is it possible to create an array of functions?<br>
**A**: Yes. Just do something like that
```bash
    declare -a array
    array[0]=f_0
    array[1]=f_1
    ...
    
    function f_0(){
        command_0_1
        command_0_2
        ...
    }
    function f_1(){
        command_1_1
        command_1_2
        ...
    }    
    ...
    
```
    
**Q**: how to collect the result of `find` in an array instead of in a variable?<br>
**A**: 

1. if the results do be returned by `find` not contain spaces or
   [globcharacters](https://man.openbsd.org/glob.7), you can use
```bash
    array=`(find dir/ options`)
```
2. in the general case, use [mapfile](https://www.gnu.org/software/bash/manual/bash.html#index-mapfile):
```bash
    mapfile '' array < <(find dir/ options -print0)
```
* see also [here](https://stackoverflow.com/questions/23356779/how-can-i-store-the-find-command-results-as-an-array-in-bash).

**Q**: how to determine the dimension of a multidimensional array `A`? <br>
**A**: In Bash multidimensional arrays are only simulated. If `A` is one of them, its dimensional can be
obtained as the maximal dimension whose next dimensional is trivial. It can be formalized in terms of a  while
loop:
```bash
    element=$A{[0]}
    dim_A=0
    has_element=$(declare -p element 2>/dev/null)
    
    while [[ $has_element =~ "declare -a "]]; do
        dim_A=$(( $dimA + 1 ))
        element=${element[0]}
    done
    echo "dimension of A is $dim_A"

```

Functions
----------

**Q**: How to take spaces into account in the variables of a function `f`?<br>
**A**: call the variables with a double quotes, e.g, 
```bash
    f "$1" "$2"
```

**Q**: how can I add a `if` loop inside a function `f` such that the condition in `if` must be satisfied for
*some* variable in `f`, without specifying which variable is? <br>
**A**: just add a `for` loop in `$@` which represent "any variable":
```bash
    function f(){
        for var in $@; do
            if [[ "$@" == condition ]]; then
                statement
            fi
        done
    }
```
* this is very useful to define options to be passed to the function, because this allow the option to be
  recognized in any variable.

 **Q**: How to define a function that has a variable as parameter? For example, suppose that `var` is a
 variable. How to define a family of functions `f_{$var}` such that for different values of `var` we have
 different functions? <br>
 **A**: use `eval` command:
```bash
    eval "function f_{$var}(){
        command_1
        command_2
        ...
    }"
```

**Q**: Given numbers `n`,`m` and a function `f`, how to collect the output of variables `n,n+1,...,m-1,m` in
an array `array`? <br>
**A**: Use induction to build `array`:
```bash
    declare -a array
    array[0]=$n
    end=$((m-n))
    for (( i=1; i<=m; i++ ))
    do
    j=$(($i+n))
    array[$i]="${array[$i-1]} ${!j}"
    done            
```
* the output is an array of strings such that the `ith` term is the string given by the outputs of variables
  `n,n+1,...,n+i`, separated by an space.
  
**Q**: Given a function `f`, how to collect the output of all its variables `$1,$2,...` in a new variable
`var`?  <br>
**A**:

1. take a particular case of the last answer with `$n=$1` and `$m=$#`;
2. in the end, define the variable 
```bash
    var=${array[$#]}.
```

File Handing
--------------

**Q**: How to add append a file `file` from `N`th line with a given content? <br>
**A**: Use `sed`:
```bash
    sed -i 'Ns/^/your_content/' file
```
