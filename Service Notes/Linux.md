# **Bash Scripting Lab – Sequential File Generator**

**Author:** *Mokgadi Selepe*

## Objective

Create an intelligent Bash script that automatically generates batches of **25 empty files** (`Moks1`, `Moks2`, …) and **continues numbering from the highest existing file** — *with no hardcoding*.

---

## Final Script: `create_moks_files.sh`

```bash
#!/bin/bash

# Author: Mokgadi Selepe
# Purpose: Create 25 empty files named Moks1, Moks2, ... and continue from the highest existing number

PREFIX="Moks"

# Find the highest number currently used (if no files exist, start at 0)
if ls ${PREFIX}* 1>/dev/null 2>&1; then
    LAST_NUM=$(ls ${PREFIX}* | grep -o '[0-9]\+' | sort -nr | head -n1)
    START_NUM=$((LAST_NUM + 1))
else
    START_NUM=1
fi

# Create the next 25 files
for ((i=0; i<25; i++)); do
    FILE_NUM=$((START_NUM + i))
    touch "${PREFIX}${FILE_NUM}"
    echo "Created: ${PREFIX}${FILE_NUM}"
done

echo ""
echo "Successfully created 25 new files starting from ${PREFIX}${START_NUM} to ${PREFIX}$((START_NUM + 24))"
```

### Make It Executable

```bash
chmod +x create_moks_files.sh
```

---

## Logic Explained

1. **Check for existing files**
   Uses `ls Moks*` to detect previously created files.

2. **Extract numeric suffixes**
   `grep -o '[0-9]\+'` isolates only digits from filenames.

3. **Find the highest number**
   `sort -nr | head -n1` ensures correct continuation.

4. **Calculate next start index**
   Highest number + 1.

5. **Create the next 25 files**
   Loop generates the next batch sequentially.

If no files exist, numbering begins at **Moks1** automatically.

---

## Proof of Execution

```bash
$ ls -1 Moks* | wc -l
0   # First run → no files

$ ./create_moks_files.sh
Created: Moks1
Created: Moks2
...
Successfully created 25 new files starting from Moks1 to Moks25

$ ./create_moks_files.sh   # Second run
Created: Moks26
...
Successfully created 25 new files starting from Moks26 to Moks50

$ ls -1 Moks* | tail -5
Moks46
Moks47
Moks48
Moks49
Moks50
```

After 3 runs → **75 sequential files created**.

---

## Validation

```bash
ls -lh Moks* | head -10   # First 10 files
ls -lh Moks* | tail -10   # Last 10 files
```

All files remain **0 KB** (empty), proving correct and safe creation.

---

## Key Bash Concepts Demonstrated

* Filename **globbing** (`Moks*`)
* **Command substitution**: `$(...)`
* **Arithmetic expansion**: `$((...))`
* Efficient **pattern extraction** with `grep -o`
* Sorting numeric values with `sort -nr`
* Clean loop construction
* Proper **error suppression** (`>/dev/null 2>&1`)

---

## Result

A safe, intelligent file-generation script that:

* Never duplicates filenames
* Never overwrites existing files
* Always starts at the correct next number
* Works every time, indefinitely

Perfect for labs, automation tasks, or interviews.
---
Contacts:
- Mokgadi: 067 719 3860
- mokgadi9939@gmail.com


