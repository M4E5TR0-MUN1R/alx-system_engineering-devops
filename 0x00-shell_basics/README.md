## 0. Write a script that prints the absolute path name of the current working directory.
<pre><code>
#!/bin/bash
pwd
</code></pre>

## 1. Display the contents list of your current directory.
<pre><code>
#!/bin/bash
ls
</code></pre>

## 2. Write a script that changes the working directory to the user’s home directory.
<ul>
<li>You are not allowed to use any shell variables</li>
</ul>
<pre><code>
#!/bin/bash
cd ~
</code></pre>

## 3. Display current directory contents in a long format.
<pre><code>
#!/bin/bash
ls -l
</code></pre>

## 4. Display current directory contents, including hidden files (starting with .). Use the long format.
<pre><code>
#!/bin/bash
ls -a -l
</code></pre>

## 5. Display current directory contents.
<ul>
<li>Long format</li>
<li>with user and group IDs displayed numerically</li>
<li>And hidden files (starting with .)</li>
</ul>
<pre><code>
#!/bin/bash
ls -a -l -n
</code></pre>

## 6. Create a script that creates a directory named my_first_directory in the /tmp/ directory.
<pre><code>
#!/bin/bash
mkdir /tmp/my_first_directory
</code></pre>

## 7. Move the file betty from /tmp/ to /tmp/my_first_directory.
<pre><code>
#!/bin/bash
mv /tmp/betty /tmp/my_first_directory
</code></pre>

## 8. Delete the file betty.
<ul>
<li>The file betty is in /tmp/my_first_directory</li>
</ul>
<pre><code>
#!/bin/bash
rm /tmp/my_first_directory/betty
</code></pre>

## 9. Delete the directory my_first_directory that is in the /tmp directory.
<pre><code>
#!/bin/bash
rm -r /tmp/my_first_directory
</code></pre>

## 10. Write a script that changes the working directory to the previous one.
<pre><code>
#!/bin/bash
cd -
</code></pre>

## 11. Lists
Write a script that lists all files (even ones with names beginning with a period character, which are normally hidden) in the current directory and the parent of the working directory and the /boot directory (in this order), in long format.
<pre><code>
#!/bin/bash
ls -l -a . .. /boot
</code></pre>

## 12. File type
Write a script that prints the type of the file named iamafile. The file iamafile will be in the /tmp directory when we will run your script.
<pre><code>
#!/bin/bash
file /tmp/iamafile
</code></pre>

## 13. symbols, and inhabit symbols 
Create a symbolic link to /bin/ls, named __ls__. The symbolic link should be created in the current working directory.
<a href="https://www.futurelearn.com/info/courses/linux-for-bioinformatics/0/steps/201767#:~:text=A%20symlink%20is%20a%20symbolic,directory%20in%20any%20file%20system."> Linux Symbolic Links Resource </a>
<pre><code>
#!/bin/bash
ln -s /bin/ls ./__ls__
</code></pre>

## 14. Copy HTML files
Create a script that copies all the HTML files from the current working directory to the parent of the working directory, but only copy files that did not exist in the parent of the working directory or were newer than the versions in the parent of the working directory.
<ul>
  <li>You can consider that all HTML files have the extension .html</li>
</ul>
<p>
yes|cp -ruv /from/* /to/. <br>
yes - Answer yes to all the questions.<br>
r - Recursive<br>
u - update<br>
v - Progress<br>
NB: progess isn't needed in this task.<br>
</p>
<pre><code>
#!/bin/bash
cp -ru *.html ..
</code></pre>

## 15. Create a script that moves all files beginning with an uppercase letter to the directory /tmp/u.
You can assume that the directory /tmp/u will exist when we will run your script
<pre><code>
#!/bin/bash
mv [[:upper:]]* /tmp/u
</code></pre>

## 16. Create a script that deletes all files in the current working directory that end with the character ~.
<pre><code>
#!/bin/bash
rm *~ 
</code></pre>

## 17. Create a script that creates the directories welcome/, welcome/to/ and welcome/to/school in the current directory.
<a href="https://www.howtogeek.com/275069/how-to-create-multiple-subdirectories-with-one-linux-command/"> How to Create Multiple Subdirectories with One Linux Command </a> <br>
You are only allowed to use two spaces (and lines) in your script, not more.
<pre><code>
#!/bin/bash
mkdir -p ./welcome/to/school
</code></pre>

## 18. Write a command that lists all the files and directories of the current directory, separated by commas (,).
<a href="https://www.tecmint.com/ls-interview-questions/#:~:text=Yup!,comma%20when%20listing%20contents%20vertically.&text=When%20used%20in%20long%20listing%20format%2C%20switch%20%2Dm%20gets%20useless."> 10 Useful ‘ls’ Command Interview Questions </a> <br>
<a href="https://www.mkssoftware.com/docs/man1/ls.1.asp"> ls Options </a> <br>
<a href="https://www.digitalocean.com/community/tutorials/ls-command-in-linux-unix"> ls command in Linux/UNIX </a> <br>
<a href="https://phoenixnap.com/kb/linux-ls-commands"> 19 Crucial Linux ls Commands to Know </a> <br>
<ul>
<li>Directory names should end with a slash (/) </li>
<li>Files and directories starting with a dot (.) should be listed</li>
<li>The listing should be alpha ordered, except for the directories . and .. which should be listed at the very beginning </li>
<li>Only digits and letters are used to sort; Digits should come first </li>
<li>You can assume that all the files we will test with will have at least one letter or one digit </li>
<li>The listing should end with a new line </li>
</ul>
<pre><code>
#!/bin/bash
ls -amvp
</code></pre>

## 19. Create a magic file
Create a magic file school.mgc that can be used with the command file to detect School data files. School data files always contain the string SCHOOL at offset 0.
<pre><code>

</code></pre>
