# Bandit Levels 0 to 10



## Level 0 → 1

### Objective

Find the password in the readme file in the home directory.

### Commands Used

    ls
    cat readme

### Explanation

Used `ls` to list files, found `readme`, and used `cat` to display its contents.





## Level 1 → 2

### Objective

Read the contents of a file named `-`.

### Commands Used

    cat ./-

### Explanation

The file name `-` is interpreted as a special character, so prefixing it with `./` tells the shell it is a file in the current directory.



## Level 2 → 3

### Objective

Read a file whose name contains spaces.

### Commands Used

    cat "spaces in this filename"

### Explanation

Quoting the filename handles spaces properly when referencing it in the command line.



## Level 3 → 4

### Objective

Find and read a hidden file.

### Commands Used

    ls -a
    cat .hidden

### Explanation

`ls -a` lists all files including hidden ones that start with a dot. Then `cat` displays the file contents.



## Level 4 → 5

### Objective

Find the human readable file among many binary files.

### Commands Used

    file inhere/*
    cat inhere/-file07

### Explanation

The `file` command shows each file’s type. The one labelled ASCII text is human readable.



## Level 5 → 6

### Objective

Locate a specific file by size and type.

### Commands Used

    find -maxdepth 2 -type f -size 1033c
    cat ./maybehere07/.file2

### Explanation

Used `find` to search within two directory levels for a file of size 1033 bytes, then displayed its contents.



## Level 6 → 7

### Objective

Find a file owned by a specific user and group.

### Commands Used

    find / -type f -size 33c -user bandit7 -group bandit6 2>/dev/null
    cat /var/lib/dpkg/info/bandit7.password

### Explanation

`find` searched the entire filesystem for a file with matching ownership and size.  
`2>/dev/null` hides permission error messages.



## Level 7 → 8

### Objective

Find the line containing the word `millionth`.

### Commands Used

    grep "millionth" data.txt

### Explanation

`grep` searches for matching text patterns and prints the lines containing them.



## Level 8 → 9

### Objective

Find the unique line in the file.

### Commands Used

    sort data.txt | uniq -u

### Explanation

Sorted the file alphabetically, then used `uniq -u` to print only the line that appears once.



## Level 9 → 10

### Objective

Extract human readable text from a binary file.

### Commands Used

    strings data.txt

### Explanation

`strings` extracts readable ASCII text from binary files.