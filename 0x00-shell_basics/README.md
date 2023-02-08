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

## 8. 
