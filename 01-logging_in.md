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
- If you are logging into cowboy from a Windows machine, you will need to install a program called putty. You can download putty [here][putty].

how do links work?  http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe

- Once you have downloaded putty, you can place the file on your desktop and double click it to launch the program. 
- In the box labeled *Host Name*, type the hostname of the system you want to log in to: **cowboy.hpc.okstate.edu**.
- Check to make sure that the *Connection Type* is **ssh** and the *Port* number is **22**.
- To save your session for next time (so you don't have to retype each time) type a name into *Saved Sessions* and click *Save*. Next time you log in, all you will need to do is double click on the saved session name.
- Click *Open* to open a connection with Cowboy. You will be asked for your user name and password. **No characters will appear when you type in the password**. This is a security feature. Don't worry, just type the password you received when you set up your account and hit \<enter\>.
- You should now have a command prompt. *Prompt* is a unix term that means the words followed by the `$` sign. This tells you that the terminal is waiting (*prompt*ing) for you to enter a command. To log out, simply type `exit` or `logout` and hit \<enter\>.

[putty]: http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe


