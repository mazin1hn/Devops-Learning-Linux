Bandit: Levels 0–10 🐧

Level 0 → Level 1

Objective: Find the password in the readme file in the home directory.
Commands used:
```bash
ls
cat readme
```
Explanation: Used ls to list files, found readme, and used cat to display its contents.
Extra tip: Exit SSH with exit, Ctrl + D, or ~. if the session hangs.

⸻

Level 1 → Level 2

Objective: Read the contents of a file named “-”.
Commands used:
```bash
cat ./-
```
Explanation: The file name “-” is interpreted as a special character, so prefixing it with ./ tells the shell it’s a file in the current directory.

⸻

Level 2 → Level 3

Objective: Read a file whose name contains spaces.
Commands used:
```bash
cat ‘spaces in this filename’
```
Explanation: Quoting the filename handles spaces properly when referencing it in the command line.

⸻

Level 3 → Level 4

Objective: Find and read a hidden file.
Commands used:
```bash
ls -a
cat .hidden
```
Explanation: ls -a lists all files, including hidden ones (starting with .). Then cat displays the file’s contents.

⸻

Level 4 → Level 5

Objective: Find the human-readable file among many binary files.
Commands used:
```bash
file inhere/*
cat inhere/-file07
```
Explanation: The file command shows each file’s type. The one labeled “ASCII text” is human-readable.

⸻

Level 5 → Level 6

Objective: Locate a specific file by size and type.
Commands used:
```bash
find -maxdepth 2 -type f -size 1033c
cat ./maybehere07/.file2
```
Explanation: Used find to search within two directory levels for a file of size 1033 bytes, then displayed its content.

⸻

Level 6 → Level 7

Objective: Find a file owned by a specific user and group.
Commands used:
```bash
find / -type f -size 33c -user bandit7 -group bandit6 2>/dev/null
cat /var/lib/dpkg/info/bandit7.password
```
Explanation: find searched the entire filesystem for a file with matching ownership and size. 2>/dev/null hides permission errors.

⸻

Level 7 → Level 8

Objective: Find the line containing the word “millionth.”
Commands used:
```bash
grep “millionth” data.txt
```
Explanation: grep searches for matching text patterns and prints lines containing them.

⸻

Level 8 → Level 9

Objective: Find the unique line in the file.
Commands used:
```bash
sort data.txt | uniq -u
```
Explanation: Sorted the file alphabetically, then used uniq -u to print only the line that appears once.

⸻

Level 9 → Level 10

Objective: Extract human-readable text from a binary file.
Commands used:
```bash
strings data.txt
```
Explanation: strings extracts readable ASCII text from binary files.
