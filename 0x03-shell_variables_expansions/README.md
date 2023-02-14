# 0x03. Shell, init files, variables and exp

---

## Resources

* [Expansion](http://linuxcommand.org/lc3_lts0080.php)

* [Shell Arithmetic](https://www.gnu.org/software/bash/manual/html_node/Shell-Arithmetic.html)

* [Variables](https://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_02.html)

* [grep command examples in Linux and Unix](https://www.cyberciti.biz/faq/howto-use-grep-command-in-linux-unix/)

* [Shell initialization files](https://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_01.html)

---

* [Linux Source Command with Examples](https://phoenixnap.com/kb/linux-source-command#:~:text=In%20Linux%20systems%2C%20source%20is,to%20be%20read%20and%20run.)

* [Linux Commands All Users Should Know {Ultimate List}](https://phoenixnap.com/kb/linux-commands)

* [Bash printf Command](https://linuxize.com/post/bash-printf-command/)

---

- printenv --> Global variables or environment variables are available in all shells. The env or printenv commands can be used to display environment variables

- set --> Local variables are only available in the current shell. Using the set built-in command without any options will display a list of all variables (including environment variables) and functions.

- unset --> unset command can be used to remove temporary variables from the event and I/O log files when the variables are no longer needed

- export --> Variables that are exported are referred to as environment variables, these are accessible to child shells.

- alias --> `alias push="git push"` Aliases for the root user can be made permanent by entering them in the .bashrc file in the root's home directory, i.e., in /root/.bashrc. System-wide aliases can be put in the /etc/bashrc file. The system needs to be restarted before system-wide aliases can take effect.

- unalias --> syntax:unalias [-a] name(s), The command unalias, which is likewise built into bash and some other shells, is used to remove entries from the current user's list of aliases.  

- .

- source --> source is a built-in shell command that reads and executes the file content.

- printf --> printf [-v var] format [arguments] , printf "Decimal: %d\nHex: %x\nOctal: %o\n" 100 100 100

- /etc/profile --> All settings that you want to apply to all your users' environments should be in this file



## Notes

---

### [~/.bashrc](https://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_01.html)

Today, it is more common to use a non-login shell, for instance when logged in graphically using X terminal windows. Upon opening such a window, the user does not have to provide a user name or password; no authentication is done. Bash searches for ~/.bashrc when this happens, so it is referred to in the files read upon login as well, which means you don't have to enter the same settings in multiple files.



### [/etc/profile](https://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_01.html)

When invoked interactively with the --login option or when invoked as sh, Bash reads the /etc/profile instructions. These usually set the shell variables PATH, USER, MAIL, HOSTNAME and HISTSIZE.

On some systems, the umask value is configured in /etc/profile; on other systems this file holds pointers to other configuration files such as:

* /etc/inputrc, the system-wide Readline initialization file where you can configure the command line bell-style.

* the /etc/profile.d directory, which contains files configuring system-wide behavior of specific programs.



### [Reserved Variables](https://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_02.html)

* HOME --> The current user's home directory; the default for the cd built-in. The value of this variable is also used by tilde expansion.

* PATH --> A colon-separated list of directories in which the shell looks for commands.

* PS1 --> The primary prompt string. The default value is "'\s-\v\$ '".

* OLDPWD --> The previous working directory as set by the cd built-in.



### [Special parameters](https://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_02.html)

The shell treats several parameters specially. These parameters may only be referenced; assignment to them is not allowed.<br>

For example <br>

* $$ --> Expands to the process ID of the shell. Try `echo $$`

* $0 --> Expands to the name of the shell or shell script. Try `echo $0`

* $* --> Expands to the positional parameters, starting from one. When the expansion occurs within double quotes, it expands to a single word with the value of each parameter separated by the first character of the IFS special variable.

```

#!/bin/bash



# positional.sh

# This script reads 3 positional parameters and prints them out.



POSPAR1="$1"

POSPAR2="$2"

POSPAR3="$3"



echo "$1 is the first positional parameter, \$1."

echo "$2 is the second positional parameter, \$2."

echo "$3 is the third positional parameter, \$3."

echo

echo "The total number of positional parameters is $#."

```

* $? --> Expands to the exit status of the most recently executed foreground pipeline.



### [What is Expansion?](http://linuxcommand.org/lc3_lts0080.php)

Each time we type a command line and press the enter key, bash performs several processes upon the text before it carries out our command. We have seen a couple of cases of how a simple character sequence, for example “*”, can have a lot of meaning to the shell. The process that makes this happen is called expansion. With expansion, we type something and it is expanded into something else before the shell acts upon it.



### [How to do command substitution with $() and backticks](https://www.geeksforgeeks.org/shell-scripting-command-substitution/)

Command substitution is a mechanism that is followed by programmers in a shell script. In this mechanism, the output of a command replaces the command itself. Shell operates the expansion by executing a command and then replacing the command substitution with the standard output of the command. In simple words, the output of a UNIX command is bundled and then used as a command.<br>

To understand it in a better way, let us consider an example. The seq command in Linux is used to print numbers from START to END in steps of INCREMENT.<br>

Syntax:<br>

seq START INCREMENT END<br>  

Return type:<br>

Prints numbers from START to END each in the new line by the difference of INCREMENT.<br>

Example:<br>

```

#In the below script we are printing numbers from 2 to 40 with a difference of 2. In other words, we are printing even numbers up to 40.



#!/bin/sh



# your code goes here



seq 2 2 40

```

We can use the output of the above command as a new command. Consider the below script,<br>  

Example:<br>

```

#!/bin/sh

# your code goes here

 

echo $(seq 2 2 40)

```



### [What is the difference between single and double quotes and how to use them properly](http://linuxcommand.org/lc3_lts0080.php)

Single Quotes are used when we need to suppress all expansions.<br>

Double Quotes, If we place text inside double quotes, 

all the special characters used by the shell lose their special meaning and are treated as ordinary characters. 

The exceptions are “$”, “\” (backslash), and “`” (back- quote). 

This means that word-splitting, pathname expansion, tilde expansion, 

and brace expansion are suppressed, but parameter expansion, arithmetic expansion, and command substitution are still carried out. 

Using double quotes, we can cope with filenames containing embedded spaces.

```

[me@linuxbox me]$ ls -l two words.txt

ls: cannot access two: No such file or directory

ls: cannot access words.txt: No such file or directory



[me@linuxbox me]$ ls -l "two words.txt"

-rw-rw-r-- 1 me me 18 2020-02-20 13:03 two words.txt

[me@linuxbox me]$ mv "two words.txt" two_words.txt

```



---

## Tasks

### 0. Write a script that prints “Hello, World”, followed by a new line to the standard output.

```

#!/bin/bash

echo Hello, World

```



### 1. Write a script that displays a confused smiley "(Ôo)'.

```

#!/bin/bash

echo \"\(Ôo\)\'

```



### 2. Display the content of the /etc/passwd file.

```

#!/bin/bash

cat /etc/passwd

```



### 3. Display the content of /etc/passwd and /etc/hosts

```

#!/bin/bash

cat /etc/passwd /etc/hosts

```



### 4. Display the last 10 lines of /etc/passwd

```

#!/bin/bash

tail /etc/passwd

```



### 5. Display the first 10 lines of /etc/passwd

```

#!/bin/bash

head /etc/passwd

```



### 6. Write a script that displays the third line of the file iacta.

```

#!/bin/bash

head /etc/passwd

```




