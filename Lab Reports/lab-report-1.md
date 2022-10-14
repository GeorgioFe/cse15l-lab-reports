# Lab Report 1 - Remote Access and Filesystem

&emsp; In this lab we will set our computer up for remote access to the CSE lab computers (or log into them directly) and practice with commands that work with the filesystem.

---

## Step 1: Installing Visual Studio Code
&emsp; First, we should go to the [Visual Studio Code website](https://code.visualstudio.com/) to download it on our computer. Below is a screenshot of how VSC should look like:

![Image](../Screenshots/Lab%20Report%201/lab1-screenshot-1.png)

---

## Step 2: Remotely Connecting
&emsp; Many courses in CSE use course-specific accounts. These are similar to accounts we might get on other systems at other institutions. We’ll see how to use VScode/terminal to connect to a remote computer over the Internet to do work there.

&emsp; We open our terminal and connect to the server computer. It is most likely that for the fist time, there will be a prompt. We type "yes" to that message and type our password in. After connection is successful, we should see something like this:

![Image](../Screenshots/Lab%20Report%201/lab1-screenshot-2.png)
&emsp; *It is important to note that during the lab session, the CSE 15L specific accounts didn't work, so we had to connect to our general UCSD accounts.*

&emsp; We call our computer the *client* and the computer that we connected to the *server*.

---

## Step 3: Trying Some Commands
&emsp; Trying Commands in local computer (client).

![Image](../Screenshots/Lab%20Report%201/lab1-screenshot-3.png)
&emsp; *We tried running a couple of commands on our personal computer, such as clear, cd, pwd, ls, and cat. We printed the working directory at first just to know where we are, I then accessed my personal projects repository through different commands (ls, cd) and printed one of the files (cat). I finally went all the way back to the home directory with ~.*

&emsp; Trying Commands in server computer.

![Image](../Screenshots/Lab%20Report%201/lab1-screenshot-4.png)
&emsp; *Prints out hello.txt, which is on the server computer.*

---

## Step 4: Moving Files with *scp*
&emsp; The command to copy files from our local computer to the server computer is *scp*. This command will be run on the client (not the server). We created and ran a file called WhereAmI.java to demonstrate this.

![Image](../Screenshots/Lab%20Report%201/lab1-screenshot-5.png)
&emsp; *As we see in the picture, we first tried running the file on the client and it printed out info for that device. We then copied the file into the server computer with the scp command and when we connected to the server and ran the program from there, we see that the program reflected on that and printed out info about the server.*

---

## Step 5: Setting an SSH Key
&emsp; Every time we log in or run scp, we have to type our password. This is frustrating and time consuming. A great solution to this is to create an *ssh key*. Below is a screenshot with all the steps highlighted to complete this process.

![Image](../Screenshots/Lab%20Report%201/lab1-screenshot-7.png)
&emsp; *Step 1: Generating the ssh key with ssh-keygen, and choosing the directory in which the key is stored.*

&emsp; *Step 2: Connecting to the server computer, creating a new directory called ssh, and exiting back to the client.*

&emsp; *Step 3: Copying the public key into the new directory that we created on the server computer.*

&emsp; After these steps, connecting to this server will not require a password each time.

---

## Step 6: Optimzing Remote Running
&emsp; There are a lot of ways to make our experience with the command line more pleasant, more effecient, and more optimized. For example if we want to quickly do something on the server computer, we can add whatever command we want at the end of the *ssh* command in quotes so this way the command will connect with the server computer, do whatever we asked it to do and exit the server computer automatically. We can also type in several commands on the same line seperated by semicolons and the computer will execute all the commands automatically.

&emsp; Below is an example of how I used some of the techniques describes above to make my work faster, and in fact, the time it took me to edit and run the java program with these new techniques was about 60% faster compared to before (without optimizing workflow).

![Image](../Screenshots/Lab%20Report%201/lab1-screenshot-8.png)







