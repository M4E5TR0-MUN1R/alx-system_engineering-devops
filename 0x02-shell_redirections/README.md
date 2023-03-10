## Resources

***

* [I/O Redirection](http://linuxcommand.org/lc3_lts0070.php)

* [Special Characters](http://mywiki.wooledge.org/BashGuide/SpecialCharacters)

---

* [passwd Command!](https://www.redhat.com/sysadmin/managing-users-passwd#:~:text=The%20passwd%20command%20changes%20passwords,or%20associated%20password%20validity%20period.)

* [passwd command in Linux with Examples](https://www.geeksforgeeks.org/passwd-command-in-linux-with-examples/)

* [Sort command and its options](https://www.geeksforgeeks.org/sort-command-linuxunix-examples/)

* [Find command](https://www.geeksforgeeks.org/find-command-in-linux-with-examples/)

* [Understanding the Grep Command](https://www.hostinger.com/tutorials/grep-command-in-linux-useful-examples/#:~:text=Grep%2C%20or%20global%20regular%20expression,any%20lines%20that%20contain%20it.)



- sort	Sorts standard input then outputs the sorted result on standard output.

- uniq	Given a sorted stream of data from standard input, it removes duplicate lines of data (i.e., it makes sure that every line is unique).

- grep	Examines each line of data it receives from standard input and outputs every line that contains a specified pattern of characters.

- fmt	Reads text from standard input, then outputs formatted text on standard output.

- pr	Takes text input from standard input and splits the data into pages with page breaks, headers and footers in preparation for printing.

- head	Outputs the first few lines of its input. Useful for getting the header of a file.

- tail	Outputs the last few lines of its input. Useful for things like getting the most recent entries from a log file.

- tr	Translates characters. Can be used to perform tasks such as upper/lowercase conversions or changing line termination characters from one type to another (for example, converting DOS text files into Unix style text files).

- sed	Stream editor. Can perform more sophisticated text translations than tr.

- awk	An entire programming language designed for constructing filters. Extremely powerful.

## Tasks

---

### 0. Write a script that prints ???Hello, World???, followed by a new line to the standard output.
```
#!/bin/bash
echo Hello, World
```

### 1. Write a script that displays a confused smiley "(??o)'.
```
#!/bin/bash
echo \"\(??o\)\'
```

### 2. Display the content of the /etc/passwd file.
```
#!/bin/bash
cat /etc/passwd
```

### 3. Display the content of /etc/passwd and /etc/hosts
* [The cat and tac command](https://www.geeksforgeeks.org/cat-command-in-linux-with-examples/)
To view contents of a file preceding with line numbers. `cat -n filename`
```
#!/bin/bash
cat /etc/passwd /etc/hosts
```

### 4. Display the last 10 lines of /etc/passwd
Tail command is the complementary of head command.The tail command, as the name implies, print the last N number of data of the given input. 
By default it prints the last 10 lines of the specified files. 
If more than one file name is provided then data from each file is precedes by its file name
```
#!/bin/bash
tail /etc/passwd
```

### 5. Display the first 10 lines of /etc/passwd
Head command is the complementary of Tail command. The head command, as the name implies, print the top N number of data of the given input.
By default, it prints the first 10 lines of the specified files. 
If more than one file name is provided then data from each file is preceded by its file name. 
```
#!/bin/bash
head /etc/passwd
```

### 6. Write a script that displays the third line of the file iacta.
* [Head command in Linux with examples](https://www.geeksforgeeks.org/head-command-linux-examples/)
Tail Syntax -->  `tail -n (number_of_lines) (/path/to/file)` And Head syntax --> `head -n (number of lines) (/path/to/file)` Combined `head -n (lines) (path) | tail -n (lines)`
```
#!/bin/bash
head -n 3 iacta | tail -1
```

### 7. Write a shell script that creates a file named exactly \*\\'"Best School"\'\\*$\?\*\*\*\*\*:) containing the text Best School ending by a new line.
For each special character add a backslash.
```
#!/bin/bash
echo "Best School" > \\\*\\\\"'\"Best School\"\\'"\\\\\*\$\\\?\\\*\\\*\\\*\\\*\\\*\:\)
```

### 8. Save current state of directory
Write a script that writes into the file `ls_cwd_content` the result of the command `ls -la`. <br>
If the file `ls_cwd_content` already exists, it should be overwritten. <br> 
If the file `ls_cwd_content` does not exist, create it. <br>
To overwrite a file we redirect standard output using ">", to append we use ">>"
```
#!/bin/bash
ls -la > ls_cwd_content
```

### 9. Write a script that duplicates the last line of the file `iacta`.
Take the last line of file iacta and append it to file iacta!
```
#!/bin/bash
tail -n 1 iacta >> iacta
```

### 10. No more javascript
Write a script that deletes all the regular files (not the directories) with a .js extension that are present in the current directory and all its subfolders.
* [Find And Remove Files With One Command On Fly](https://www.cyberciti.biz/faq/linux-unix-how-to-find-and-remove-files/#:~:text=The%20only%20difference%20between%20above,files%20matched%20by%20file%20pattern.)
* [How to Remove Files Recursively in Linux](https://linuxhint.com/remove-files-recursively-linux/)
* [35 Practical Examples of Linux Find Command](https://www.tecmint.com/35-practical-examples-of-linux-find-command/)
The basic find command syntax is as follows: `find dir-name criteria action` Where,<br>
* dir-name : Defines the working directory such as look into /tmp/
* criteria : Use to select files such as ???*.sh??? (all files ending with .sh extension)
* action : The find action (what-to-do on file) such as delete the file or print file names and so on.
Basically `find . -name "FILE-TO-FIND" -exec rm [options] {} \;` if you want the search to be case insensitive `find . -iname "FILE-TO-FIND" -exec rm [options] {} \;`
Let???s assume you want to recursively remove all files with a certain extension only. The syntax is the following:<br>
`find <ParentDirectory> -type f -name '*.<Extension>' -print -delete` The print option is not a must when deleting files.
The syntax to remove files by extensions using -exec is the following:
`find <ParentDirectory> -type f -name '*.<Extension>' -exec rm -f {} \;`
* -type f : Only match files and do not include directory names.
* -type d : Only match dirs and do not include files names.
* rm -f option is force.
Task code:
```
#!/bin/bash
find ./ -type -f -name '*.js' -delete
```

### 11. Write a script that counts the number of directories and sub-directories in the current directory.
* The current and parent directories should not be taken into account (NB: current and parent directories will be denoted by `.` and `..` respectively.)
* Hidden directories should be counted
```
#!/bin/bash
find . -type d -not -name "." | wc -l
```

### 12. Create a script that displays the 10 newest files in the current directory.
Requirements:
* One file per line
* Sorted from the newest to the oldest 
* [List One Filename Per Line in Linux](https://www.baeldung.com/linux/list-one-filename-per-line#:~:text=If%20the%20output%20target%20is,output%20a%20file%20per%20line.)
ls -t option sort files from new to old.
```
#!/bin/bash
ls -t1 | head
```

### 13. Create a script that takes a list of words as input and prints only words that appear exactly once.
* Input format: One line, one word
* Output format: One line, one word
* Words should be sorted
script will be run as follows. `cat list | ./13-unique`
* [uniq Command in LINUX with examples](https://www.geeksforgeeks.org/uniq-command-in-linux-with-examples/)
Options For uniq Command: 
1. -c ??? -count : It tells how many times a line was repeated by displaying a number as a prefix with the line.
2. -d ??? -repeated : It only prints the repeated lines and not the lines which aren???t repeated.
3. -D ??? -all-repeated[=METHOD] : It prints all duplicate lines and METHOD can be any of the following: 
	none : Do not delimit duplicate lines at all. This is the default.
	prepend : Insert a blank line before each set of duplicated lines.
	separate : Insert a blank line between each set of duplicated lines.
4. -f N ??? -skip-fields(N) : It allows you to skip N fields(a field is a group of characters, delimited by whitespace) of a line before determining the uniqueness of a line.
5. -i ??? -ignore case : By default, comparisons done are case sensitive but with this option case insensitive comparisons can be made.
6. -s N ??? -skip-chars(N) : It doesn???t compare the first N characters of each line while determining uniqueness. This is like the -f option, but it skips individual characters rather than fields.
7. -u ??? -unique : It allows you to print only unique lines.
8. -z ??? -zero-terminated : It will make a line end with 0 bytes (NULL), instead of a newline.
9. -w N ??? -check-chars(N) : It only compares N characters in a line.
10. ?????? help : It displays a help message and exit.
11. ?????? version : It displays version information and exit.

```
#!/bin/bash
sort | uniq -u
```
### 14. Display lines containing the pattern ???root??? from the file `/etc/passwd`
* [Understanding the grep Command Syntax](https://www.geeksforgeeks.org/grep-command-in-unixlinux/)
The grep filter searches a file for a particular pattern of characters, and displays all lines that contain that pattern. <br>
The pattern that is searched in the file is referred to as the regular expression (grep stands for global search for regular expression and print out). <br>
Syntax:<br> 
`grep [options] pattern [files]`<br>
Options Description:<br>
- -c : This prints only a count of the lines that match a pattern
- -h : Display the matched lines, but do not display the filenames.
- -i : Ignores, case for matching
- -l : Displays list of a filenames only.
- -n : Display the matched lines and their line numbers.
- -v : This prints out all the lines that do not matches the pattern
- -e exp : Specifies expression with this option. Can use multiple times.
- -f file : Takes patterns from file, one per line.
- -E : Treats pattern as an extended regular expression (ERE)
- -w : Match whole word
- -o : Print only the matched parts of a matching line, with each such part on a separate output line.

- -A n : Prints searched line and nlines after the result.
- -B n : Prints searched line and n line before the result.
- -C n : Prints searched line and n lines after before the result.<br>
Task Code:
```
#!/bin/bash
grep -i "root" /etc/passwd
```

### 15. Display the number of lines that contain the pattern ???bin??? in the file `/etc/passwd`
```
#!/bin/bash
grep -i "bin" /etc/passwd | wc -l
```

### 16. Display lines containing the pattern ???root??? and 3 lines after them in the file `/etc/passwd.`
```
#!/bin/bash
grep -iA 3 "root" /etc/passwd
```

### 17. Display all the lines in the file `/etc/passwd` that do not contain the pattern ???bin???.
`grep -v` option is used to invert the selection.
```
#!/bin/bash
grep -v "bin" /etc/passwd
```

### 18. Display all lines of the file `/etc/ssh/sshd_config` starting with a letter.
* include capital letters as well
[Matching the lines that start with a string](https://www.geeksforgeeks.org/grep-command-in-unixlinux/) : The `^` regular expression pattern specifies the start of a line.<br> 
This can be used in grep to match the lines which start with the given string or pattern. <br>
`grep "^name_or_pattern" (filename)`
```
#!/bin/bash
grep "^[a-z]" /etc/ssh/sshd_config 
```

### 19. Replace all characters `A` and `c` from input to `Z` and `e` respectively.
The [tr command](https://phoenixnap.com/kb/linux-tr#:~:text=The%20tr%20command%20is%20a,characters%2C%20and%20basic%20text%20replacement.) is a Linux command-line utility that translates or deletes characters from standard input (stdin) and writes the result to standard output (stdout). 
Use tr to perform different text transformations, including case conversion, squeezing or deleting characters, and basic text replacement.
Since tr can't read a file directly and outputs the results in standard output, it is often used with pipes (|) and redirects (>>) to allow more complex file content processing.<br>
Linux tr [Command Options](https://phoenixnap.com/kb/linux-tr): <br>
The options provide additional character transformation actions. The available options are:<br>
- Option	Description
- -C		Complements the characters in SET1, including every character in the output except the ones specified.
- -c		Complements the values in SET1. Operations apply to characters that are not in the given set.
- -d		Deletes characters from the SET1 input.
- -s 		Squeezes repeated characters specified in the last operand (either SET1 or SET2) and replaces them with a single occurrence of that character.
- -t		Truncates SET1 to the length of SET2.
- -u		Ensures that any output is unbuffered.
- --help	Displays the help file with all available options.
- --version	Displays the program version information.
```
#!/bin/bash
tr "A" "Z" | tr "c" "e"
```

### 20. Create a script that removes all letters `c` and `C` from input.
* Based on the the `/etc/passwd` file
```
#!/bin/bash
tr -d "Cc"
```

### 21. Write a script that reverse its input.
[How To Reverse a String In Unix / Linux Shell?](https://www.cyberciti.biz/faq/how-to-reverse-string-in-unix-shell-script/)
```
#!/bin/bash
rev
```

### 22. Write a script that displays all users and their home directories, sorted by users.
Based on the the `/etc/passwd` file <br>
* [Linux cut Command Explained with 6 Examples](https://phoenixnap.com/kb/linux-cut)
The cut command is a command-line utility that allows you to cut out sections of a specified file or piped data and print the result to standard output. <br> 
The command cuts parts of a line by field, delimiter, byte position, and character.<br>
```
#!/bin/bash
cut -d ":" -f1,6 /etc/password | sort
```

### 23. Write a command that finds all empty files and directories in the current directory and all sub-directories.
* Only the names of the files and directories should be displayed (not the entire path)
* Hidden files should be listed
* One file name per line
* The listing should end with a new line
* You are not allowed to use `basename`, `grep`, `egrep`, `fgrep` or `rgrep`
```
#!/bin/bash
find . -type f,d -empty -print | rev | cut -d "/" -f 1 | rev
```
Explanation:<br>
find all (-empty) files in current directory (.), which are of both file and directory type (-type f,d) then (-print) their paths,<br>
after that reverse the paths so that we get the file and directory names first before anything else. <br>
we then use cut and backslash ("/") the delimiter to take the first field only, we then reverse th output again to obtain file or directory name.

### 24. Write a script that lists all the files with a `.gif` extension in the current directory and all its sub-directories.
* [9 Practical Examples of the cut Command in Linux](https://www.makeuseof.com/cut-command-examples-linux/)
* Hidden files should be listed
* Only regular files (not directories) should be listed
* The names of the files should be displayed without their extensions
* The files should be sorted by byte values, but case-insensitive (file aaa should be listed before file bbb, file .b should be listed before file a, and file Rona should be listed after file jay)
* One file name per line
* The listing should end with a new line
* You are not allowed to use `basename`, `grep`, `egrep`, `fgrep` or `rgrep`
To Extract Text From Start or End Positions <br>
Use the -cn- option to extract text from nth character onwards to the end of the line, where n is the index of a character in the string.
```
#!/bin/bash
find . -type f -iname "*.gif" | sort | rev | cut -d "." -f 2- | rev | tr -d  "/" | cut -c 2-
```
or 
```
find . -name "*.gif" -type f -printf "%f\n" | rev | cut -d. -f2- | rev | LC_ALL=C sort -f
```

### 25. Acrostic
An acrostic is a poem (or other form of writing) in which the first letter (or syllable, or word) of each line (or paragraph, or other recurring feature in the text) spells out a word, message or the alphabet. 
The word comes from the French acrostiche from post-classical Latin acrostichis). 
As a form of constrained writing, an acrostic can be used as a mnemonic device to aid memory retrieval.<a href="https://en.wikipedia.org/wiki/Acrostic"> Read more </a>.
Create a script that decodes acrostics that use the first letter of each line.
* The ???decoded??? message has to end with a new line
* You are not allowed to use `basename`, `grep`, `egrep`, `fgrep` or `rgrep`
```
#!/bin/bash
cut -c 1 | paste -s -d ''
```

### 26. Write a script that parses web servers logs in TSV format as input and displays the 11 hosts or IP addresses which did the most requests.
* Order by number of requests, most active host or IP at the top
* You are not allowed to use grep, egrep, fgrep or rgrep
Format:
```
host    When possible, the hostname making the request. Uses the IP address if the hostname was unavailable.
logname Unused, always -
time    In seconds, since 1970
method  HTTP method: GET, HEAD, or POST
url Requested path
response    HTTP response code
bytes   Number of bytes in the reply
```
Here is an example with one day of logs of the NASA website (1995).
```
julien@ubuntu:/tmp/0x02$ wget https://s3.amazonaws.com/alx-intranet.hbtn.io/public/nasa_19950801.tsv
--2022-03-08 11:08:26--  https://s3.amazonaws.com/alx-intranet.hbtn.io/public/nasa_19950801.tsv
Resolving s3.amazonaws.com (s3.amazonaws.com)... 52.217.171.144
Connecting to s3.amazonaws.com (s3.amazonaws.com)|52.217.171.144|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 782913 (765K) [binary/octet-stream]
Saving to: ???nasa_19950801.tsv???

nasa_19950801.tsv   100%[===================>] 764.56K  --.-KB/s    in 0.008s

2022-03-08 11:08:26 (98.4 MB/s) - ???nasa_19950801.tsv??? saved [782913/782913]

julien@ubuntu:/tmp/0x02$ head nasa_19950801.tsv
host    logname time    method  url     response        bytes
in24.inetnebr.com       -       807249601       GET     /shuttle/missions/sts-68/news/sts-68-mcc-05.txt 200     1839
uplherc.upl.com -       807249607       GET     /       304     0
uplherc.upl.com -       807249608       GET     /images/ksclogo-medium.gif      304     0
uplherc.upl.com -       807249608       GET     /images/MOSAIC-logosmall.gif    304     0
uplherc.upl.com -       807249608       GET     /images/USA-logosmall.gif       304     0
ix-esc-ca2-07.ix.netcom.com     -       807249609       GET     /images/launch-logo.gif 200     1713
uplherc.upl.com -       807249610       GET     /images/WORLD-logosmall.gif     304     0
slppp6.intermind.net    -       807249610       GET     /history/skylab/skylab.html     200     1687
piweba4y.prodigy.com    -       807249610       GET     /images/launchmedium.gif        200     11853
julien@ubuntu:/tmp/0x02$ ./103-the_biggest_fan < nasa_19950801.tsv 
www-relay.pa-x.dec.com
piweba3y.prodigy.com
www.thyssen.com
130.110.74.81
ix-min1-02.ix.netcom.com
uplherc.upl.com
reggae.iinet.net.au
seigate.sumiden.co.jp
ircgate1.rcc-irc.si
s150.phxslip4.indirect.com
torben.dou.dk
julien@ubuntu:/tmp/0x02$ 
```
Task Code:
```
#!/bin/bash
tail  -n +2 | cut -f -1 | sort -k 1 | uniq -c | sort -rnk 1 | head -n 11 | rev | cut -d ' ' -f -1 | rev
```
