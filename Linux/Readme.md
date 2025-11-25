# **Bash Scripting Lab**

## About This Project

This project was a challenge to practice **Bash scripting** on Linux. The goal was to create a script that automates file creation in a smart way.

***

## What I Did

*   Wrote a Bash script that:
    *   Creates **25 empty files** using the `touch` command.
    *   Names the files in the format:  
        `<yourName><number>` (for example: `Moks1`, `Moks2`, `Moks3`).
    *   Each time the script runs, it creates the **next batch of 25 files** starting from the last number that already exists.
    *   The script does **not hard-code numbers**. It automatically finds the highest number and continues from there.

*   Tested the script by listing the directory contents to make sure the files were created correctly.

***

## How It Works

1.  The script checks the existing files in the directory.
2.  It finds the highest number in the file names.
3.  It creates 25 new files starting from the next number.
4.  Every time you run the script, it adds another batch of 25 files.

***

## Example

*   First run:  
    Creates files `Moks1` to `Moks25`.
*   Second run:  
    Creates files `Moks26` to `Moks50`.

***

## Why This Is Useful

*   Automates repetitive tasks.
*   Saves time when creating multiple files.
*   Shows how to use loops, variables, and commands in Bash.

***

## How to Run

1.  Make the script executable:
    ```bash
    chmod +x myscript.sh
    ```
2.  Run the script:
    ```bash
    ./myscript.sh
    ```

***

-Mokgadi: mokgadi9939@gmail.com

