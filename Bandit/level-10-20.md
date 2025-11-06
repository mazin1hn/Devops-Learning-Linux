Bandit: Levels 11–20 🐧

Level 11 → Level 12

Objective: Decode a ROT13-encoded string to find the password.
Commands used:
```bash
cat data.txt
echo | cat data.txt | tr ‘A-Za-z’ ‘N-ZA-Mn-za-m’
```
Explanation: The file contains ROT13 text. tr with the ROT13 mapping decodes it to reveal the password.

⸻

Level 12 → Level 13

Objective: Convert a hexdump back to binary and repeatedly decompress until you reach readable text.
Commands used:
```bash
xxd -r data.txt > data
file data
mv data data.gz && gzip -d data.gz
mv data data.bz2 && bzip2 -d data.bz2
mv data data.tar && tar -xvf data.tar

repeat until file is ASCII

cat data8
```
Explanation: xxd -r converts hex dump to binary. Use file to detect compression formats, then gzip -d, bzip2 -d, and tar -xvf as needed until you get an ASCII file to cat.

⸻

Level 13 → Level 14

Objective: SSH into another account using a provided private key.
Commands used:
```bash
ssh -i sshkey.private bandit14@localhost
cat /etc/bandit_pass/bandit14
```
Explanation: ssh -i specifies the private key (identity file) to authenticate as the target user and read the password file.

⸻

Level 14 → Level 15

Objective: Connect to a service on a specific port using Telnet to retrieve the password.
Commands used:
```bash
telnet localhost 30000
```
Explanation: Telnet connects to the service port and returns the password in the session output.

⸻

Level 15 → Level 16

Objective: Use OpenSSL client to connect to an SSL service and get the next password.
Commands used:
```bash
openssl s_client -quiet -connect localhost:30001
```
Explanation: openssl s_client establishes an SSL/TLS connection; the service responds with the password. -quiet suppresses connection metadata.

⸻

Level 16 → Level 17

Objective: Scan a port range, find an open SSL service, connect with OpenSSL and retrieve a private key.
Commands used:
```bash
nmap -p 31000-32000 localhost
openssl s_client -quiet -connect localhost:31790
```
Explanation: nmap discovers open/filtered ports. Connecting to the correct port with openssl s_client returns the password and sometimes an RSA private key used for the next level.

⸻

Level 17 → Level 18

Objective: Fix permissions on a private key file, SSH using that key, and compare files to find the differing password.
Commands used:
```bash
ls -l bandit7.txt
chmod 600 bandit7.txt
ssh -i bandit7.txt bandit17@bandit.labs.overthewire.org -p 2220
diff passwords.new passwords.old
```
Explanation: Private keys must have restrictive permissions (600) before SSH accepts them. Once logged in, diff shows the changed line revealing the password.

⸻

Level 18 → Level 19

Objective: Run remote commands via SSH or bypass startup scripts to read the password file.
Commands used:
```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme

or

ssh bandit18@bandit.labs.overthewire.org -p 2220 /bin/bash –norc
ls
cat readme
```
Explanation: Appending a command to ssh runs it remotely without opening an interactive shell. Using --norc starts bash without reading ~/.bashrc (useful when login scripts block access).

⸻

Level 19 → Level 20

Objective: Use a setuid helper program to run a command as the target user and read the next password.
Commands used:
```bash
./bandit20-do whoami
./bandit20-do cat /etc/bandit_pass/bandit20
ls -l ./bandit20-do
./bandit20-do id
```
Explanation: bandit20-do is a setuid binary that executes commands with the effective UID of another user (bandit20). Running it with cat /etc/bandit_pass/bandit20 returns the password.