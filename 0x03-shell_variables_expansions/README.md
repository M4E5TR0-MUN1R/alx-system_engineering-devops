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
- export --> Variables that are exported are referred to as environment variables (GLOBAL variables), these are accessible to child shells.
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
* "$$" --> Expands to the process ID of the shell. Try `echo $$`
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

### 0. Create a script that creates an alias.
* Name: ls
* Value: rm *
```
#!/bin/bash
alias ls="rm *"
```
### 1. Create a script that prints hello user, where user is the current Linux user.
* [Get the Current User in Linux](https://www.baeldung.com/linux/get-current-user)
```
#!/bin/bash
echo hello $USER	
```

### 2. Add /action to the PATH. /action should be the last directory the shell looks into when looking for a program.
* [Adding a New Path in Bash](https://www.baeldung.com/linux/path-variable#adding-to-path)
- `export PATH=$PATH:/some/new/path`
```
#!/bin/bash
export PATH=$PATH:/action
```

### 3. Create a script that counts the number of directories in the PATH.
* [Linux tr Command Syntax](https://phoenixnap.com/kb/linux-tr#:~:text=The%20tr%20command%20is%20a,characters%2C%20and%20basic%20text%20replacement.)
`tr [options] SET1 [SET2]` The tr command is a Linux command-line utility that translates or deletes characters from standard input (stdin) and writes the result to standard output (stdout). 
Use tr to perform different text transformations, including case conversion, squeezing or deleting characters, and basic text replacement.
Since tr can't read a file directly and outputs the results in standard output, 
it is often used with pipes (|) and redirects (>>) to allow more complex file content processing.
`tr WWW www`

* [The wc command is used to find the number of lines](https://www.baeldung.com/linux/bash-count-lines-in-file#:~:text=The%20wc%20command%20is%20used,the%20name%20of%20the%20file.)
The wc command is used to find the number of lines, characters, words, and bytes of a file.
To find the number of lines using wc, we add the -l option. This will give us the total number of lines and the name of the file.

```
#!/bin/bash
echo $PATH | tr ":" "\n" | wc -l
```

### 4. Create a script that lists environment variables.
* [printenv – print all or part of environment](https://www.sanfoundry.com/printenv-command-usage-examples-linux/)
printenv prints the values of the specified environment VARIABLE(s). If no VARIABLE is specified, print name and value pairs for them all. eg `printenv HOME` or `printenv` Where the latter prints all.
```
#!/bin/bash
printenv
```

### 5. Create a script that lists all local variables and environment variables, and functions.
* [Linux set Command & How to Use it {9 Examples}](https://phoenixnap.com/kb/linux-set#:~:text=The%20set%20command%20is%20a,and%20Korn%20shell%20(%20ksh%20).)
The set command is a built-in Linux shell command that displays and sets the names and values of shell and Linux environment variables.
`set [options] [arguments]`
```
#!/bin/bash
set
```

### 6. Create a script that creates a new local variable.
* Name:`BEST`
* Value:`School` 
```
#!/bin/bash
BEST="School"
```
`echo $BEST` would output School.

### 7. Create a script that creates a new global variable.
* Name:`BEST`
* Value:`School` 
* [How to Set Environment Variables {Global and Local}](https://builtin.com/software-engineering-perspectives/how-to-set-environment-variables-linux)
```
LOCAL_VAR="I am a Local Variable"
export GLOBAL_VAR="I am a Global Variable"
echo $LOCAL_VAR
echo $GLOBAL_VAR
unset LOCAL_VAR
unset GLOBAL_VAR
```
Task code
```
#!/bin/bash
export BEST="School"
```

### 8. Write a script that prints the result of the addition of 128 with the value stored in the environment variable TRUEKNOWLEDGE, followed by a new line.
* [Echo command in Linux with examples](https://phoenixnap.com/kb/echo-command-linux#:~:text=Examples%20of%20Echo%20Command,-Here%20are%20some&text=Using%20the%20%2De%20option%20allows,%2De%20'Hello%2C%20World!)
`echo -e "Hello \n World"` Using the -e option wich echo command allows you to use escape characters. These special characters make it easy to customize the output of the echo command.<br>
The echo command uses the following options:
* -n: Displays the output while omitting the newline after it.
* -E: The default option, disables the interpretation of escape characters.
* -e: Enables the interpretation of the following escape characters:
* \\: Displays a backslash character (\).
* \a: Plays a sound alert when displaying the output.
* \b: Creates a backspace character, equivalent to pressing Backspace.
* \c: Omits any output following the escape character.
* \e: The escape character, equivalent to pressing Esc.
* \f: The form feed character, causes the printer to automatically advance to the start of the next page.
* \n: Adds a new line to the output.
* \r: Performs a carriage return.
* \t: Creates horizontal tab spaces.
* \v: Creates vertical tab spaces.
* \NNN: Byte with the octal value of NNN.
* \xHH: Byte with the hexadecimal value of HH.
```
#!/bin/bash
echo -e "$((128+$TRUEKNOWLEDGE))"
```

### 9. Write a script that prints the result of `POWER` divided by `DIVIDE`, followed by a new line.
* `POWER` and `DIVIDE` are environment variables
```
#!/bin/bash
echo "$(($POWER/$DIVIDE))"
```

### 10. Write a script that displays the result of `BREATH` to the power `LOVE`
* `BREATH` and `LOVE` are environment variables
* The script should display the result, followed by a new line
```
#!/bin/bash
echo "$(($BREATH**$LOVE))"
```

### 11. Write a script that converts a number from base 2 to base 10.
* The number in base 2 is stored in the environment variable `BINARY`
* The script should display the number in base 10, followed by a new line
* [Builtin Bash any base to decimal conversion](https://phoxis.org/2012/07/12/builtin-bash-any-base-to-decimal-conversion/)
`echo $((base#number))`<br>
Where the base is the value of the base in which the number is in. The value of base can be from 2 upto 64. After 10 base first lower case characters are used to represent additional base digits, when the base value is greater than 32 upper case characters are used. In the case of base value 63 and 64, the 63rd and 64th digit of the base are the @ and _ symbols respectively.

Also to represent hexadecimal you can start the hex number by 0x or 0X, and to denote an octal number you can start the number with 0 as normal. Like

echo $((0xa))
echo $((012))
Both of these will print out 10, which is the decimal equivalent of 0xa in hex and 012 in octal.

The same can be achieved by

echo $((16#a))
echo $((8#12))
At last for completeness i should also add that without any of the 0x, or 0 appended or the base#number format, plain integers are considered to be in decimal, ie. in base 10 by default.
Although you can only convert any integer base (within 2 and 64, both inclusive) to decimal, and not other base, this can come in handy.<br>
Task Code:
```
#!/bin/bash
echo $((2#$BINARY))
```

### 12. Create a script that prints all possible combinations of two letters, except oo.
* Letters are lower cases, from a to z
* One combination per line
* The output should be alpha ordered, starting with aa
* Do not print oo
* Your script file should contain maximum 64 characters
`echo {a..z}` --> Outputs a,b,c,d...z <br>
`echo {1..26}` --> Outputs 1,2,3,4...26 <br>
`echo {a..z}{1..26}` --> Outputs all combinations of a-z and 1-26 <br>
* [Brace Expansion](http://linuxcommand.org/lc3_lts0080.php)
Perhaps the strangest expansion is called brace expansion. With it, we can create multiple text strings from a pattern containing braces.<br>
`mkdir {2017..2019}-{01..12}` --> Makes directories with first part of name 2017-2019 and second part of name 01-12.
* [Removing Characters from String in Bash](https://linuxhint.com/remove_characters_string_bash/)
`grep -v "query" ` inverts selection. <br>
`sort` Arranges the output in numerical or alphabetic order.
Task code:
```
#!/bin/bash
echo {a..z}{a..z} | tr " " "\n" | sort | grep -v "oo"
```

### 13. Write a script that prints a number with two decimal places, followed by a new line.
* The number will be stored in the environment variable `NUM`.
* [How to Round to 2 Decimal Places in Bash](https://linuxhint.com/round-two-decimal-places-bash/)
```
#!/bin/bash
printf "%.2f\n" $NUM
```

## Additional Tasks!

### 14. Write a script that converts a number from base 10 to base 16. 
* The number in base 10 is stored in the environment variable `DECIMAL`
* The script should display the number in base 16, followed by a new line
```
#!/bin/bash
printf "%x\n" $DECIMAL
```

### 15. Write a script that encodes and decodes text using the rot13 encryption. Assume ASCII.
* [Rot13](https://wiki.linuxquestions.org/wiki/Rot13#:~:text=rot13%20is%20a%20text%20scrambling,%2C%20B%20becomes%20O%2C%20etc.)
rot13 is a text scrambling method to prevent text from being accidentally read, such as the answer to a riddle or joke some might consider offensive. <br>
Example Encoding:
```
$ echo "You are in a twisty maze of passages, all alike." | rot13
Lbh ner va n gjvfgl znmr bs cnffntrf, nyy nyvxr.
```
Example Decoding:
```
$ echo "Lbh ner va n gjvfgl znmr bs cnffntrf, nyy nyvxr." | rot13
You are in a twisty maze of passages, all alike.
```
Only A-Z and a-z is scrambled, other characters and symbols are left untouched.<br>
Here's a long complex shell command to rot13 some text:
```
$ echo "hello there123" | tr 'a-zA-Z' 'n-za-mN-ZA-N'
uryyb gurer123
```
Basically translate a-z and A-Z to their 26th forward counterparts, makes sense?
Task code:
```
#!/bin/bash
tr 'a-zA-Z' 'n-za-mN-ZA-N'
```

### 16. Write a script that prints every other line from the input, starting with the first line.
To Print Even Numbered Lines,<br>
`sed -n 'n;p'`
Print Odd Numbered Lines,
`sed -n 'p;n'`
```
#!/bin/bash
sed -n 'n;p'
```
Since first line is an Odd line, we go with `sed -n 'n;p'`.

Correct Assignment Code Rquires no use of ";" therefore we use
* [paste command](https://www.geeksforgeeks.org/paste-command-in-linux-with-examples/)
* [cut command](https://www.geeksforgeeks.org/cut-command-linux-examples/)
```
#!/bin/bash
paste - - | cut -f1
```
 
### 17. Write a shell script that adds the two numbers stored in the environment variables `WATER` and `STIR` and prints the result.
* `WATER` is in base `water`
* `STIR` is in base `stir`.
* The result should be in base `bestchol`
```
#!/bin/bash
printf '%o\n' $(( 5#$( echo $WATER | tr water 01234) + 5#$( echo $STIR | tr stir. 01234 ) )) | tr 01234567 bestchol
```


