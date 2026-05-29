---
layout: module
title: "High Performance Computing Tour"
permalink: /modules/genomics/hpc
nav_order: 5
parent: Genomic modules
grand_parent: Modules
---

<!-- hidden notes 
I am giving demos and now you can be vaguly (know the terminology learn what to search how to ask for help and )

What are three things you found confusing about the HPC and what is your review of the article
-->

## Table of contents

{: .no_toc .text-delta }

1. TOC
{:toc}

## Remote computing and HPC

Material credited to Dr. C. Titus Brown!

### Create you UC Davis HPC account

1. Connect to [HIPPO](https://hippo.ucdavis.edu/clusters)
2. Choose `farm`.
3. There should be an option to create an account, or request access to another group.
4. Select your research group, and remove the SSH Key option.
    > For our purposes, we were going to use the `gmcoopgrp`.

### Digression: Why HPC, and why OnDemand, and why farm?

Why HPC?

- big disks (100s of TB of disk space)
- bigger compute (10s-100s of CPUs)
- large memory options (10s-100s of GBs of RAM)
- many compute jobs! (that aren't running on your laptop)
- shared workspace (sharing large files and results)
- Linux machine (so can run a wide range of software)
- a machine with a really fast network connection

{: .note}
> Today, we'll focus on `high priority` and `interactive computing`, but batch computing is a thing we can talk about! We can talk about these approaches in an advanced topic session.

### Connecting to OnDemand; the Files tab.

Connect to the HPC OnDemand system on farm at [OnDemand](https://ondemand.farm.hpc.ucdavis.edu/).

Visit the Files tab.

{: .note}
> (If this is a new account for you, you won't see much!)
> note that you can't see system level files or group disks through the Files tab, unless you use a symbolic link ("symlink") - we'll talk about that below.

Create a working directory for today

Go to the Files tab, select `Home Directory`, and click `New Directory`. Name it "2026-eeg-genomics". This will be our "working folder" for today's workshop.

Why a working folder?

> It's nice to group everything together, and it will help us troubleshoot problems!

Why this name?

> - date stamped
> - will cluster with like in the same order
> - unlikely to "collide" with any other names you choose

## Using RStudio on the farm HPC

Go to `Interactive Apps` and start up an `RStudio Server` app, with the following parameters:

- Slurm account: use your grp
- Partition: high2 partition
- request 2 CPUs
- request 5 GB RAM
- request 8 hour reservation

Leave everything else (conda environment, modules, directory) blank!

Now click `request`.

(Note that settings will stick from the last time you ran RStudio! That's why your defaults may look different from mine!)

## Digression: how HPCs work

> The office building analogy, hat tip to Christy Grettenberger.

Imagine you need to recruit some workers for a temporary gig. You buy into a co-working space that's got an office building.

> You can request **one or more rooms of various sizes (RAM/memory)**; there is an upper limit, though.
> You can ask to fill the rooms with a **number of desks for workers to use (CPUs, or threads)**.
> You have **access to a small personal storage unit and some really large storage units** that you bought & are shared with others (disk space).

Everyone enters through the front lobby - that's the head node (except for people using OnDemand, who have a special entrance!)

Behind the scenes, the co-working space is rearranging the walls to make the rooms the size you need. (Subject to the upper limit, of course.)

You can't request more rooms than are free at any given time.

When your reservation runs out, you will be summarily evicted!

You can request rooms at some point in the future, and assign specific work to start in them when they become available!

Each "account" that you're under has priority access to a certain total amount of space in the rooms, and a certain number of desks, along with sole access to some storage units. You share access to those resources with everyone else on that account.

You can get short-term access to other people's resources, if they are not using them. (24 hours on low priority queue, I think - on farm.)

A question we will tackle later: how do you know how big a room you need (how much memory), and how many desks (CPUs) you should use?

<img src="{{ '/assets/images/office-floorplan.png' | relative_url }}" alt="Office floor plan" width="400">

## Useful HPC commands

To connect to a remote computer through the terminal we securely log into them through the `ssh` command.

```bash
ssh -i <path-to-your-private-key> <username>@farm.cse.ucdavis.edu
```

To make the use of `ssh` (the "secure shell") simpler, create and edit a `config` file in the `.ssh` directory on your local computer.

Input:

```bash
nano ~/.ssh/config
```

Output:

```bash
Host farm
   HostName farm.hpc.ucdavis.edu
   User <username>
   IdentityFile <path-to-your-private-key>
```

Now, logging in to a remote location is easier to type and remember.

```bash
ssh farm
```

The following commands are for the `Slurm` cluster managment and job scheduler used in UC Davis' HPC.

```bash
sinfo
sbatch
srun
squeue
scancel
```
> [Details for these commands are here!](https://slurm.schedmd.com/quickstart.html)

Instead of installing software on your user partition and taking up precious memory, the HPC has pre-installed popular software. You can access this software with the `module` command.

```bash
module avail
module avail | grep 'r'
module avail | grep 'trimmomatic'
module load trimmomatic
```
