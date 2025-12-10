# Bandit Levels 11 to 20



## Level 11 → 12

### Objective

Decode a ROT13-encoded string to find the password.

### Commands Used

    cat data.txt
    cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'

### Explanation

The file contains text encoded using ROT13.  
The `tr` command translates each letter by shifting it 13 places, revealing the original password.



## Level 12 → 13

### Objective

Convert a hexdump back to binary and repeatedly decompress the file until readable text is obtained.

### Commands Used

    xxd -r data.txt > data
    file data
    mv data data.gz && gzip -d data.gz
    mv data data.bz2 && bzip2 -d data.bz2
    mv data data.tar && tar -xvf data.tar

    Repeat until file is ASCII

    cat data8

### Explanation

`xxd -r` converts the hexdump back into binary.  
The `file` command identifies the compression format.  
Each decompression step is applied until the final ASCII file is reached and displayed.



## Level 13 → 14

### Objective

SSH into another account using a provided private key.

### Commands Used

    ssh -i sshkey.private bandit14@localhost
    cat /etc/bandit_pass/bandit14

### Explanation

The `-i` flag specifies the private key used for authentication.  
Once logged in, the password is retrieved from the system password directory.



## Level 14 → 15

### Objective

Connect to a service on a specific port using Telnet to retrieve the password.

### Commands Used

    telnet localhost 30000

### Explanation

Telnet connects to the service running on port 30000 and outputs the password directly in the session.



## Level 15 → 16

### Objective

Use OpenSSL to connect to an SSL service and retrieve the next password.

### Commands Used

    openssl s_client -quiet -connect localhost:30001

### Explanation

`openssl s_client` establishes a secure SSL connection to the service.  
The `-quiet` flag suppresses handshake metadata, allowing the password to be displayed cleanly.



## Level 16 → 17

### Objective

Scan a range of ports, find an active SSL service, connect to it, and retrieve a private key.

### Commands Used

    nmap -p 31000-32000 localhost
    openssl s_client -quiet -connect localhost:31790

### Explanation

`nmap` scans the specified port range to locate active services.  
Connecting to the correct port using OpenSSL returns the password and RSA private key for the next level.



## Level 17 → 18

### Objective

Fix permissions on a private key file, SSH using that key, and compare files to find the differing password.

### Commands Used

    ls -l bandit17.key
    chmod 600 bandit17.key
    ssh -i bandit17.key bandit17@bandit.labs.overthewire.org -p 2220
    diff passwords.new passwords.old

### Explanation

Private keys must have strict permissions before SSH accepts them.  
Once logged in, `diff` compares both files and displays the changed line containing the password.



## Level 18 → 19

### Objective

Run remote commands via SSH or bypass startup scripts to read the password file.

### Commands Used

    ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme

    or

    ssh bandit18@bandit.labs.overthewire.org -p 2220 /bin/bash --norc
    ls
    cat readme

### Explanation

Appending a command to SSH runs it remotely without opening a full shell.  
Using `--norc` prevents Bash from loading startup scripts that block access.



## Level 19 → 20

### Objective

Use a setuid helper program to run a command as the target user and read the next password.

### Commands Used

    ./bandit20-do whoami
    ./bandit20-do cat /etc/bandit_pass/bandit20
    ls -l ./bandit20-do
    ./bandit20-do id

### Explanation

`bandit20-do` is a setuid binary that runs commands with the effective user ID of another user.  
Running it with `cat /etc/bandit_pass/bandit20` reveals the final password.