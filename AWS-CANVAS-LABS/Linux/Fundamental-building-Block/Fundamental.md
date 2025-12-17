# **Basic Fundamentals Linux Commands**


<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/ada50bbc-e447-4773-84fb-265732c19446" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/83159a2c-2d2e-4221-9120-fbabb478b1d8" />

***Bash Metacharactares*

<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/d6543748-1a8f-49fd-82af-2801c0063b04" />

***Redirection Operators*

<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/64b275d1-6b50-4d96-bdec-3b7a07da02fb" />

Alert! By default, the >output redirector will overwrite existing file content with no warning.

***Cut Command*

<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/15d1e663-e988-4cfb-9d1f-bbd09433c100" />

- The cut command pulls out specific parts of each line in a file.
- You have to tell it what you’re extracting:
    - -b – bytes
    - -c – characters (columns)
    - -f – fields
    - -d – the delimiter that separates fields (required when using -f)

Here are the examples I noted down:

- cut -d ',' -f 1 names.csv – grab the first field of every record, using a comma as the separator.
- cut -c 1-2 names.csv – take the first two characters of each line.
- cut -b 1-5 names.csv – take the first five bytes of each line (remember, a character can be more than one byte depending on encoding).
- cut -c 1,6,7 names.csv – pull characters 1, 6, and 7 from each record.
- cut -c 4- names.csv – start at character 4 and keep everything to the end of the line.
- cut -c -3 names.csv – keep only the first three characters of each line.

So, cut lets you slice a file by bytes, characters, or fields, as long as you specify the delimiter when you’re working with fields.
File‑system navigation
- pwd – I print the current working directory.
- ls – I list files; ls -l gives me a detailed view, ls -a shows hidden ones.
- cd <path> – I change directories; cd .. takes me up one level, cd ~ drops me back in my home folder.

***The SED COMMAND*

<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/dbc28a59-a46c-4300-8b22-6187b4ccc703" />

- The two examples do the same thing, just in different ways.
    - The first one feeds the output of echo into sed using a pipe (|).
    - The second one tells sed to work directly on a file called example.txt.

- The sed command s/page/website/ changes the word page to website in the input.
    - It only changes the first occurrence on each line unless you tell it otherwise.

- You can control which occurrence gets replaced:
    - sed 's/page/website/5' example.txt → replaces the 5th occurrence on each line.
    - Adding /g (global) → sed 's/page/website/g' example.txt replaces all occurrences on a line.

- sed can do a lot more, like deleting lines or applying changes only to certain line ranges, but the basics are just “find this text and replace it with that text”.

 ***The SORT COMMAND*

 <img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/daadcacf-82f3-4bd9-a1f1-67b42d9b95e2" />

- By default, sort treats the whole line as the key and orders things like this:
    - Lines that start with a number come first.
    - Then lines that start with “a” (or “A”) come before other letters.
    - Lower‑case letters come before upper‑case letters.

- Some handy options:
    - -o – write the sorted output to a file (sort file.txt -o sorted.txt is the same as sort file.txt > sorted.txt).
    - -r – sort in reverse order (largest to smallest, Z‑A).
    - -n – sort numerically when the lines contain numbers.
    - -k – sort by a specific column (useful for table‑style data).
    - -u – remove duplicate lines.
    - -c – check if a file is already sorted; it just tells you yes or no.

That’s the gist of how sort works, explained simply.


***The AWK Command*

<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/8c974bbc-b94a-4c9c-b7b4-88af66d5f704" />

I just read that awk is a handy tool you can run straight away – no compiling needed. 
It’s designed for writing tiny, quick‑run programs, and its name comes from the three developers who created it: Aho, Weinberger, and Kernighan.

- No compilation required – just type the script and go.
- Ideal for small, one‑off programs.
- Named after *A*ho, *W*einberger, and *K*ernighan.


  <img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/d1bc2f17-b880-442b-86e5-da7531b51f64" />

- How awk works
    - No compiling needed – you give it a tiny program and an input file.
    - Syntax: awk options 'program' inputFile.

- Program forms
    - { action } – do something to every record.
    - select_record_or_field { action } – only act on records that match a pattern.

- Common options
    - -F <sep> – set the field separator (e.g., -F , for commas, -F @ for @).

- Examples
    - awk -F , '{ print $3 }' customers.txt → prints the third field of each comma‑separated line.
    - awk -F @ '{ print $1 }' customers.txt → prints everything before the first @ on each line.
    - awk -F , '/[0-9][0-9]/ { print $1 }' names.csv → prints the first field of lines that contain a two‑digit number.
    - awk -F , '$2 > 35 { print $1 }' names.csv → prints the first field where the second field is greater than 35.
    - awk 'BEGIN { print "Start Processing." }; { print $1 }; END { print "Done! :]" }' names.csv → prints a header, then the first field of each record, then a footer.

That’s the gist of what awk is doing, explained simply.

---

Working with files & directories
- mkdir <dir> – I create a new folder.
- rmdir <dir> – I delete an empty folder.
- touch <file> – I create an empty file or update its timestamp.
- cp <src> <dest> – I copy files; cp -r copies directories recursively.
- mv <src> <dest> – I move (or rename) files and folders.
- rm <file> – I remove a file; rm -r removes a directory and everything inside (use with care!).

Viewing & searching
- cat <file> – I dump the whole file to the screen.
- less <file> – I page through a file interactively.
- head <file> – I see the first few lines (default 10).
- tail <file> – I see the last few lines; tail -f follows a log in real‑time.
- grep <pattern> <file> – I search for text; add -i for case‑insensitive, -r for recursive.
- find <path> -name <pattern> – I locate files by name.

Permissions & ownership
- chmod <mode> <file> – I change permissions (e.g., chmod 644 file.txt).
- chown <user>:<group> <file> – I change the owner and group.
- chgrp <group> <file> – I change just the group.

System info & processes
- uname -a – I show kernel version and system info.
- whoami – I tell you which user I am.
- ps aux – I list all running processes.
- top / htop – I watch system resources in real‑time.
- kill <pid> – I stop a process; kill -9 forces it.

Package management (Debian/Ubuntu)
- sudo apt update – I refresh the package list.
- sudo apt upgrade – I upgrade all installed packages.
- sudo apt install <pkg> – I install a new package.

Package management (Red Hat/CentOS)
- sudo yum update – I update the system.
- sudo yum install <pkg> – I add a package.

Services & daemons (systemd)
- systemctl status <service> – I check a service’s status.
- sudo systemctl start <service> – I start a service.
- sudo systemctl enable <service> – I make a service start on boot.

Disk usage
- df -h – I see free space on mounted filesystems.
- du -sh <dir> – I estimate space used by a directory.

Networking
- ping <host> – I test connectivity.
- ifconfig / ip addr show – I view IP addresses.
- ssh <user>@<host> – I log into a remote machine.
- scp <src> <user>@<host>:<dest> – I copy files over SSH.

Archives & compression
- tar -cvf archive.tar <files> – I create a tarball.
- tar -xvf archive.tar – I extract it.
- gzip <file> – I compress; gunzip decompresses.
- zip -r archive.zip <dir> – I zip a folder; unzip extracts it.

Miscellaneous handy tricks
- history – I see my command history.
- !n – I repeat command number n from history.
- Ctrl + R – I search my history interactively.
- man <command> – I open the manual page (my go‑to for help).

-Mokgadi: mokgadi9939@gmail.com

