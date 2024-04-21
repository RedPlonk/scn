Navigating the file system
==========================

- Part 2: Navigating the File System
  - Commands: pwd, cd, ls, mkdir, rmdir, find
  - Parts of a path (root, system directory)
  - Searching for files
  - File permissions

## Introduction to Linux File System

Linux, a powerful and versatile operating system, is renowned for its stability and robustness. Its file system is a critical component that any user or administrator must understand to effectively manage the operating system. This understanding not only aids in basic file management but also enhances security and system administration.

## Understanding Parts of a Path

### Root Directory

In Linux, the root directory is denoted by a slash (`/`). It is the very base of the directory structure from which all other directories and files stem. Unlike Windows, which uses a drive letter for each storage device (e.g., C:\), Linux treats all storage devices as part of a single directory tree with the root directory at its base.

### System Directories

Below the root directory, Linux features several important system directories, each serving a specific function:

   - `/bin` - Contains essential binary executables.
   - `/etc` - Hosts configuration files for the system.
   - `/home` - Contains the home directories of all users except the root user.
   - `/root` - The home directory for the root user.
   - `/var` - Where variable files such as logs and databases are stored.
   - `/usr` - Used for user programs and non-essential system binaries.

### Home Directory

Each user on a Linux system has a home directory, typically found under `/home/username`. It's a personal space where user files and subdirectories are stored, such as documents, downloads, and configuration files specific to the user.

## How to Search for Files in Linux

Linux offers several powerful tools for locating files and directories within its file system. Among these, the `find` and `locate` commands are the most commonly used due to their flexibility and efficiency.

### Using the `find` Command

The `find` command is highly versatile and allows you to search for files and directories based on a variety of criteria such as name, type, size, and modification time. Here’s how you can use it:

- **Search by Name:** To find all files named `example.txt` in the `/home` directory and its subdirectories:
  ```bash
  find /home -name example.txt
  ```
- **Search by Type:** To find all directories (type `d`) in `/var`:
  ```bash
  find /var -type d
  ```
- **Search by Modification Time:** To find files modified in the last 7 days:
  ```bash
  find / -mtime -7
  ```
- **Combining Criteria:** To find all `.jpg` files larger than 1MB modified in the last 30 days in the `/pictures` directory:
  ```bash
  find /pictures -type f -name '*.jpg' -size +1M -mtime -30
  ```

### Using the `locate` Command

The `locate` command is another useful tool for finding files by name. It uses a database updated by `updatedb` (usually run daily via cron). It’s faster than `find` for just searching by filename because it searches this pre-built database instead of scanning the directory tree.

- **Basic Usage:** To find files that include `report` in their name:
  ```bash
  locate report
  ```

It's important to note that because `locate` uses a database that might not be updated in real-time, it might not find files that were created after the last database update unless `updatedb` is run manually.

### Practical Examples of Each Command

Let's look at some practical examples to better understand the usage of `find` and `locate`:

1. **Find all Python files modified in the last 2 days within the current directory:**
   ```bash
   find . -type f -name '*.py' -mtime -2
   ```
2. **Locate all the PDF files that include the word "invoice" in their names:**
   ```bash
   locate invoice | grep '.pdf$'
   ```

Continuing with our exploration of Linux, we now delve into one of its fundamental aspects: file permissions. Understanding and managing these permissions is crucial for securing your system and controlling access to files and directories.

## Understanding File Permissions

Linux file permissions determine who can read, write, and execute files and directories. There are three types of permissions and three categories of users for whom these permissions can be set.

### Basics of File Permissions

Each file or directory has associated permissions that dictate how it can be accessed and by whom. These permissions include:
- **Read (r):** Allows the content of the file to be read.
- **Write (w):** Permits the modification or deletion of the file.
- **Execute (x):** For files, it allows running the file as a program. For directories, it permits accessing files within the directory.

Permissions are set for three different categories of users:
- **Owner:** The user who created the file or directory.
- **Group:** Users who are part of a group that is assigned to the file.
- **Others:** All other users on the system.

### Permissions in Octal Format (Numeric)

Permissions in Linux can be viewed and modified using both symbolic (character) and numeric (octal) formats. The octal format is a three-digit number, with each digit representing a different category of users:
- The first digit represents permissions for the **owner**.
- The second digit is for the **group**.
- The third digit stands for **others**.

Each digit is a sum of:
- 4 for read (r),
- 2 for write (w),
- 1 for execute (x).

For example:
- **644** (`rw-r--r--`): Read and write for the owner, and read-only for group and others.
- **755** (`rwxr-xr-x`): Read, write, and execute for the owner; read and execute for group and others.

### Permissions in Character Format (Symbolic)

In symbolic notation, permissions are represented by a string of characters, for example, `rwxr-xr--`. Each triplet corresponds to the owner, group, and others, respectively.

- **rwx:** Read, write, and execute.
- **r-x:** Read and execute.
- **r--:** Read only.

### Changing Permissions with `chmod`

The `chmod` command is used to change the file permissions. Here's how you can use it:
- **Using Octal Notation:** To set the permissions of a file named `example.txt` to `rw-r--r--` (644):
  ```bash
  chmod 644 example.txt
  ```
- **Using Symbolic Notation:** To add execute permission for the owner:
  ```bash
  chmod u+x example.txt
  ```

### Examples of Setting Permissions

Here are some practical examples:
1. **Setting a file to be writable and readable by the group:**
   ```bash
   chmod g+rw filename
   ```
2. **Removing execute permissions for others:**
   ```bash
   chmod o-x filename
   ```
3. **Setting directory permissions to 755:**
   ```bash
   chmod 755 directoryname
   ```

These commands and examples illustrate the importance of carefully managing file permissions in Linux to protect system security and user data.

### Example Path Explanation

Consider the path `/home/john/documents/report.txt`:
   - `/` - Root directory.
   - `home` - A directory under root.
   - `john` - User's home directory.
   - `documents` - A directory within John's home.
   - `report.txt` - A file inside the documents directory.

This path illustrates the hierarchical structure of directories in Linux, showing how files are organized and accessed.

### Exercise Set for `pwd` (Print Working Directory)
**Exercise 1:** Check Your Current Directory

1. Open your terminal.
2. Type `pwd` and press Enter.
3. Note down the output. This shows your current directory path.

**Exercise 2:** Changing Directories and Verifying

1. Change to your home directory by typing `cd ~` and pressing Enter.
2. Use `pwd` to confirm that you are now in your home directory.
3. Record the output and compare it to the expected home directory path.

### Exercise Set for `cd` (Change Directory)
**Exercise 1:** Navigating to a Subdirectory

1. From your home directory, list all directories using `ls`.
2. Pick a subdirectory and navigate into it using `cd [subdirectory name]`.
3. Use `pwd` to ensure you have moved into the correct directory.

**Exercise 2:** Returning to the Previous Directory

1. From the current directory, use `cd ..` to go back to the parent directory.
2. Verify your current directory using `pwd`.
3. Navigate back to the initial directory using `cd -` and verify again with `pwd`.

### Exercise Set for `ls` (List Directory Contents)
**Exercise 1:** Listing All Files and Directories

1. In any directory, type `ls -a` to list all contents, including hidden files.
2. Observe the output and identify any hidden files (usually prefixed with a dot).

**Exercise 2:** Detailed List of Files

1. Use `ls -l` to list all files and directories with detailed information such as permissions, number of links, owner, group, size, and timestamp.
2. Note the file permissions of each file listed.

### Exercise Set for `mkdir` (Make Directory)
**Exercise 1:** Creating a Single Directory

1. Choose a location where you want to create a new directory.
2. Use `mkdir newfolder` to create a directory named `newfolder`.
3. Verify the creation by using `ls` and observing if `newfolder` appears in the output.

**Exercise 2:** Creating Multiple Directories

1. In your current directory, use `mkdir dir1 dir2 dir3` to create three directories simultaneously.
2. Verify their creation by listing the directory contents with `ls`.

### Exercise Set for `rmdir` (Remove Directory)
**Exercise 1:** Removing an Empty Directory

1. Create a temporary directory using `mkdir tempdir`.
2. Remove this directory by typing `rmdir tempdir`.
3. Confirm removal by listing the directory contents to ensure `tempdir` no longer exists.

**Exercise 2:** Attempting to Remove a Non-Empty Directory

1. Create a directory and add a file inside it using `mkdir testdir` and `touch testdir/testfile`.
2. Try removing the directory using `rmdir testdir` and observe the error message.
3. Remove the file with `rm testdir/testfile` and then remove the directory using `rmdir testdir`. Confirm the directory is removed.

### Exercise Set for `find`
**Exercise 1:** Finding Files by Name

1. In your home directory, use `find . -name "sample.txt"` to search for a file named `sample.txt`.
2. Observe and note down which directories contain the file named `sample.txt`.

**Exercise 2:** Finding Directories

1. Use `find / -type d -name "config"` to find all directories named `config` starting from the root directory.
2. Note the paths of all directories named `config`.

