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
drwxrwxr-x 3 USER USER 4096 Dec 13 08:35 .
drwxrwxr-x 4 USER USER 4096 Dec 13 08:35 ..
drwxrwxr-x 2 USER USER 4096 Dec 13 08:35 directory
-rw-rw-r-- 1 USER USER    0 Dec 13 08:35 .dotfile
-rw-rw-r-- 1 USER USER    0 Dec 13 08:35 regular-file.txt
```
