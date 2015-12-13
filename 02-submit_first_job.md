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

> ## A note on schedulers{.callout}
>
> There are several schedulers in use on different HPC systems, but they all are fundamentally the same.  We'll go over this in more detail later, but they all will require you to request walltime, the number of nodes, and a few other things followed by the commands to run your job. The most popular schedulers are Slurm, Grid Engine, and Torque/PBS. 


Since a scheduled job make take some time to complete, we'll go ahead and submit this hello world job now so it can be working while we learn about the files.

~~~{.bash}
$ qsub helloworld.pbs
~~~

The output from this command will include your **job id number**.

The file `helloworld.pbs` is called a **submission script**.

> ## On filenames{.callout}
>
>  Linux does not care about file extensions. (In Windows, for example. the extions `.exe` signifies an executible file.)  In Linux, it is good practice to use meaningful filenames to make your job of reading them and remembering what they are easier.  Here we use, by convention or convenience, the extension `.pbs` for a PBS submission script and `.sh` for a bash script. Also remember that filenames are case sensitive.

> ## spaces{.callout}
>
> You'll thank yourself later if you never use spaces in filenames or directory names.  The underscore is a great substitute.


Let's look at the jobs running on the cluster.  (Cluster is another word for HPC system.)

~~~{.bash}
$ showq
~~~


***NOTE:***   The `showq -u` and `qpeek` commands are not much use for this extremely short hello world example.  If you do a longer example later, postpone these unil then.  

If you just want to see your jobs (if any):

~~~{.bash}
$ showq -u yourusername
~~~

If you have a long job running (which we don't) you can check on the output with `qpeek`, but you'll need to know your job id number.  If you forgot, use `showq -u yourusername` to see it.  Suppose your job id number is `412343`, just type:

~~~{.bash}
$ qpeek 412343
~~~




Let's take a look at the contents of the submission script `helloworld.pbs`. The three most common ways to do this are with one of these commands: `cat`, `more`,and `less`.  You could also open it in a text editor, such as `nano`, `vim`, or `emacs.`


~~~{.bash}
$ cat helloworld.pbs
~~~

~~~{.output}
#!/bin/bash

# This is a comment that is just for humans to read
# Lines starting with #PBS are instructions to the scheduler

# Select the queue you want:
#PBS -q express

# Request the number of nodes and the number of
# processors per node
#PBS -l nodes=1:ppn=1

# Request the maximum time that your job could possibly need
#PBS -l walltime=10:00

#  This line puts all the output that would have gone to the screen
#  into a single file.  Some schedulers do this by default.
#PBS -j oe

#  This makes sure your job starts in the same directory as
#  where you submitted the job.
cd $PBS_O_WORKDIR

# This is the command to run a job
./helloworld.sh
~~~

