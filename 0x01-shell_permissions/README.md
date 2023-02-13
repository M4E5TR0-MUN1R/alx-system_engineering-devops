## Resources
* [How to copy permissions from one file to another on Linux](https://www.cyberciti.biz/faq/how-to-copy-permissions-from-one-file-to-another-on-linux/)
* [Permissions](http://linuxcommand.org/lc3_lts0090.php)
* [chmod]()
* sudo
* [su -- How to Use the su Command in Linux with Examples](https://phoenixnap.com/kb/su-command-linux-examples#:~:text=The%20su%20command%20lets%20you,shell%20interpreter%20on%20the%20fly.)
* [chown -- Chown Command in Linux for File Ownership_1 ](https://linuxize.com/post/linux-chown-command/)
* [chown -- Chown Command: Change Owner of File in Linux](https://phoenixnap.com/kb/linux-chown-command-with-examples)
* [chgrp](https://phoenixnap.com/kb/linux-chown-command-with-examples)
* [id](https://phoenixnap.com/kb/linux-chown-command-with-examples)
* [groups](https://phoenixnap.com/kb/linux-chown-command-with-examples)
* whoami
* [adduser --  Linux adduser Command with Examples](https://phoenixnap.com/kb/linux-adduser#ftoc-heading-10)
* useradd
* addgroup

## Notes
### How to make only directories executable and leave files alone
Use `chmod +X` (as opposed to `+x`) which will make only directories executable and leave files alone. 
This is great for recursively fixing a Drupal files directory. For example:
```
chmod -R 664 sites/default/files && chmod -R a+X sites/default/files
```
That will make all your files writeable by you and the server, but not executable, but will also make directories executable (i.e., listable).

### Creating a directory and sets full read, write, execute permissions for all users
[How to Use mkdir Command to Make or Create a Linux Directory](https://phoenixnap.com/kb/create-directory-linux-mkdir-command#:~:text=The%20mkdir%20command%20by%20default,777%20when%20creating%20a%20directory.&text=The%20directory%20with%20rwx%20permissions%20for%20all%20users%20is%20highlighted.)
```
mkdir –m777 directory_name	
```
### How can I change all files belonging to one user to another user?
```
chown --from=oldguy newguy * -R
```
or
```
chown -R --from=:currentgroup :newgroup /some/directory
```
### Starwars from Terminal :computer:
```
telnet towel.blinkenlights.nl
```
If you don't have telnet, you can use the bash built-in tcp pipes.
```
cat < /dev/tcp/towel.blinkenlights.nl/23
```
---
## Tasks

### 0. Create a script that switches the current user to the user betty.
* You should use exactly 8 characters for your command (+1 character for the new line)
* You can assume that the user betty will exist when we will run your script
```
#!/bin/bash
su betty
```

### 1. Write a script that prints the effective username of the current user.
```
#!/bin/bash
whoami
```

### 2. Write a script that prints all the groups the current user is part of.
Note: depending on the user, you will get a different output.
```
#!/bin/bash
groups
```

### 3. Write a script that changes the owner of the file hello to the user betty.
```
#!/bin/bash
chown betty hello
```

### 4. Write a script that creates an empty file called hello.
```
#!/bin/bash
touch hello
```

### 5. Write a script that adds execute permission to the owner of the file hello.
The file hello will be in the working directory
```
#!/bin/bash
chmod u+x hello
```

### 6. Write a script that adds execute permission to the owner and the group owner, and read permission to other users, to the file hello.
The file hello will be in the working directory
```
#!/bin/bash
chmod 754 hello
```

### 7. Write a script that adds execution permission to the owner, the group owner and the other users, to the file hello
* The file hello will be in the working directory
* You are not allowed to use commas for this script
```
#!/bin/bash
chmod a+x hello
```

### 8. Write a script that sets the permission to the file hello as follows:
* Owner: no permission at all
* Group: no permission at all
* Other users: all the permissions
The file hello will be in the working directory You are not allowed to use commas for this script
```
#!/bin/bash
chmod 007 hello
```

### 9. Write a script that sets the mode of the file hello to this:
```
-rwxr-x-wx 1 julien julien 23 Sep 20 14:25 hello
```
* The file hello will be in the working directory.
* You are not allowed to use commas for this script.
```
#!/bin/bash
chmod 753 hello
```

### 10. Write a script that sets the mode of the file hello the same as olleh’s mode.
* The file hello will be in the working directory
* The file olleh will be in the working directory
```
#!/bin/bash
chmod --reference=olleh hello
```

### 11. Directories
Create a script that adds execute permission to all subdirectories of the current directory for the owner, the group owner and all other users.
Regular files should not be changed.
```
#!/bin/bash
chmod +X *
```
### 12. Create a script that creates a directory called my_dir with permissions 751 in the working directory.
```
#!/bin/bash
mkdir -m751 my_dir
```

### 13. Write a script that changes the group owner to school for the file hello
The file hello will be in the working directory
```
#!/bin/bash
chgrp school hello
```

### 14. Owner and group
Write a script that changes the owner to vincent and the group owner to staff for all the files and directories in the working directory.
```
#!/bin/bash
chown vincent:staff *
```

### 15. Symbolic links
Write a script that changes the owner and the group owner of _hello to vincent and staff respectively.
* The file _hello is in the working directory
* The file _hello is a symbolic link
Note: chown -h
```
#!/bin/bash
chown -h vincent:staff _hello
```

### 16. If only
Write a script that changes the owner of the file hello to betty only if it is owned by the user guillaume.
The file hello will be in the working directory
```
#!/bin/bash
chown --from=guillaume betty hello
```

### 17. Write a script that will play the StarWars IV episode in the terminal
```
#!/bin/bash
telnet towel.blinkenlights.nl
```
OR
```
#!/bin/bash
cat < /dev/tcp/towel.blinkenlights.nl/23
```
