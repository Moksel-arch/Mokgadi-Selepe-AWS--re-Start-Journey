# **Basic Fundamentals Linux Commands**
<img width="997" height="452" alt="image" src="https://github.com/user-attachments/assets/ada50bbc-e447-4773-84fb-265732c19446" />

📁 File‑system navigation
- pwd – I print the current working directory.
- ls – I list files; ls -l gives me a detailed view, ls -a shows hidden ones.
- cd <path> – I change directories; cd .. takes me up one level, cd ~ drops me back in my home folder.

📂 Working with files & directories
- mkdir <dir> – I create a new folder.
- rmdir <dir> – I delete an empty folder.
- touch <file> – I create an empty file or update its timestamp.
- cp <src> <dest> – I copy files; cp -r copies directories recursively.
- mv <src> <dest> – I move (or rename) files and folders.
- rm <file> – I remove a file; rm -r removes a directory and everything inside (use with care!).

🔍 Viewing & searching
- cat <file> – I dump the whole file to the screen.
- less <file> – I page through a file interactively.
- head <file> – I see the first few lines (default 10).
- tail <file> – I see the last few lines; tail -f follows a log in real‑time.
- grep <pattern> <file> – I search for text; add -i for case‑insensitive, -r for recursive.
- find <path> -name <pattern> – I locate files by name.

🔐 Permissions & ownership
- chmod <mode> <file> – I change permissions (e.g., chmod 644 file.txt).
- chown <user>:<group> <file> – I change the owner and group.
- chgrp <group> <file> – I change just the group.

🧰 System info & processes
- uname -a – I show kernel version and system info.
- whoami – I tell you which user I am.
- ps aux – I list all running processes.
- top / htop – I watch system resources in real‑time.
- kill <pid> – I stop a process; kill -9 forces it.

📦 Package management (Debian/Ubuntu)
- sudo apt update – I refresh the package list.
- sudo apt upgrade – I upgrade all installed packages.
- sudo apt install <pkg> – I install a new package.

📦 Package management (Red Hat/CentOS)
- sudo yum update – I update the system.
- sudo yum install <pkg> – I add a package.

🔧 Services & daemons (systemd)
- systemctl status <service> – I check a service’s status.
- sudo systemctl start <service> – I start a service.
- sudo systemctl enable <service> – I make a service start on boot.

💾 Disk usage
- df -h – I see free space on mounted filesystems.
- du -sh <dir> – I estimate space used by a directory.

🌐 Networking
- ping <host> – I test connectivity.
- ifconfig / ip addr show – I view IP addresses.
- ssh <user>@<host> – I log into a remote machine.
- scp <src> <user>@<host>:<dest> – I copy files over SSH.

📜 Archives & compression
- tar -cvf archive.tar <files> – I create a tarball.
- tar -xvf archive.tar – I extract it.
- gzip <file> – I compress; gunzip decompresses.
- zip -r archive.zip <dir> – I zip a folder; unzip extracts it.

🛠 Miscellaneous handy tricks
- history – I see my command history.
- !n – I repeat command number n from history.
- Ctrl + R – I search my history interactively.
- man <command> – I open the manual page (my go‑to for help).

-Mokgadi: mokgadi9939@gmail.com

