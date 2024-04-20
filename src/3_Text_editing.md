Text Editing
============

- Part 3: Text Editing
  - Commands: echo, cat, less, nano, grep, touch, joe, shell functions
  - Naming files and directories
  - Editing files

### Exercise Set for `echo` (Display a Line of Text)
**Exercise 1:** Display Simple Text

1. Open your terminal.
2. Type `echo "Hello, Linux World!"` and press Enter.
3. Observe the text displayed on your terminal.

**Exercise 2:** Redirecting Echo to a File

1. In the terminal, type `echo "This is a test file content." > testfile.txt`.
2. Use `cat testfile.txt` to view the contents of the file and verify that the text has been written.

### Exercise Set for `cat` (Concatenate and Display Files)
**Exercise 1:** Viewing Contents of a File

1. Create a file using `echo "First line of text" > myfile.txt`.
2. Add a second line using `echo "Second line of text" >> myfile.txt`.
3. Use `cat myfile.txt` to display the contents of the file.

**Exercise 2:** Concatenating Multiple Files

1. Create another file using `echo "Another file content." > anotherfile.txt`.
2. Concatenate both files and view the output using `cat myfile.txt anotherfile.txt`.

### Exercise Set for `less` (View Content of a File Page by Page)
**Exercise 1:** View a Large File

1. Create a large file by typing `for i in {1..500}; do echo "Line $i" >> largefile.txt; done`.
2. Open the file using `less largefile.txt`.
3. Navigate through the file using the arrow keys and observe how `less` handles large file navigation.

**Exercise 2:** Search Within a File in `less`

1. While still in `less`, type `/Line 150` and press Enter to search for "Line 150".
2. Observe how `less` navigates directly to the line containing the search term.

### Exercise Set for `nano` (Basic Text Editor)
**Exercise 1:** Create and Edit a File with Nano

1. Open terminal and type `nano mytextfile.txt`.
2. In nano, type a few lines of text.
3. Use `CTRL+O` and `ENTER` to save the file, then `CTRL+X` to exit nano.

**Exercise 2:** Modify an Existing File

1. Reopen `mytextfile.txt` in nano.
2. Add additional text and use `CTRL+X`, then `Y` and `ENTER` to save changes and exit.

### Exercise Set for `grep` (Search Text Using Patterns)
**Exercise 1:** Basic Text Search

1. Use `grep "line" largefile.txt` to find all occurrences of "line" in the previously created large file.
2. Observe and record which lines contain the word.

**Exercise 2:** Case Insensitive Search

1. Use `grep -i "LINE" largefile.txt` to perform a case-insensitive search.
2. Compare the output with the previous case-sensitive search.

### Exercise Set for `touch` (Change File Timestamps/Create Files)
**Exercise 1:** Creating a New File

1. In the terminal, type `touch newfile.txt`.
2. Use `ls -l newfile.txt` to verify the creation date and time of the file.

**Exercise 2:** Updating the Timestamp of an Existing File

1. Wait a minute, then use `touch newfile.txt` again.
2. Check the timestamp again using `ls -l newfile.txt` to see the update.

### Exercise Set for `joe` (Joe's Own Editor)
**Exercise 1:** Editing in Joe

1. Open terminal and type `joe anothernewfile.txt`.
2. Type some text, then save with `CTRL+K X` and confirm saving when prompted.

**Exercise 2:** Searching in Joe

1. Reopen `anothernewfile.txt` in joe.
2. Press `CTRL+K W` and type a search term that is in the text, then `ENTER` to find it.

### Exercise Set for Shell Functions
**Exercise 1:** Create a Simple Function

1. Open your terminal.
2. Type the following to create a function named `greet`:
   ```bash
   greet() {
      echo "Welcome, $1!"
   }
   ```
3. Activate the function by typing `greet "User"` and observe the output.

**Exercise 2:** A More Complex Function

1. Define a function `list_files` that takes a directory name and lists its contents:
   ```bash
   list_files() {
      echo "Listing files in $1:"
      ls -l $1
   }
   ```
2. Call the function with a directory path, e.g., `list_files /home/user`.
