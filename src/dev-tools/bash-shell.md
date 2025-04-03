# Bash/Shell Cheatsheet

Commonly used Bash/Shell commands and scripting elements for navigating the file system, manipulating files, working with text, and writing scripts.

## Navigation and File Management

### Navigating Directories

`pwd`
Print the current working directory.

`ls`
List files and directories in the current directory.

`ls -l`
List files and directories in long format (detailed information).

`ls -a`
List all files and directories, including hidden ones.

`ls -lh`
List files and directories in long format with human-readable sizes.

`cd [directory]`
Change the current directory to the specified directory.

`cd ..`
Move up one directory level.

`cd ~`
Go to the home directory.

`cd -`
Go to the previous directory.

### File and Directory Operations

`mkdir [directory]`
Create a new directory.

`rm [file]`
Remove (delete) a file.

`rm -r [directory]`
Remove a directory and its contents recursively.

`rm -rf [directory]`
Forcefully remove a directory and its contents recursively (use with extreme caution!).

`cp [source] [destination]`
Copy a file or directory.

`cp -r [source_directory] [destination_directory]`
Copy a directory and its contents recursively.

`mv [source] [destination]`
Move or rename a file or directory.

`touch [file]`
Create an empty file or update the timestamp of an existing file.

`cat [file]`
Display the contents of a file.

`less [file]`
View the contents of a file page by page.

`head [file]`
Display the first few lines of a file.

`head -n [number] [file]`
Display the first `number` lines of a file.

`tail [file]`
Display the last few lines of a file.

`tail -n [number] [file]`
Display the last `number` lines of a file.

`tail -f [file]`
Follow the contents of a file in real-time (useful for log files).

`find [directory] [options]`
Search for files and directories.

`find . -name "*.txt"`
Find all files with the `.txt` extension in the current directory and its subdirectories.

`find . -type d`
Find all directories in the current directory and its subdirectories.

`find . -type f -size +10M`
Find all files larger than 10MB.

### File Permissions

`chmod [permissions] [file]`
Change file permissions.

`chmod +x [file]`
Make a file executable.

`chmod 755 [file]`
Set permissions to read, write, and execute for the owner, and read and execute for the group and others.

`chown [user]:[group] [file]`
Change the owner and group of a file.

## Text Manipulation

### Searching

`grep [pattern] [file]`
Search for a pattern in a file.

`grep -i [pattern] [file]`
Search for a pattern case-insensitively.

`grep -r [pattern] [directory]`
Search for a pattern recursively in a directory.

`grep -v [pattern] [file]`
Show lines that do not match the pattern.

### Text Processing

`sed 's/[old]/[new]/g' [file]`
Replace text in a file (stream editor).

`sed -i 's/[old]/[new]/g' [file]`
Replace text in a file and save the changes in place.

`awk '{print $1}' [file]`
Print the first field of each line in a file.

`awk -F ',' '{print $2}' [file]`
Print the second field of each line in a comma-separated file.

`sort [file]`
Sort the lines of a file.

`sort -r [file]`
Sort the lines of a file in reverse order.

`sort -n [file]`
Sort the lines of a file numerically.

`uniq [file]`
Remove duplicate lines from a sorted file.

`wc [file]`
Count the number of lines, words, and characters in a file.

`wc -l [file]`
Count the number of lines in a file.

## Redirection and Pipes

`>`
Redirect standard output to a file (overwrites the file).

`>>`
Redirect standard output to a file (appends to the file).

`<`
Redirect standard input from a file.

`|`
Pipe the output of one command to the input of another command.

`ls -l | grep ".txt"`
List files in long format and then filter the output to show only lines containing ".txt".

`cat file1.txt > file2.txt`
Copy the content of file1.txt to file2.txt (overwriting file2.txt).

`cat file1.txt >> file2.txt`
Append the content of file1.txt to file2.txt.

## Scripting

### Variables

`variable="value"`
Assign a value to a variable.

`echo $variable`
Print the value of a variable.

`export variable`
Make a variable available to child processes.

### Control Structures

`if [ condition ]; then [commands]; fi`
Basic if statement.

`if [ condition ]; then [commands]; else [commands]; fi`
If-else statement.

`if [ condition1 ]; then [commands]; elif [condition2]; then [commands]; else [commands]; fi`
If-elif-else statement.

`for variable in [list]; do [commands]; done`
For loop.

`while [ condition ]; do [commands]; done`
While loop.

`case $variable in [pattern1]) [commands];; [pattern2]) [commands];; *) [commands];; esac`
Case statement.

### Operators

`-eq`, `-ne`, `-lt`, `-le`, `-gt`, `-ge`
Numeric comparison operators (equal, not equal, less than, less than or equal, greater than, greater than or equal).

`==`, `!=`
String comparison operators (equal, not equal).

`-z`, `-n`
String length operators (zero length, non-zero length).

`-f`, `-d`, `-e`
File operators (file exists, directory exists, exists).

`&&`
Logical AND.

`||`
Logical OR.

### Functions

`function_name() { [commands]; }`
Define a function.

`function_name`
Call a function.

### Comments

`# This is a comment`
Single-line comment.

## Process Management

`ps`
List running processes.

`ps aux`
List all running processes with detailed information.

`kill [process_id]`
Terminate a process.

`kill -9 [process_id]`
Forcefully terminate a process (use with caution!).

`jobs`
List background jobs.

`fg`
Bring the last background job to the foreground.

`fg %[job_number]`
Bring a specific background job to the foreground.

`bg`
Send the last stopped job to the background.

`bg %[job_number]`
Send a specific stopped job to the background.

## Other Useful Commands

`history`
Show command history.

`!!`
Repeat the last command.

`![number]`
Repeat a command from history by its number.

`alias [alias_name]="[command]"`
Create a command alias.

`unalias [alias_name]`
Remove a command alias.

`clear`
Clear the terminal screen.

`man [command]`
Display the manual page for a command.

`echo [text]`
Print text to the terminal.

`printf "[format]" [arguments]`
Print formatted text.

`date`
Display the current date and time.

`cal`
Display a calendar.

`whoami`
Display the current username.

`sudo [command]`
Execute a command with superuser privileges.

`exit`
Exit the current shell session.
