# Shell Programming - Bash

This chapter discuss shell programming. Just as stated in previous chapter, shell is a userland software which provides a text user interface to give command using internal builtin commands and also manage program execution and process, therefore its main function is as command interpreter. User write commands in shell then whenever user push Enter button, shell will interprets and runs the command. Shell also provides a set of programming language constructs which enable developer to automate tasks or doing any other repetitive tasks. This chapter discuss how to create the shell script for that purposes.

## What is Shell Script?

Shell script (or in other OS such as Windows also known as batch file) is a file which its content is a set of instructions - known by shell - to do a specific task. In other word, we may define shell script as source code of programming language which consists of shell builtin commands and other external executable commands. Those are usually mixed and constructed to create a file which can be executed so that whenever that functionalities needed they can be done again using that file.

A shell script must be created specfic to be executed by a specific shell script software. As we may understood, there are some shell software available at this moment. So, when we create a shell script for Bash, it usually can not be executed succesfully using _Fish_ or _Zsh_ or _Tcsh_.

## Structures of Shell Script

A shell script is an ordinary text file - one may creates it using any text editor such as _Vim, Emacs, VSCode, Atom_, etc - which has this structure:

```
+-----------------------------------+
| #!/usr/bin/bashv                  |
| ...                               |
| shell builtin and or external     |
| commands                          |
| ...                               |
| ...                               |
| ...                               |
+---------------------------------- +
```
The first line (__#!/usr/bin/bash__) is called __shebang__ and is used to let the shell knows that all of the contents should be executed by Bash which reside in that directory (__/usr/bin/bash__). The next line should be known and understood by Bash in the form of shell builtin commands and or external commands. For the shell script to be able to be executed, the file mode should be changed to executable (assumming the filename is myfirst.sh):

    chmod +x myfirst.sh

To execute the shell script, type:

    ./myfirst.sh

or if you put the shell script into known PATH for execution (/usr/bin, /usr/local/bin, /home/user/bin, etc - depends of settings), just type:

    myfirst.sh

Example:
_myfirst.sh_
```
#!/usr/bin/bash

clear
echo "Hello"
```

Try to make it executable and the execute it using the guide above. The subsequent section is used to discuss anything which can be used inside the shell script.

## Redirection

Redirection is used to control where the output of a command goes and where the input of a command comes from. Linux usually has these terms and they usually simbolized as file (file
descriptor):

1. __stdin__: standard input stream - e.g. keyboard. File descriptor: _0_
2. __stdout__: standard output stream - e.g. monitor. File descriptor: _1_
3. __stderr__: standard error output stream - usually also on monitor. File descriptor: _2_

The file descriptor part is usually used like this:
    
    cat /etc/passwd 1>/dev/null

That command means that we will display contents of /etc/passwd file to stdout but the stdout is /dev/null (means "there will be no device to handle"). Bash uses these basic redirection:

1. __<:__ input
2. __>:__ output
3. __>>:__ output append

Example:

```
echo "Hello" > output.txt
cat < output.txt
Hello
echo "world" >> output.txt
cat < output.txt
Hello
world
Pipes
```

## Pipes

Pipe is used to take the output of a command on the left part of pipe and put them as the output of the right part of pipe. Take a look at this example:

    ls -la | grep *.rs

The example above is used to list files in current directory and the result (the list) will be grep’ed to find all the files with __.rs__ extension.

## Variables

Variable assignment is used to assign a value to a placeholder. The placeholder is called a variable. The syntax in Bash:

    name=value

Example:
```
salary=5000000
echo $salary
```

There are also some built-in variable:

- $0: name of the script.
- $1 - $9: first 9 arguments to the script
- $#: number of arguments passed to the script.
- $@: all arguments supplied to the script.
- $?: exit status of the most recently run process.
- $$: process ID of current script.
- $USER: username who runs the script.
- $HOSTNAME: hostname where the script runs
- $SECONDS: number of seconds since the script was started.
- $RANDOM: returns a different random number.
- $LINENO: returns current line number in the script.

## User Interface and User Input

Naturally, user interface in shell is very raw. There is ony a command line and this also happens in shell script. For more advanced interaction with user, another software is needed so that developer can use a pretty decent user interface eventhough the result still in shell / console. The software which usually used for that purpose is __dialog__ (https://invisible-island.net/dialog/). Usually __dialog__ is already installed when Linux installation finish. Here is some usage of __dialog__:

    dialog --infobox "Here is the information" 5 20

The example will display information window with the size 5 as the height and 20 as the width. See __dialog — help__ to see more options. For user input, dialog also provides __dialog --inputbox ..., dialog --passwordhox__, etc. For simple user input, read command can be used:

```
#!/bin/bash
echo Hello, what is your name?
read yourname
echo Hello $yourname - good to see you!
```

## Conditionals

Conditional statement in Bash is used to manage flow of program based on condition. This is almost the same as human daily activities such as _"If 1 am a manager then my salary is 8000000"_. Basically, Bash provides __if__ and __case__ for that purpose. To understand that, one needs to also understand about
operation and operator.

### if

Syntax of __if__ as follows:

#### Basic

```
if [ <some test> ]
kthen
    <commands>
fi
```

#### if... else

```
if [ <some test> ]
then
    <commands>
else
    <other commands>
fi
```

#### if... elif... else

```
if [ <some test> ]
then
    <commands>
elif [ <some test> ]
then
    <different commands>
else
    <other commands>
fi
```

Test in if could be combined using:
-  and - &&
-  or - ||

Some common tests:

- __!EXPRESSION__: not expression
- __-n STRING__: length of STRING is greater than zero
- __-z STRING__: lengh of STRING is zero (empty)
- __STRING1 = STRING2__: STRING1 is equal to STRING2
- __STRING != STRING2__: STRING1 is not equal to STRING2
- __INTEGER! -eq INTEGER2__: INTEGER1 is numerically equal to INTEGER2
- __INTEGER! -gt INTEGER2__: INTEGER! is numerically greater than INTEGER2
- __INTEGER! -lt INTEGER2__: INTEGER! is numerically less than INTEGER2
- __-d FILE__: FILE exists and is a directory.
- __-e FILE__: FILE exists.
- __-r FILE__: FILE exists and has read permission
- __-s FILE__: FILE exists and it’s size is greater than zero (not empty).
- __-w FILE__: FILE exists and has write permission
- __-x FILE__: FILE exists and has execute permission

### case

The case statement is used to test that a variable match to a specific pattern and then doing whatever commands based on the result.

```
case <variable> in
<pattern 1>)
    <commands>
    ;;
<pattern 2>)
    <other commands>
    ;;
esac
```

## Looping

Looping is used to do repetitive commands. Basically, Bash provides four ways to handle looping: _while, until, for, & select_. There is also _break_ (to stop looping execution) and _continue_ (to continue to the next loop).

### while

```
while [ <some test> ]
do
    <commands>
done
```

### until

```
until [ <some test> ]
do
    <commands>
done
```

### for

```
for var in <list>
do
    <commands>
done
```

select

```
select var in <list>
do
    <commands>
done
```

## Functions

Function is the smallest unit of program in Bash programming. It encapsulates a set of commands into one unit called function so that it can be reused again. Below is syntac of function:

```
function_name (parameters) {
    ...
    commands
    ...
}
```

or

```
function function_name {
    ...
    commands
    ...
}
```

Function can also accept parameters. Parameters can be accessed using $1, $2, $3, and so on. If a values has to be returned from the function, then use __return__:

```
function_name (parameters) {
    ...
    commands
    ...
    return ...
}
```

## Operators

Some operators have been discussed in previous section. There are also another operators and related statements. We will discuss them in this section.

- __+,-,* /__: addition, subtraction, multiply, divide
- __var++__: increase var variable by 1
- __var--__: decrease var variable by 1
- __% Modulus__: return the remainder after division (modulo)
- __let__ <arithmetic expression>: doing arithmetic operation
- __expr item1 operator item2__: the same with let, but print the answer instead of storing the result in variable.
- __$expression__: execute expression inside
- __${#variable}__: length of variable