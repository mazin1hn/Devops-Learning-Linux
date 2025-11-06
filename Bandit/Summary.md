🐧 Linux Notes & Summary

📘 Overview

Personal Linux notes from completing OverTheWire Bandit (Levels 0 to 20), focused on core shell usage, file handling, permissions, compression, and basic networking.

⸻

⚡ Summary
	•	Built a strong foundation in Linux navigation, permissions, compression, search, and networking basics.
	•	Learned how to combine small, focused commands into powerful pipelines.
	•	Gained confidence troubleshooting hidden files, encodings, and user privileges.

🧠 Key Lessons
	•	Everything in Linux is a file: devices, processes, and sockets.
	•	The find, grep, cat, and file commands together can solve most inspection tasks.
	•	Always read the manual (man) and chain tools with pipes (|) to discover more efficient solutions.

⸻

🧩 Core Commands Cheat Sheet

🗂️ Navigation & File Management
	•	pwd: print working directory
	•	ls -la: list all files (including hidden)
	•	cd ..: move up a directory
	•	cat, less, head, tail: view file contents

🔍 Searching & Filtering
	•	grep "pattern" file: find lines matching a pattern
	•	grep -n "pattern" file: include line numbers
	•	sort file | uniq -u: show unique lines only
	•	strings file: extract printable text from binary files

🧭 Finding Files
	•	find /path -type f -name "filename": search by name
	•	find / -type f -size 1033c: search by exact size
	•	find / -type f -user bandit7 -group bandit6 2>/dev/null: filter by owner or group, hide errors

📄 File Type & Inspection
	•	file file_name: detect file type
	•	xxd -r hexdump.txt > binary: reverse hexdump to binary

🗜️ Compression / Archives
	•	gzip -d file.gz or gunzip file.gz: decompress gzip
	•	bzip2 -d file.bz2: decompress bzip2
	•	tar -xvf file.tar: extract tar archives

🔡 Text Transform & Encoding
	•	tr 'A-Za-z' 'N-ZA-Mn-za-m': ROT13 encode or decode
	•	xxd -r: convert hex to binary

🌐 Networking & Remote Access
	•	ssh -i keyfile user@host -p port: SSH with a private key
	•	ssh user@host "command": run a command remotely
	•	telnet host port: connect to a TCP port
	•	openssl s_client -quiet -connect host:port: test SSL or TLS service
	•	nmap -p 31000-32000 localhost: scan ports

🔒 Permissions & Ownership
	•	ls -l: show permissions and ownership
	•	chmod 600 keyfile: restrict private key file access
	•	chmod +x script.sh: make file executable
	•	id: show user and group IDs
	•	Setuid binaries (-rwsr-x---) run with the owner’s privileges

🧰 Useful Shell Tricks
	•	2>/dev/null: suppress permission errors
	•	cmd1 | cmd2: pipe one command’s output into another
	•	cmd && cmd2: run the second only if the first succeeds
	•	history | grep <term>: find a past command

⸻

🧩 Bandit Problem-Solving Pattern
	1.	ls -la: inspect everything in the directory
	2.	file: identify file type (text, binary, archive)
	3.	If hex, use xxd -r; if compressed, use gzip, bzip2, or tar
	4.	Use strings, grep, or sort | uniq for readable content
	5.	For remote levels, use telnet, openssl, or ssh
	6.	Manage keys with chmod 600
	7.	Use find with filters to locate specific file attributes

⸻

🧾 Resources
	•	man <command>: detailed help page
	•	<command> --help: quick flag reference
	•	OverTheWire Bandit
	•	Stack Overflow
