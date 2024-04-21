### Exercises for `mv` (Move and Rename Files)
**Exercise 1: Renaming Files with Patterns**
**Objective:** Use the `mv` command in a scripted loop to rename multiple files following a pattern.
**Steps:**

1. Create several files for testing: `touch testfile1.txt testfile2.txt testfile3.txt`.
2. Write a simple loop to rename these files from `.txt` to `.md`: 
   ```bash
   for file in *.txt; do
     mv "$file" "${file%.txt}.md"
   done
   ```
3. Use `ls` to verify that all files now have the `.md` extension.

**Exercise 2: Organizing Files by Type**
**Objective:** Move files of different types into designated directories.
**Steps:**

1. Create a few test files: `touch file1.docx file2.pdf file3.docx file4.pdf`.
2. Create directories for each file type: `mkdir DOCX PDF`.
3. Write a script to move files into their respective directories based on the extension:
   ```bash
   mv *.docx DOCX/
   mv *.pdf PDF/
   ```
4. Verify by listing the contents of `DOCX` and `PDF` directories.

### Exercises for `sed` (Stream Editor)
**Exercise 1: Replacing Text in a File**
**Objective:** Use `sed` to find and replace text in a file.
**Steps:**

1. Create a file named `sample.txt` and add some content: `echo "This is a test file. Testing, one, two, three." > sample.txt`.
2. Use `sed` to replace "test" with "demo": `sed 's/test/demo/g' sample.txt`.
3. Display the output using `cat sample.txt` to verify the replacement.

**Exercise 2: Delete Lines Containing a Specific Pattern**
**Objective:** Use `sed` to delete lines that contain a certain word.
**Steps:**

1. Add more lines to `sample.txt`: `echo "Remove this line test." >> sample.txt`.
2. Use `sed` to delete lines containing the word "Remove": `sed '/Remove/d' sample.txt`.
3. Display the updated content to verify that the line has been removed.

### Exercises for `awk` (Pattern Scanning and Processing Language)
**Exercise 1: Print Specific Fields from a Text File**
**Objective:** Use `awk` to print specific fields from a delimited file.
**Steps:**

1. Create a CSV file: `echo -e "Name,Age,Job\nAlice,30,Doctor\nBob,25,Engineer" > people.csv`.
2. Use `awk` to print only the names and jobs: `awk -F',' '{print $1, $3}' people.csv`.
3. Check the output to ensure it lists only the names and their jobs.

**Exercise 2: Summing a Column of Numbers**
**Objective:** Use `awk` to sum the values of a specific column.
**Steps:**

1. Add a column for salary to `people.csv`: `echo -e "Name,Age,Job,Salary\nAlice,30,Doctor,50000\nBob,25,Engineer,48000" > people.csv`.
2. Use `awk` to sum the salary column: `awk -F',' 'BEGIN {sum=0} {sum += $4} END {print "Total Salary:", sum}' people.csv`.
3. Verify the output shows the correct total salary.

### Exercises for `grep` with Regex
**Exercise 1: Finding Lines That Start With a Capital Letter**
**Objective:** Use `grep` with a regex pattern to find lines starting with a capital letter.
**Steps:**

1. Use `grep` on `people.csv` to find lines starting with a capital letter: `grep '^[A-Z]' people.csv`.
2. Check the output to ensure it includes all lines except the header.

**Exercise 2: Finding Entries With a Specific Age**
**Objective:** Use `grep` with regex to find all entries where the age is 25.
**Steps:**

1. Use `grep` to find entries with the age 25 in `people.csv`: `grep ',25,' people.csv`.
2. Verify the output to ensure only entries with the age 25 are displayed.
