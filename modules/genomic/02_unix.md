---
layout: module
title: "Command Line Interface Basics"
permalink: /modules/genomics/unix
nav_order: 2
parent: Genomic modules
grand_parent: Modules
---

## Table of contents

{: .no_toc .text-delta }

1. TOC
{:toc}

<!-- hidden notes 
Break it done simply
    the terminal is like when you open a file directory 

Install terminal

OS, terminal, shell
- keyboard-centric : talk about peripherial devices

terminal layout, filepaths

command, argument, stdin, stdout, stderr, pipe

editor, filetypes

flashy example first?

The power behind the command line is piping simple functions together to achieve complex workflows

awk | sort | uniq | tr

or maybe my bash script to parse the sra metadata would be more applicable.
-->

# Command Line Basics for Complete Beginners

By the end of this module, you will:

1. Build a mental model of your command line tools
2. Have some ability to use the terminal for basic computational tasks
3. Conceptualize the potential benefits of combining foundational computational skills with domain expertise

{:toc}

## Operating systems, Terminals, and Shells

Think of your computer like a giant file cabinet... Filled with files covered in text. To keep everything running smoothly without a giant mess, really smart people have built a few tools to keep everything working together.

### The Operating System

Think of this as: **The brain of the computer.**

The Operating System (OS) like Windows, macOS, or Linux is the main program that runs everything on your computer. When your computer turns on, the OS is what wakes up first.

> What it does: Your operating system decides which applications get to use the electricity, which gets to computational resources like memory, and where things are stored on the hard drive.
>
> Why we need it: Without the OS, the apps would fight over the tools.

### The Terminal

Think of this as: **A chat window where you talk to the computer.**

Most people talk to their computer by clicking on colorful buttons (the "User Interface"). But that way is limited by whoever decided what buttons should be available and exactly what those buttons do!

There is a secret way to talk to the computer using only words. That’s the Terminal.

> What it is: It’s just a window with a blinking cursor where you type text.
>
> What it does: It’s like a walkie-talkie or an intercom. It doesn't actually "do" the work; it just carries your voice (your typing) into the computer.

### The Shell

Think of this as: **A helpful translator for the terminal to communicate with the computer**

Our operating systems are very smart, but they speak a very complicated language of only 0s and 1s. The OS doesn't understand "Please make a new folder.", "Where am I?", or "What is in this file?". This is where the Shell comes in.

> What it does: The Shell sits inside the Terminal. It listens to the words you type and translates them into "Computer Speak" for the OS.
>
> How it works: If you type `pwd` in your Terminal, the Shell tells the OS, "Hey boss, the human wants to know where they are in the hard drive. Please tell me where they are and I'll let them know." 
> Or...
> If you type `mkdir "projects"` in the Terminal, the Shell tells the OS, "Hey boss, the human wants a new spot to store their projects. Please move some bits around to make that happen."

### How They Work Together

Imagine you want to start a new project after collecting some data:

1. You turn on your computer and see you OS starting up.

2. You open the Terminal application. Your terminal loads its default shell.

3. You type a commands like `ls`, `cd`, and `mkdir` into the Shell.

4. The Shell runs to the Operating System and says, "The human know where they are in the hard drive." and "Now they want to move to a new area of the hard drive." and "The human wants to make a new storage bin. Can you move some bits for that?"

5. The Operating System returns information on what directory content is available, moves you to the directory you wrote down, and then makes a new directory by the name you gave it.

In short: The Terminal is the phone, the Shell is the person on the other end translating, and the OS is the worker actually doing the heavy lifting!

### Examples software releases:

#### OS examples:

* macOS
* Windows
* Linux

#### Terminal examples:

* Terminal
* [Git Bash](https://git-scm.com/install/windows)
* Windows Terminal
* WezTerm
* [Kitty](https://sw.kovidgoyal.net/kitty/)
* [Warp](https://www.warp.dev/)

#### Shell examples

* `bash`
* `zsh`
* `powershell`
* [`fish`](https://fishshell.com/)

---

## Terminal anatomy: Embracing the digital you

Terminals may appear intimidating initially, but, as with everything, the more opportunities you have to experience something, the more comfortable things become. Below is an image of the terminal. From left to right, `colton@badger` is my username and computer (or `<username>@<computer>`. Next, we see a separator `:`. Followed by a filepath that shows the path to our current working directory the terminal is operating in on the computer, `~/projects/2026_summer_eeg_program`. The final character, `$`, is the prompt character where the commands may actually be typed into our terminal.

* `colton` → username
* `badger` → device name
* `~/projects/2026_summer_eeg_program` → current location (working directory)
* `$` → prompt (ready for the next command)

<img src="{{ '/assets/images/colt-terminal.png' | relative_url }}" alt="My terminal">

But! Any terminal or any shell can deviate from this layout. As we see below, my same terminal is now running the `fish` shell. From left to right, we first see the current working directory `2026_summer_eeg_program` and not the full path to this directory. The `fish` shell deviates further into various symbols that we may cover in more advanced topic discussions.

<img src="{{ '/assets/images/colt-fish.png' | relative_url }}" alt="My terminal with a fish shell">

At this point, you may have noticed that your mouse does not work within the terminal. You cannot click to move the flashing cursor. You are mostly limited to the keyboard as your primary peripherial device within the terminal. This is due to the history of the computer. Processing units and keyboards came before the monitor. Before monitor displays were available, flashing indicator lights and a continuous feed printer were the primary tools for "seeing" what you were doing on the computer.

To navigate the terminal:

* Move character by character: `Left Arrow` / `Right Arrow`
* Move word by word: `Alt + Left Arrow` / `Alt + Right Arrow`
* Jump to the beginning of the line: `Ctrl + A`
* Jump to the end of the line: `Ctrl + E`
* Clear the whole screen: `Ctrl + L`
* Cancel the current command line: `Ctrl + C`
* Kill the currently running process: `Ctrl + \`

### Basic Terminal Commands and Arguments: Doing things in your digital house

Commands are how we can execute processes. We can create, remove, edit files and directory structure withing our computers. More specific commands allow us to do domain specific things, but those commands require installation.

Here are some basic commands that are base unix and always available.

#### Show Current Working Directory

```bash
pwd
```

#### List Files

```bash
ls
```

{: .note}
> Most commands come with arguments that allow for commands to become a far more flexible tool. There are some commands that require arguments to execute.
>
> ```bash
> command argument
> ```
>
> Example:
>
> ```bash
> cd projects
> ```
>
> * command = `cd`
> * argument = `projects`

#### Create Folder

```bash
mkdir test
```

#### Change (Working) Directory

```bash
cd test
```

#### Create Empty File

```bash
touch testnotes.txt
```

#### Remove File

```bash
rm testnotes.txt
```

#### Go to Parent Directory

```bash
cd ..
```

{: .note}
> Arguments come in to different varieties in the terminal, `positional` and `keyword/flags`.
>
> All the previous examples were positional, but below we begin using flags with out unix commands.

#### Remove a Directory

```bash
rm -rf test
```

#### Clear the Terminal

```bash
clear
```

## Filepaths: Living in a digital house

**A thought exercise for you to consider:** If the terminal is your digital presence in the digital space of your computer, our computer is our digital house with different rooms that are directories.

In otherwords, our directories are the rooms of our digital house and the filepaths we use in our terminal are the paths we walk to go from room to room in our digital house.

<img src="{{ '/assets/images/floor-tree-plan.png' | relative_url }}" alt="apartment floor plan with file directory tree">

### Important Symbols

| Lead Symbol | Meaning        |
| ------ | ---------------- |
| `.`    | current directory   |
| `..`   | parent directory    |
| `~`    | home directory      |
| `/`    | root directory      |

These symbols allow for `relative paths` or the user of special symbols that are the same across every linux machine, but the value stored by that symbol unique to the computer.

Without these symbols we would always be limited to the `absolute path` for files!

* `relative path` example: `~/projects/`
* `absolute path` example: `/home/colton/projects/`

## Editors: Our tool box

A text editor lets you write documents, code, notes, or any file containing text. The editor is how we access the various applications we want to make edits to:

1. fix bugs
2. extend capabilities
3. remove capabilities
4. refactor for improvements or adjustments
5. simple edit the text in our documents

Common editors:

* Vi or Vim or NeoVim (my preference but has a notorious learning curve)
* Nano or Pico
* Visual Studio Code

Example:

First, make a new project directory and move into that directory.

```bash
mkdir eeg_examples && cd eeg_examples
```

> what just happened and why is there `&&` in our prompt!
>
> `&&` means run next command after completing prior command

Now create a note!

```bash
nano notes.txt
```

Copy the notes below into `notes.txt`.

```text
Copy these notes
---

The quick brown fox
Jumps over
the lazy dog

I need
This 
To reach
Ten lines of text...
```

To save, `Ctrl + O`

To exit, `Ctrl + X`

Next, copy the file we wrote into existing.

```bash
cp notes.txt notes_again.txt
```

Now, rename the file by moving it into a new name.

```bash
mv notes.txt notes_thrice.txt
```

Do you still have a `notes.txt` file?

```bash
mv notes_thrice.txt notes.txt
```

---

## File Types: This is our houses stuff!

Files usually end with extensions. These extensions are another standard convention that is set in place by humans to understand the differences in all our various files.

Examples:

| File         | Type                   |
| ------------ | ---------------------- |
| `notes.txt`  | text                   |
| `script.sh`  | shell script           |
| `app.exe`    | executable file        |
| `data.csv`   | spreadsheet-style data |
| `program.r`  | R program              |
| `program.py` | Python program         |
| `README.md`  | markdown document      |

## Standard Streams: The digital plumbing and electrical for our digital house

Our processes communicate using streams of information. These streams are called the **standard input (STDIN)**, **standard output (STDOUT)**, and **standard error (STDERR)**. Mostly by convention, these are treated like:

| Name   | Meaning            |
| ------ | ------------------ |
| stdin  | input to a program |
| stdout | normal output      |
| stderr | error messages     |

For example, using our keyboard we initiate the process encoded by `echo` which inputs `hello` and outputs `hello`.

```bash
echo hello
```

Output:

```text
hello
```

In the terminal, every command you run (process) is connected to three standard streams by default. Our process neither knows nor cares where these streams terminate.

You can think of them like plumbing and electrical for our digital house:

```text
keyboard ──► stdin ──► program ──► stdout ──► screen
                              └──► stderr ──► screen (errors)
```

---

### stdin (standard input)

This is how a program receives data.

By default, stdin comes from your keyboard, but it can also come from files or even other commands.

#### stdin from keyboard

Run the command:

```bash
cat
```

Now type:

```text
hello
```

Press Enter, and you’ll see:

```text
hello
hello
```

Here:

* your keyboard ──► stdin ──► `cat`

To exit:

* press `Ctrl + D` or `Ctrl + C`

Run the command below to find out why this occurs:

```bash
cat --help
```

---

#### stdin from a file

Instead of typing an excrutiatingly long document into your terminal, we can stream the contents of a file directly into stdin using the `<` (less than) symbol

```bash
cat < notes.txt
```

This means:

* stream contents of `file.txt`
* to feed it into `cat` as stdin
* `cat` then streams that content into stout!

---

#### stdin from another command?

What if when running a command like `ls` I need the stdout to display in a vertical list. When I run the command, I see:

```bash
colton@badger:/living-dining-kitchen$ ls
```

Output:

```text
bath  bedroom  closet  den  patio
```

Even when I try to use one of the command's arguments like `ls -l`

```bash
colton@badger:/living-dining-kitchen$ ls -l
```

And I get way more information than I want!

```text
total 20
drwxr-xr-x 2 root root 4096 May 20 14:23 bath
drwxr-xr-x 3 root root 4096 May 20 14:22 bedroom
drwxr-xr-x 2 root root 4096 May 20 14:23 closet
drwxr-xr-x 2 root root 4096 May 20 14:24 den
drwxr-xr-x 2 root root 4096 May 20 14:24 patio
```

We can `pipe` the stdout of one command to the stdin of the following command using `|`.

```bash
colton@badger:/living-dining-kitchen$ ls | cat
```

The output is not in a list!

```text
bath
bedroom
closet
den
patio
```

### stdout (standard output)

This is where normal program output goes.

#### Example

```bash
echo "hello world"
```

Output:

```text
hello world
```

That text is sent to **stdout**, which is displayed in your terminal.

---

#### Redirect stdout to a file

The `>` (greater than) symbol is used to direct the stdout steam into a file. This is like the `<` (less than) symbol is used to redirect the file contents to the stdin.

```bash
echo "hello world" > output.txt
```

Now:

* nothing prints to the screen
* output goes into `output.txt`

Check it:

```bash
cat output.txt
```

What happens when you run?

```bash
echo "goodbye" >> output.txt
```

---

#### Append instead of overwrite

```bash
echo "add another line" >> output.txt
```

* `>` overwrites!
* `>>` appends (or adds to the bottom of a list)!

---

### stderr (standard error)

This is where errors go. It is separate from stdout so you can handle errors differently, because you might want:

* normal output printed in the terminal or saved to a file
* errors still shown on screen or saved in a separate log file

If an error happens, it is still captured but we have ultimate control over where these streams end.

---

#### An error message

```bash
ls does_not_exist.txt
```

Output:

```text
ls: cannot access 'does_not_exist.txt': No such file or directory
```

That message goes to **stderr**, not stdout.

---

#### Redirecting stderr

Send errors to a file:

```bash
ls does_not_exist.txt 2> errors.log
```

```bash
cat errors.log
```

Now:

* stdout → screen
* stderr → `errors.log`

Guess how we can append to the error log?!

---

#### Redirect both stdout and stderr

```bash
command > output.txt 2>&1
```

Meaning:

* `>` sends stdout to file
* `2>&1` sends stderr to same place as stdout

Modern shorthand:

```bash
command &> output.txt
```

Example:

```bash
cat notes.txt > text_2.txt 2> error.log
cat text_2.txt
cat error.log 
cat no_such_text > text_2.txt 2> error.log
cat text_2.txt 
cat error.log 
```

```bash
history | tail -n 10
```

# Combine everything into genomics

Downloading a ecoli genome into a specific filepath and retaining the download log with `wget`

```bash
wget https://ftp.ncbi.nlm.nih.gov/genomes/all/GCA/000/005/845/GCA_000005845.2_ASM584v2/GCA_000005845.2_ASM584v2_genomic.fna.gz \
-O ecoli.fa.gz \
-o ecoli-download.log
```
> `wget` is a special case where stdout and stderr have flags!

or

```bash
curl https://ftp.ncbi.nlm.nih.gov/genomes/all/GCA/000/005/845/GCA_000005845.2_ASM584v2/GCA_000005845.2_ASM584v2_genomic.fna.gz -o ecoli-curl.fa.gz
```

It is important to inspect the files.

```bash
file ecoli-download.log
cat ecoli-download.log 
clear
file ecoli.fa.gz
cat ecoli.fa.gz
```

Streaming large files like genomes or even metagenomes through a pipe removes the generation of large intermediate files that would then need to be removed for diskspace.

```bash
gunzip -c ecoli.fa.gz 
gunzip -c ecoli.fa.gz | head
gunzip -c ecoli.fa.gz | grep >
gunzip -c ecoli.fa.gz | grep ">"
```

But what about a larger file?

```bash
wget ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR197/008/SRR1976948/SRR1976948_1.fastq.gz
```
> This will take ~10 minutes to download

or

```bash
curl ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR197/008/SRR1976948/SRR1976948_1.fastq.gz
```

```bash
gunzip -c SRR1976948_1.fastq.gz | head
```

```bash
gunzip -c SRR1976948_1.fastq.gz | grep "@SRR" | wc -l
```

## Creating your account & connecting to OnDemand

Create your account / adding yourself to **gmcoopgrp**

Connect to [Hippo](https://hippo.ucdavis.edu/clusters)

Choose 'farm'.

There should be an option to create an account, or request access to another group. Select 'gmcoopgrp', and remove the SSH Key option.
