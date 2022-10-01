# How to Log Into a Course-Specific Account on **ien6**:


## Step 1
![s1](step1.PNG)

- Head to Visual Studio Code's website to download and install as their instructions show. These steps vary depending on your operating system.

## Step 2
![s2](step2.PNG)

- With VSCode now installed, open a terminal using CTRL or Command +, (Depending on Computer,) or go to terminal page in the upper left hand corner and select new terminal.

## Step 3
![s3](step3.PNG)

* Now that you're in a terminal, type "SSH" followed by "cs15lfa22(your class-specific name)@ieng6.ucsd.edu" to make first contact. After prompting for a password, which you should've previously set up for this class-specific account, you should now have access to the remote device.

## Step 4
![s4](step4.PNG)

* There's many commands available, but here's a few being run as an example.

## Step 5
![s5p1](step51.PNG)

* Now let's test moving a file over. Start by creating a new java file called WhereAmI.java. Then, run "scp WhereAmI.java cs15lfa22(class-specific name)@ieng6.ucsd.edu:~/" in the terminal from the directory where you made the file for it to be copied to the remote machine. If the transfer was successful after inputting your password, you should see information on it's progress. Now see if the file transfered by running ls and running the program with:

javac WhereAmI.java

java WhereAmI

* The following should be the result:

![s5p2](step52.PNG)

* The program has successfully copied over and is running on the remote machine, which is why it gives information on itself rather than ourselves, (the client.)

## Step 6

* We can continue to use the terminal like this, but it's slow. To create a key to automatically let our client in without a password, first follow the steps below, replacing "jz" and your file directory with your approximate information:

![s6p1](step61.PNG)

* Now log into the terminal, and create a new directory called .ssh using mkdir. This is what will save what the client generated. (I couldn't get a screenshot to show this action as I had already made the directory before and got a "directory already exists" error.)

* Lastly, run the following command to send the key into the server:

![s6p2](step62.PNG)

* If this process worked correctly, you should now not be prompted for a password when accessing the server, as can be seen in this example:

![s6p3](step63.PNG)

## Step 7

* Last but not least, now that we've let our computer more easily communicate without the barriers of a password, we can run mutiple tasks at the same time using quotations. for example:

![s7](step7.PNG)



That's it! Thanks for looking!