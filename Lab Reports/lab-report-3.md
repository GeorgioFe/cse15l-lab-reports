# Lab Report 3 - Commands

&emsp; For this lab we chose the command <code>grep</code> to demonstrate how it works with several options.

&emsp; <code>grep</code> searches any given input files, selecting lines that match one or more patterns. By default, a pattern matches an input line if the regular expression (RE) in the pattern matches the input line without its trailing newline. An empty expression matches every line. Each input line that matches at least one of the patterns is written to the standard output.

&emsp; The 3 options that we are going to demonstrate are: <code>-c, -l, -i</code>

---

## 1. <code>-c</code>

&emsp; Only a count of selected lines is written to standard output.

### &emsp; Example 1:

![image](../Screenshots/Lab%20Report%203/lab3-screenshot-1.png)
&emsp; *Here, the <code>grep</code> command is looking for the pattern "United" in <code>technical/911report/chapter-1.txt</code> and printing out the number of lines where "United" is found.*


### &emsp; Example 2:

![image](../Screenshots/Lab%20Report%203/lab3-screenshot-2.png)
&emsp; *Here, we used the <code>grep</code> command with several files to see which of the files in <code>technical/911report/</code> contain the most lines with the pattern "Bin Ladin".*

### &emsp; Example 3:

![image](../Screenshots/Lab%20Report%203/lab3-screenshot-3.png)
&emsp; *Here, similar to example 2, we used the <code>grep</code> command with several files to see which of the files in <code>technical/911report/</code> contain the most lines with the pattern "CIA".*

### &emsp; Use Case:

The <code>-c</code> option can be used to visualize the files that contain the most amount of the given pattern. This can help us filtering out a list of long files.

---

## 2. <code>-l</code>

&emsp; Only the names of files containing selected lines are written to standard output. <code>grep</code> will only search a file until a match has been found, making searches potentially less expensive. Pathnames are listed once per file searched.

### &emsp; Example 1:

![image](../Screenshots/Lab%20Report%203/lab3-screenshot-4.png)
&emsp; *Here, the <code>grep</code> command is looking for the pattern "2002" in <code>technical/biomed/</code> and printing out the name of the files in which "2002" is found.*


### &emsp; Example 2:

![image](../Screenshots/Lab%20Report%203/lab3-screenshot-5.png)
&emsp; *Here, similar to example 1, the <code>grep</code> command is looking for the pattern "cancer" in <code>technical/biomed/</code> and printing out the name of the files in which "cancer" is found.*

### &emsp; Example 3:

![image](../Screenshots/Lab%20Report%203/lab3-screenshot-6.png)
&emsp; *Here, we used the <code>grep</code> command with several files to see which of the files in <code>technical/911report/</code> contain the pattern "atta".*

### &emsp; Use Case:

The <code>-l</code> option can be used as a search engine for files. Instead of printing out the lines where the pattern was found, it prints out the name of the files in which that pattern was found at least once.

---

## 3. <code>-i</code>

&emsp; Perform case insensitive matching. By default, <code>grep</code> is case sensitive.

### &emsp; Example 1:

![image](../Screenshots/Lab%20Report%203/lab3-screenshot-7.png)
&emsp; *Here, the <code>grep</code> command is looking for the pattern "bin ladin" in <code>technical/911report/</code> and printing out the number of lines in which "bin ladin" is found. This is doing essentially the same thing as our very first example for <code>-c</code>, however if we look carefully in the number of lines we see that it is more accurate with <code>-i</code> since it's case insensitive.*


### &emsp; Example 2:

![image](../Screenshots/Lab%20Report%203/lab3-screenshot-8.png)
&emsp; *Here, similar to example 1, the <code>grep</code> command is looking for the pattern "cia" in <code>technical/911report/</code> and printing out the number of lines in which "cia" is found. We notice that the numbers are different from the example we did above without <code>-i</code>. This further proves that <code>-i</code> is essential when using <code>grep</code> as a search tool.*

### &emsp; Example 3:

![image](../Screenshots/Lab%20Report%203/lab3-screenshot-9.png)
&emsp; *Here, we knew that "JSTOR" is only written all uppercase, so we tried to search for "jstor" lowercase and indeed we found the correct file.*

### &emsp; Use Case:

The <code>-i</code> option is essential for the <code>grep</code> command because when searching for something, we usually don't care about case sensitivity, and <code>-i</code> does exactly that. It ensures that the given pattern is searched for regardless of upper or lower case. In my opinion, <code>grep</code> should be case insensitive by default.