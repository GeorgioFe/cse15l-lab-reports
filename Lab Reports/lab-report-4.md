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

