Navigating the file system
==========================

- Part 2: Navigating the File System
  - Commands: pwd, cd, ls, mkdir, rmdir, find
  - Parts of a path (root, system directory)
  - Searching for files
  - File permissions

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

