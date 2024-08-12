### Command Syntax

- Command options and arguments
- Command typically have the syntax:
    - command option(s) argument(s)
- Options
    - Modify the way that a command works
    - Usually consist of a hyphen or dash followed by a single letter
    - Some commands accept multiple options which can usually be grouped together after a single hyphen
- Arguments
    - Most commands are used together with one or more arguments
    - Some commands assume a default argument if none is supplied
    - Arguments are optional for some commands and required by others

### Files and Directory Permissions (chmod)

- UNIX is a multi-user system, every file and directory in your account can be protected from or made accessible to other users by changing its access permissions. Every user has responsibility for controlling access to their files
- Permissions for a file or directory may be restricted to by types
- There are 3 types of permissions
    - r - read
    - w - write
    - x - execute = running a program
- Each permission (rws) can be controlled at three levels
    - u - user = yourself
    - g - group = can be people in the same project
    - o - other = everyone on the system
- File or Directory permission can be displayed by running ls -l command
- Command to change permission
    - chmod

### Permission using Numeric Mode

- Permission to a file and directory can also be assigned numerically
    - `chmod ugo+r FILE`
    - `chmod 444 FILE`
- The table below assigns numbers to permissions types

| Number | Permission Type        | Symbol |
|--------|------------------------|--------|
| 0      | No permission          | ---    |
| 1      | Execute                | --x    |
| 2      | Write                  | w--    |
| 3      | Execute + Write        | -wx    |
| 4      | Read                   | r--    |
| 5      | Execute + Read         | r-x    |
| 6      | Write + Read           | rw-    |
| 7      | Execute + Write + Read | rwx    |

### Access Control List

- What is ACL?
    - Access control list (ACL) provides an additional more flexible permission merchanism for file systems. It is designed to assist with UNIX file permissions. ACL allows you to give permissions for any user or group to any disc resource
- Use of ACL:
    - Think of a scenario in which a particular user is not a member of group created by you but still want to give some read or write access, how can you do it without making user a member of group, here comes in picture Access Control Lists, ALC helps up to do this trick
    - Basically, ACLs are used to make a flexible permission mechanism in Linux
    - From Linux man pages, ACLs are used to define more fine-grained discretionary access rights for files and directories
- Commands to assign and remove ACL permissions are:
    - `getfacl`
    - `setfacl`

### Help Commands

- There are 3 types of helps commands
    - `whatis` command
        - `makewhatis` to update dictionary
        - `mandb`
    - command `--help`
    - `man` command

### TAB Completion and Up Arrow

- Hitting TAB key completes the available commands, files or directories
    - `chm TAB`
    - `ls j<TAB>`
    - `cd Des<TAB>`
- Hitting up arrow key on the keyboard returns tha last command ran

### Adding Text to Files (Redirects)

- 3 simple ways tos add text to a file
    - `vi`
    - Redirect command output `>` or `>>`
    - `echo >` or `>>`

### INPUT AND OUTPUT REDIRECTS

- There are 3 directes in Linux
    - Standard input (`stdin`) and it has file descriptor number as 0
    - Standard output (`stdout`) and it has file descriptor number as 1
    - Standard error (`stderr`) and it has file descriptor number as 2
- Output (`stdout`) - 1
    - By default, when running a command, its output goes to the terminal
    - The output of a command can be routed to a file using > symbol
        - `ls -l > listings`
        - `pwd > findpath`
    - If using the same file for additional output or to append to the same file, then use >>
        - `ls -la >> listings`
        - `echo "Hello World" >> findpath`
- Input (`stdin`) - 0
    - Input is used when feeding file contents to a file
    - `cat < listings`
    - `mail -s "Office memo" alluser@abc.com < memoletter`
- Error (`stderr`) -2
    - When a command is executed, we use a keyboard and that is also considered (stdin -0)
    - That command output goes on the monitor and that output is (stdout -1)
    - If the command produced any error on the screen then it is considered (stderr -2)
        - We can use redirects to route errors from the screen
            - E.g `ls -l /root 2> errorfile`
            - `telnet localhost 2> errorfile`

### Standard Output to a File (tee)

- "tee" command is used to store and view (both at the same time) the output of any command
- The command is named after the T-splitter used in plumbing. It basically breaks the output of a program so that it can be both displayed and saved in a file. It does both the tasks simultaneously, copies the result into the specified files or variables and also display the result

### Pipes (|)

- A pipe is used by the shell to connect the output of one command directly to the input of another command
- The symbol for a pipe is the vertical bar (|) The command syntax is:
    - `command1 [arguments] | command2 [arguments]`
    - `ls -ltr | more`
    - `ll | tail -1`

### File Maintenance Commands

- `cp`
- `rm`
- `mv`
- `mkdir`
- `rmdir` or `rm -r`
- `chgrp`
- `chown`

### File Display Commands

- `cat`
- `more`
- `less`
- `head`
- `tail`

### Filters / Text Processors Commands

- `cut`
- `aws`
- `grep` and `egrep`
- `sort`
- `uniq`
- `wc`

### cut - Text Processors Commands

- Cut is a command line utility that allows you to cut parts of lines from specified files or piped data and print the result to standard output. It can be used to cut parts of a line by delimiter, byte position, and character
    - cut filename = Does not work
    - cut --version = Check version
    - cut -c1 filename = List one character
    - cut -c1,2,4 = Pick and chose character
    - cut -c1-3, filename = List range of characters
    - cut -c1-3,6-8 filename = List specific range of characters
    - cut -b1-3 filename = List by byte size
    - cut -d: -f 6 /etc/passwd = List first 6th column separated by :
    - cut -d: -f 6-7 /etc/passwd = List first 6 and 7th column separated by :

### awk - Text Processors Commands

- aws is a utility/language designed for data extraction. Most of the time it is used to extract fields from a file or from an output
    - awk -- version = Check version
    - awk '{print $1}' file = List 1st field from a file
    - ls -l | awk '{print $1, $3}' = List 1 and 3rd filed of ls -l output

## grep/egrep - Text Processors Commands

### sort / uniq - Text Processors Commands

- What are sort and uniq commands?
    - Sort command sorts in alphabetical order
    - Uniq command filters out the repeated or duplicate lines
-

## wc - Text Processors Commands

- What is wc command?
    - The command reads either standard input or a list of files and generate: new line count, word count, and byte count
- wc --version OR wc --help = Check version or help
- wc file = Check file line count, word count and byte count
- wc -l file = Get the number of lines in a file
- wc -w file = Get the number of words in a file
- wc -c file = Get the number of bytes in a file
- wc DIRECTORY = NOT allowed
- ls -l | wc -l = Number of files
- grep keyword | wc -l = Number of keyword lines

## Compress and un-compress (tar, gzip, gunzip)
- tar
  - tar -cvf etc.tar /etc
- gzip
- gzip -d OR gunzip

## Truncate File Size (truncate)
- The Linux truncate command is often used to shrink or extend the size of a file to the specified size
- Command
  - truncate -s 10 filename

# Combining and Splitting Files
- Multiple files can be combined into one and
- One file can be split into multiple files
  - cat file1 file2 file3 > file4 
  - split file4
  - e.g. split -l 300 file.txt childfile
- Split file.txt into 300 lines per file and output to `childfilea`, `childfileb`  and `childfilec`


### Linux VS. Windows Commands














































