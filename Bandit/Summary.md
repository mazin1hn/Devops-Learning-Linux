# Linux Notes and Summary

## Overview

Personal Linux notes from completing OverTheWire Bandit Levels 0 to 20, focused on core shell usage, file handling, permissions, compression, and basic networking.



## Summary

- Built a strong foundation in Linux navigation, permissions, compression, search, and networking basics  
- Learned how to combine small, focused commands into powerful pipelines  
- Gained confidence troubleshooting hidden files, encodings, and user privileges  



## Key Lessons

- Everything in Linux is a file including devices, processes, and sockets  
- The find, grep, cat, and file commands together can solve most inspection tasks  
- Always read the manual using man and chain tools with pipes to discover efficient solutions  



## Core Commands Cheat Sheet



### Navigation and File Management

- `pwd` print working directory  
- `ls -la` list all files including hidden  
- `cd ..` move up a directory  
- `cat`, `less`, `head`, `tail` view file contents  



### Searching and Filtering

- `grep "pattern" file` find lines matching a pattern  
- `grep -n "pattern" file` include line numbers  
- `sort file | uniq -u` show unique lines only  
- `strings file` extract printable text from binary files  



### Finding Files

- `find /path -type f -name "filename"` search by name  
- `find / -type f -size 1033c` search by exact size  
- `find / -type f -user bandit7 -group bandit6 2>/dev/null` filter by owner or group and hide errors  



### File Type and Inspection

- `file file_name` detect file type  
- `xxd -r hexdump.txt > binary` reverse hexdump to binary  



### Compression and Archives

- `gzip -d file.gz` or `gunzip file.gz` decompress gzip  
- `bzip2 -d file.bz2` decompress bzip2  
- `tar -xvf file.tar` extract tar archives  



### Text Transform and Encoding

- `tr 'A-Za-z' 'N-ZA-Mn-za-m'` ROT13 encode or decode  
- `xxd -r` convert hex to binary  



### Networking and Remote Access

- `ssh -i keyfile user@host -p port` SSH with a private key  
- `ssh user@host "command"` run a command remotely  
- `telnet host port` connect to a TCP port  
- `openssl s_client -quiet -connect host:port` test SSL or TLS service  
- `nmap -p 31000-32000 localhost` scan ports  



### Permissions and Ownership

- `ls -l` show permissions and ownership  
- `chmod 600 keyfile` restrict private key file access  
- `chmod +x script.sh` make a file executable  
- `id` show user and group IDs  
- Setuid binaries run with the owner’s privileges  



### Useful Shell Tricks

- `2>/dev/null` suppress permission errors  
- `cmd1 | cmd2` pipe output from one command into another  
- `cmd1 && cmd2` run the second command only if the first succeeds  
- `history | grep term` search command history  



## Bandit Problem Solving Pattern

1. Use `ls -la` to inspect everything in the directory  
2. Use `file` to identify file type such as text, binary, or archive  
3. If hex, use `xxd -r`  
4. If compressed, use `gzip`, `bzip2`, or `tar`  
5. Use `strings`, `grep`, or `sort | uniq` for readable content  
6. For remote levels, use `telnet`, `openssl`, or `ssh`  
7. Manage SSH keys with `chmod 600`  
8. Use `find` with filters to locate specific file attributes  



## Resources

- `man <command>` for detailed help pages  
- `<command> --help` for quick flag reference  
- OverTheWire Bandit https://overthewire.org/wargames/bandit/  
- Stack Overflow https://stackoverflow.com/  