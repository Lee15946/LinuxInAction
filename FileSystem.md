`passwrd`: change password for user

There are two paths to navigate to a filesystem

### Create Files and Directories
- Creating files
  - `touch`
  - `cp`
  - `vi`
- Creating Directories
  - `mkdir`

- `ls -ltr`: list everything as time order reverse
- `cp -R`: command to copy a directory

### Find Files and Directories
- Two main commands are used to find files/directories
  - `find`
  - `locate`
- `locate` uses a prebuilt database, which should be regularly updated, while `find` literates over a file system to locate files. Thus, locate is much faster than find, but can be inaccurate if the database (can be seen as a cache) is not updated
- To update locate database, run `updatedb`

### WildCards
- A wildcard is a character that can be used as a substitute for any of a class of characters in a search
  - * - represents zero or more characters
  - ? - represents a single character
  - [] - represents a range of characters
  - \ - as an escape character
  - ^ - the beginning of the line
  - $ - the end of the line
### Soft and Hard Links
- inode = Pointer of number of a file on the hard disk
- Soft Link = Link will be removed if file is removed or renamed
  - ln -s
- Hard Link = Deleting renaming or moving the original file will not affect the hard link
  - ln