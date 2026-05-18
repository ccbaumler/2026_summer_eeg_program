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

---

## what are filepaths

filepaths are the house

They are addressing filepath is the path you walk in your home (local) or workplace (remote / cloud)

url - save as above but what is it like? A strip mall?

## Learning to code

Reading documentation is the gold standard - look up reddit post here

Reading the code and construction mneumonic devices to remember them - read through some function names

Ask GenAI to show you how to use the code and explain the operations - Create small use examples of the code (vingettes)
