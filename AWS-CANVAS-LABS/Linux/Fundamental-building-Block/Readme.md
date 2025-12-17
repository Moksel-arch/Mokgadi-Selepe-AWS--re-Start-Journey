# Basic Linux Commands Cheat Sheet

Hey there! This is my personal collection of basic Linux commands that I use all the time. I wrote it to help me remember them and maybe help others who are just getting started. It's nothing fancy—just the stuff I find most useful day to day.

## File System Navigation

- `pwd` – Shows where I am right now (prints the current directory).
- `ls` – Lists files and folders. Add `-l` for more details, `-a` to see hidden files too.
- `cd <folder>` – Changes directory. `cd ..` goes up one level, `cd ~` takes me home.

## Working with Files & Directories

- `mkdir <name>` – Makes a new folder.
- `rmdir <name>` – Deletes an empty folder.
- `touch <file>` – Creates an empty file or updates the timestamp of an existing one.
- `cp <source> <destination>` – Copies files. Use `cp -r` for folders (recursive).
- `mv <source> <destination>` – Moves or renames files/folders.
- `rm <file>` – Deletes a file. `rm -r` deletes a folder and everything inside (be careful!).

## Viewing & Searching Files

- `cat <file>` – Dumps the whole file to the screen.
- `less <file>` – Lets me scroll through a file page by page.
- `head <file>` – Shows the first 10 lines (good for peeking).
- `tail <file>` – Shows the last 10 lines. `tail -f` is great for watching logs live.
- `grep <pattern> <file>` – Searches for text. `-i` makes it case-insensitive, `-r` searches folders recursively.
- `find <path> -name "<pattern>"` – Finds files by name.

## Cut Command

The `cut` command pulls out specific parts from each line in a file.

You tell it what to extract:
- `-b` for bytes
- `-c` for characters
- `-f` for fields (columns)
- `-d` to set the delimiter (needed with `-f`)

Some examples I use:
- `cut -d ',' -f 1 names.csv` → gets the first column (comma-separated)
- `cut -c 1-2 names.csv` → first two characters of each line
- `cut -c 4- names.csv` → from character 4 to the end
- `cut -c -3 names.csv` → first three characters only

## Sed Command (Simple Find & Replace)

`sed` is great for replacing text.

Basic: `sed 's/old/new/' file.txt` → replaces first "old" with "new" on each line.

- Add `g` at the end: `sed 's/old/new/g'` → replaces all on each line
- Replace only the 5th: `sed 's/old/new/5'`

You can pipe stuff into it: `echo "hello page" | sed 's/page/website/'`

## Sort Command

`sort` puts lines in order.

By default it sorts alphabetically, numbers first, then lowercase before uppercase.

Useful flags:
- `-r` → reverse order
- `-n` → numeric sort
- `-k 2` → sort by second column
- `-u` → remove duplicates
- `-o output.txt` → save to a file

## Awk Command

`awk` is a mini programming language for processing text. Super powerful for columns.

Basic: `awk '{ print $1 }' file.txt` → prints first column (space-separated by default)

- `-F ','` → use comma as separator
- `awk -F ',' '{ print $3 }' file.csv` → third column
- `awk -F ',' '$2 > 35 { print $1 }' file.csv` → print first column only if second > 35
- Add `BEGIN` and `END` blocks for headers/footers

## Permissions & Ownership

- `chmod 644 file.txt` – Sets permissions (owner read/write, others read).
- `chown user:group file` – Changes owner and group.
- `chgrp group file` – Changes just the group.

## System Info & Processes

- `whoami` – Tells me which user I am.
- `ps aux` – Lists all running processes.
- `top` (or `htop` if installed) – Watch CPU/memory live.
- `kill <pid>` – Stops a process. `kill -9` forces it.

## Package Management

**Ubuntu/Debian:**
- `sudo apt update`
- `sudo apt upgrade`
- `sudo apt install <package>`

**Red Hat/CentOS:**
- `sudo yum update`
- `sudo yum install <package>`

## Disk & Networking

- `df -h` – Shows disk space in human-readable format.
- `du -sh <folder>` – How much space a folder uses.
- `ping google.com` – Checks if host is reachable.
- `ip addr show` – Shows my IP addresses.
- `ssh user@host` – Logs into remote server.
- `scp file user@host:/path` – Copies files over SSH.

## Archives & Compression

- `tar -cvf archive.tar files/` – Create tarball
- `tar -xvf archive.tar` – Extract
- `gzip file` – Compress (makes .gz)
- `zip -r archive.zip folder/` – Zip a folder

## Handy Tricks

- `history` – See past commands
- `!<number>` – Repeat a command from history
- `Ctrl + R` – Search history backwards
- `man <command>` – Opens the manual (best help ever)

That's pretty much it! These are the commands I reach for most often. Hope someone finds it useful.

If you have questions, feel free to reach out:

---
Contacts:
- Mokgadi: 067 719 3860
- mokgadi9939@gmail.com
