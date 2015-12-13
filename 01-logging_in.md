---
layout: page
title: HPC-novice
subtitle: Logging in
minutes: 15
---
> ## Learning Objectives {.objectives}
>
> *   Explain logging in to a remote computer.
> *   Download putty for Windows and log in (for all OSes present)

How you log in to a remote system depends on what
kind of computer you are using.  We'll cover Windows, 
Linux and Mac.

Windows 
-------
- If you are logging into cowboy from a Windows machine, you will need to install a program called putty. You can download putty here:  [http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe)
- Once you have downloaded putty, you can place the file on your desktop and double click it to launch the program. 
- In the box labeled *Host Name*, type the hostname of the system you want to log in to: **cowboy.hpc.okstate.edu**.
- Check to make sure that the *Connection Type* is **ssh** and the *Port* number is **22**.
- To save your session for next time (so you don't have to retype each time) type a name into *Saved Sessions* and click *Save*. Next time you log in, all you will need to do is double click on the saved session name.
- Click *Open* to open a connection with Cowboy. You will be asked for your user name and password. **No characters will appear when you type in the password**. This is a security feature. Don't worry, just type the password you received when you set up your account and hit \<enter\>.
- You should now have a command prompt. *Prompt* is a unix term that means the words followed by the `$` sign. This tells you that the terminal is waiting (*prompt*ing) for you to enter a command. To log out, simply type `exit` or `logout` and hit \<enter\>.

Linux
-----
Launch a terminal, type the following and hit enter:

~~~ {.bash}
ssh username@cowboy.hpc.okstate.edu
~~~

In the above example, `username` is your user name. For example, if your user name was `monkey,` you would type:

~~~ {.bash}
ssh monkey@cowboy.hpc.okstate.edu
~~~

Macintosh
---------
Since the Macintosh OS is based off of Unix just like Linux, logging into Cowboy is very similar to logging in from a Linux computer:

-	Double click on the *Hard Drive* icon.
-	Double click on the *Applications* folder.
-	Double click on the *Utilities* folder.
-	Double click on *Terminal*.

Now that you have launched the terminal, follow the same directions as logging in with a Linux computer.

> ## The command prompt {.callout}
>
> In these lessons, the command prompt is shown as `$` and indicates that the terminal is waiting for you to type your next command.  In reality, your command prompt will have some text preceding the `$` which may include your username, the name of the computer, the directory you are in, and more depending on the way it is configured.

> ## Case sensitivity {.callout}
>
>  Everything in linux is case sensistive, including your username and password.  For example, `my_input_data.txt` is ***not*** the same as `My_Input_Data.txt`




Changing your Password
----------------------
The first time you log in, you should change your password from the default password assigned when your account was created to a more secure (and easier to remember) password of your choosing. Type the following and hit enter:

~~~ {.bash}
$ passwd
~~~

You should see the following text (for the purposes of this tutorial we will use the example user name monkey):

~~~ {.output}
Changing password for user monkey.
Current Password:
~~~

Type in your current password (currently the default password assigned to you) and hit \<enter\>. You will then be prompted to enter a new password twice. From now on, you will log into the system with this new password. Please choose a **STRONG** password.

Logging Out 
-----------

To log out just type:

~~~ {.bash}
$ exit
~~~
You can also use the key combination `Ctrl-D.`



> ## Login Nodes {.callout}
>
>When you log in, you are on a login node. Remember, an HPC system actually a network of many computers ("nodes") linked together by a high speed network so that they can communicate and can combine computing power in order to complete a task faster than any single computer.
>
>Login nodes are for logging in, working with files, and for submitting jobs. Always submit jobs to the scheduler, and never run a job from a login node. We will explain job submission more thoroughly later in this tutorial.




> ## Using the Mouse {.callout}
>
> When logged into like we have here, you are using a terminal so you mouse does not do anything. All commands are typed and interaction with the computer is text based. The one exception is that your mouse can be used to copy and paste. If you highlight any text in the terminal (putty only, use your usual copy and paste on Linux and Mac) with your mouse it is automatically copied. To paste it either right click (in putty) or click the middle button/scroll wheel of your mouse.

> ## Why Use a Terminal? {.callout} 
>
> So why use a terminal? Wouldn't it be easier if HPC systems had a graphical user interface (GUI) with buttons and a mouse like most modern personal computers? While there is a steep learning curve associated with using a terminal, terminal based computer systems are ideally suited for certain types of computing. Consider a research scientist who has data files containing the results of their research. Each run of the experiment contains data from that run and in the course of their research, the scientist must make a change to each one of the files. If there are only twenty data files then clicking on each file to open it and change it, while time consuming is doable. However, what does the scientist do for an experiment that has 200 runs, or even 2,000? Unless they employ a lot of graduate students, our poor researcher will not be able to complete their research in a timely manner. The terminal has a nice set of features that allows us to automate such tasks so that the computer does the work for us. We will talk more about these options later. Remember, while the terminal has a steep learning curve, it is an investment that pays itself back later by saving you time.

> ## Using more than one terminal at a time {.callout}
>
> Somtimes you will want to be able to edit files or do work in different locations in the file system at the same time.  Rather than repeatedly moving back and forth, you can open another terminal exactly as described above.

You're now ready to move on to [Submit first job](02-submit_first_job.html)



