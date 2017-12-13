# Linux Command Line Tools

 * [cat](#cat)
 * [ls](#ls)
 * [man](#man)
 * [Grep](#grep)
 * [chmod](#chmod)
 * [chown](#chown)
 * [tail](#tail)
 * [ps](#ps)
 * [vim](#vim)
 * [git](#git)
 * [ifconfig](#ifconfig)

## cat

### Description
```Bash
Outputs the contents of a file.
```

### Syntax
```Bash
cat [FILE]
```

### Example

##### Command
```Bash
cat hello.txt
```
##### Output
```Bash
hello
```

## ls

### Description
```Bash
Lists the files in a given directory.
```

### Syntax
```Bash
ls [FLAGS] [DIRECTORY]
```

### Commonly Used Flags
```Bash
-l -> output long listing format (datetime modified, permissions, etc..)
-a -> show dotfiles
-r -> reverse sorting order
-R -> recursive
-X -> sort alphabetically
```

### Example

##### Command
```Bash
ls -al
```
##### Output
```Bash
drwxrwxr-x 3 USER GROUP 4096 Dec 13 08:35 .
drwxrwxr-x 4 USER GROUP 4096 Dec 13 08:35 ..
drwxrwxr-x 2 USER GROUP 4096 Dec 13 08:35 directory
-rw-rw-r-- 1 USER GROUP    0 Dec 13 08:35 .dotfile
-rw-rw-r-- 1 USER GROUP    0 Dec 13 08:35 regular-file.txt
```

## man

### Description
```Bash
Provides a manual for a given command or tool by displaying the associated manual page.
```

### Syntax
```Bash
man [COMMAND/TOOL]
```

### Example

##### Command
```Bash
man cat
```
##### Output
```Bash
CAT(1)                                                                                           User Commands                                                                                           CAT(1)

NAME
       cat - concatenate files and print on the standard output

SYNOPSIS
       cat [OPTION]... [FILE]...

DESCRIPTION
       Concatenate FILE(s) to standard output.

       With no FILE, or when FILE is -, read standard input.

       -A, --show-all
              equivalent to -vET
        .
        .
        .

EXAMPLES
       cat f - g
              Output f's contents, then standard input, then g's contents.

       cat    Copy standard input to standard output.

AUTHOR
       Written by Torbjorn Granlund and Richard M. Stallman.

REPORTING BUGS
       GNU coreutils online help: <http://www.gnu.org/software/coreutils/>
       Report cat translation bugs to <http://translationproject.org/team/>

COPYRIGHT
       Copyright © 2016 Free Software Foundation, Inc.  License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>.
       This is free software: you are free to change and redistribute it.  There is NO WARRANTY, to the extent permitted by law.

SEE ALSO
       tac(1)

       Full documentation at: <http://www.gnu.org/software/coreutils/cat>
       or available locally via: info '(coreutils) cat invocation'

GNU coreutils 8.25                                                                               February 2017     
```

## grep

### Description
```Bash
Outputs lines matching a given pattern. The file may be excluded when input is piped into grep.
```

### Syntax
```Bash
grep [FLAGS] PATTERN {FILE}
```

### Commonly Used Flags
```Bash
-r -> search recursively through a directory instead of a file
-n -> output the line numbers of a match
```

### Example 1

##### Command
```Bash
grep -rn 'file' .
```
##### Output
```Bash
./file.txt:1:This is the contents of the file.
./directory/nested-directory/nested-file.txt:1:This is the contents of the nested file.
```

### Example 2

##### Command
```Bash
ls -laR | grep 'file'
```
##### Output
```Bash
-rw-rw-r-- 1 USER GROUP   34 Dec 13 08:57 file.txt
-rw-rw-r-- 1 USER GROUP   41 Dec 13 08:56 nested-file.txt
```

## chmod

### Description
```Bash
Changes the file mode bits. What this means is that you can change the permissions of a given file or set of files. For example this tool may be used to change a regular file to an executable file.
```

### Syntax
```Bash
chmod [FLAGS] [MODE]
```

### Commonly Used Flags
```Bash
-R -> recursive
```

### Example

##### Command
```Bash
chmod +x executable-file.sh
```
##### Before
```Bash
-rw-rw-r-- 1 USER GROUP 0 Dec 13 09:08 executable-file.sh
```

##### After
```Bash
-rwxrwxr-x 1 USER GROUP 0 Dec 13 09:08 executable-file.sh
```

## chown

### Description
```Bash
Changes the ownership of a given file.
```

### Syntax
```Bash
chown [FLAGS] [OWNER:GROUP] [FILE/DIRECTORY]
```

### Commonly Used Flags
```Bash
-R -> recursive
```

### Example

##### Command
```Bash
sudo chown root:root directory
```
##### Before
```Bash
.:
total 4
drwxrwxr-x 3 USER GROUP 4096 Dec 13 11:24 directory

./directory:
total 4
-rw-rw-r-- 1 USER GROUP    0 Dec 13 11:24 file.txt
drwxrwxr-x 2 USER GROUP 4096 Dec 13 11:25 nested-directory

./directory/nested-directory:
total 0
-rw-rw-r-- 1 USER GROUP 0 Dec 13 11:25 nested-file.txt
```

##### After
```Bash
.:
total 4
drwxrwxr-x 3 root root 4096 Dec 13 11:24 directory

./directory:
total 4
-rw-rw-r-- 1 root root    0 Dec 13 11:24 file.txt
drwxrwxr-x 2 root root 4096 Dec 13 11:25 nested-directory

./directory/nested-directory:
total 0
-rw-rw-r-- 1 root root 0 Dec 13 11:25 nested-file.txt
```