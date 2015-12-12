---
layout: page
title: HPC-novice
subtitle: submit first job
minutes: 15
---
> ## Learning Objectives {.objectives}
>
> *   Submit the hello world example 
> *   Explain concepts involved

The typical workflow on an HPC system involves the following steps:
* Login
* Transfer any files or data needed on the system (we'll get to this later)
* Prepare job submission script and submit the job
* Monitor job progress (if desired)
* Log out (and potentially wait for an email saying your job finished)

Doing these things in a linux terminal requires several (but not that many) commands to move files around, edit files and work with the scheduler.

In this lesson, we walk through an entire example explaining as we go.  In order to have our example job finish quickly, we'll submit a prepared script and discuss its contents while the job runs.

To get started, log in to your HPC system.  You should have a terminal window open waiting for your input.


Next, we'll download the example submission files:
   wget --no-check-certificate https://github.com/dbrunson/hpc-novice/raw/gh-pages/examples.tar

And extract the files:
   tar xvf examples.tar


