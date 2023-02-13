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

