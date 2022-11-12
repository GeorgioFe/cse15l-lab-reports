# Lab Report 4: Vim

## Part I: Changing the name of the `start` parameter and its uses to `base` using vim

### &emsp; Vim keystrokes:
- `vim DocSearchServer.java`
- `/start <Enter> c w base <Esp> n . n . <Shift> ; w q <Enter>`

&emsp;&emsp; After entering vim, we completed the required task in 23 keystrokes.

### &emsp; Steps:
1. After entering vim, the cursor will highlight the first character in the file.

![image](../Screenshots/Lab%20Report%204/lab4-screenshot-1.png)

2. We type `/start<Enter>` to make the cursor highlight the first occurance of the word `start`.

![image](../Screenshots/Lab%20Report%204/lab4-screenshot-2.png)

3. We then type `cw` to delete the selected word (`start' in this case) and go into insert mode.

![image](../Screenshots/Lab%20Report%204/lab4-screenshot-3.png)

4. We proceed with typing `base<Esc>` to replace the deleted word with `base` and go to normal mode.

![image](../Screenshots/Lab%20Report%204/lab4-screenshot-4.png)

5. We repeat this process by pressing `n` which will make the cursor highlight the next occurance of the word `start` and press `.` which will do the exact same steps we did at the first occurance.

![image](../Screenshots/Lab%20Report%204/lab4-screenshot-5.png)
![image](../Screenshots/Lab%20Report%204/lab4-screenshot-6.png)

6. After doing this for all occurances, we finally type `<Shift>;wq<Enter>` to save and quit vim.

---

## Part II: Vim vs. `scp`

### &emsp; `scp` method:

&emsp; The thing that took most of the time with this method was the `scp` and `ssh` commands. Other than that I quickly edited the file in vscode.
Overall the time it took with this method was 39.82 seconds.

### &emsp; Vim method:

&emsp; This method was fairly easy and quick since we already thought about the quickest way to change a word, so it seemed much easier and faster. I didn't have any specific difficulties with it.
Overall the time it took with this method was 35.93 seconds.

For a remotely run project, I would definitely prefer the vim method as I can directly edit what I need on the actual server. Additionally, using vim would be much quicker as I get used to it.

If the project has a major change in terms of code, then I would definitely prefer doing it on vscode with much clearer graphical interface, even if the `scp` is going to take a little more time.