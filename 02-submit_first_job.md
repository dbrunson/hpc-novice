---
layout: page
title: HPC-novice
subtitle: Submit first job
minutes: 15
---
> ## Learning Objectives {.objectives}
>
> *   Submit the hello world example
> *   First exposure to some linux commands
> *   Explain concepts involved

The typical workflow on an HPC system involves the following steps:

* Login
* Transfer any files or data needed on the system (we'll get to this later)
* Prepare job submission script and submit the job
* Monitor job progress (if desired)
* Log out (and potentially wait for an email saying your job finished)

> ## Good citizenship {.callout}
>
>  HPC systems are usually shared among large groups of people. This is why it is important to make sure that you use the scheduler rather than running processes on the login nodes.  Low impact activities such as editing files, creating job scripts and submitting jobs are fine.  If you accidently start a process and need to stop it quickly you can use `Ctrl-C` to kill it. Some login nodes will automatically kill your process if it uses too many resources on the login nodes and you may get a strong request from your HPC provider to be more careful.

Doing these things in a linux terminal requires several (but not that many) commands to move files around, edit files and work with the scheduler.

In this lesson, we walk through an entire example explaining as we go.  In order to have our example job finish quickly, we'll submit a prepared script and discuss its contents while the job runs.

To get started, log in to your HPC system.  You should have a terminal window open waiting for your input.

> ## A few linux commands {.callout}
> 
> Linux commands are typically lowercase cryptic abbreviations. The `$` represents the command prompt waiting for you to type. After typing the command, press the enter key.
>
> `$ whoami`  -- your username
>
> `$ pwd`     -- your current directory/folder (print working directory)
>
> `$ ls`      -- list the contents of your current directory


Next, let's create a new directory (also called folders) for this lesson material. The name of the folder is up to you, but you'll want to remember it.

~~~ {.bash}
$ mkdir submit_lesson
~~~

We can list the contents of our current directory with the `ls` command (you may have other things in your directory, but make sure the new directory we just created is there:

~~~{.bash}
$ ls
~~~

~~~{.output}
submit_lesson
~~~


Next, we change into the new directory with the `cd` command:

~~~{.bash}
$ cd submit_lesson
~~~

>## TAB auto-complete {.callout}
>
> The terminal has a wonderful feature to save you from making typos.  After you start to type `submit_lesson`, say after the `su`, press the TAB key. It will complete the name of the directory unless you have some other directory that also starts with `su`.  In that case, you can add press TAB again to see the possibilities, then add more letters so that your choice is clear.


Next, we'll download the example submission files. Don't worry much about these commands yet.  `wget` is a tool to download files from the internet and `tar` is a tool much like `unzip` that unpacks a collection of files. To facilitate copying and pasting the url, here is the link to `examples.tar` [https://github.com/dbrunson/hpc-novice/raw/gh-pages/examples.tar](https://github.com/dbrunson/hpc-novice/raw/gh-pages/examples.tar)  (Right-click on the link and choose 'copy link location' or something similar.

~~~{.bash}
$ wget  https://github.com/dbrunson/hpc-novice/raw/gh-pages/examples.tar
~~~

The `wget` command will have many lines of output showing its progress. When you get a command prompt `$` back, use `tar` as below to extract the files:

~~~{.bash}
$ tar xvf examples.tar
~~~

Let's check to see if that worked by using `ls -F`.  The `-F` is a 'flag' or command line option to the `ls` command and it causes subdirectories to have a `/` at the end of their name.

~~~{.bash}
$ ls -F
~~~
~~~{.output}
examples/  examples.tar
~~~

Let's navigate into the `examples` subdirectory and see what's there:

~~~{.bash}
$ cd examples
$ ls
~~~
~~~{.output}
helloworld.pbs  helloworld.sh
~~~

