---
layout: module
title: "Introduction to Computation"
permalink: /modules/genomics/intro
nav_order: 1
parent: Genomic modules
grand_parent: Modules
---

## Table of contents

{: .no_toc .text-delta }

1. TOC
{:toc}

<!-- hidden notes 
Not computer 101 but programming 101

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

# A Simple Introduction to Computation

By the end of this module, you will:

1. Understand the structure and goals of this lecture series
2. Install and open a terminal on our local computer
3. Build a mental model of how programming works within a computational system

{:toc}

## Programming and Coding

In the space of computational tool usage, you may hear `programming` and `coding` used interchangably. However, these words are not synonyms!

Coding: Writing the algorithm and instructional code in a programming language.

Programming: Planning the design, build, and maintenance of software.

For example, I need to calculate the total price expended for various prices and quantities. The most simple, linear flow software we could design would:

- **Pseudo-code**:
1. Set the price and quantity
2. Calculate the total cost for price by quantity
3. Output the total for the end user

{% tabs coding %}

{% tab coding bash %}

```bash
price=3
quantity=10
total=$(( $price * $quantity ))
echo $total
```

{: note }
> Notice:
>
> - no spaces around `=`
> - `$` used to access variable
> - `$(())` used for arithmetic operations
> - Float arithmetic not allowed; only integer arithmetic allowed!

{% endtab %}

{% tab coding R %}

```R
price <- 2.99
quantity <- 10
total = price * quantity
print(total)
```

{: note }
> Notice:
>
> - Variables assigned with `<-`
> - Spaces around assignment operator
> - Arithmetic operations simplified
> - Float arithmetic allowed!

{% endtab %}

{% tab coding python %}

```python
price = 2.99
quantity = 10
total = price * quantity
print(total)
```

{: note }
> Notice:
>
> - Variables assigned with `=`
> - Spaces around assignment operator
> - Arithmetic operations simplified
> - Float arithmetic allowed!

{% endtab %}

{% endtabs %}

These modules will focus more on building your fundamental coding skills first. Lots of these skills are intertwined and while I may not advertise the programmatic skills we cover, we will cover some fundamental programming. As your confidence increases, we may delve into details in programming, if there is both time and interest!

... But, this does not explain how our code is interacting with the physical computer in front of us.

---

## Binary: the computer’s tiny language

At the deepest level, computers only understand two states:

- ON
- OFF

We write those as:

- `1`
- `0`

That’s called **binary**. Binary is special. It is the ***simplest*** numerical system possible and the "*simplest language*" in the world.

For example:

```text
10110011
```

Each digit in the example is known as a `bit`. To humans, this either looks very large number (~10 million) or like a series of 1s and 0s without context. To the CPU, it might mean:

> “Add these numbers”
> or
> “Move this data into memory”

That is because CPUs are incredibly fast machines that reads long streams of `1`s and `0`s and follow their instructions. Turning on and off switches within the hardware of the computer to perform specific tasks we have assigned it through binary communication.

---

## Assembly: a human-readable version of binary

In the beginning there was only binary. And, binary was painful for humans. So people invented **assembly language** as the first step to ease human-computer integration.

Instead of writing:

```text
10110000 01100001
```

you could write:

```asm
MOV AL, 61h
```

Which means:

> “Move a copy of the following value into the AL memory allocation.”

Assembly is still very close to the hardware (i.e. it is one of the lowest level programming laguage). Like binary operations, usually one assembly instruction becomes one machine instruction. This assembly instruction is translated into binary machine code by the assembler.

Think of assembly/assemblers as **nicknames humans use to remember binary operations that translate to machine tasks**.

---

## High-level programming languages: Human-centric programming

While binary is painful, assembly is still annoyingly difficult! Imagine writing a instructions for walking where you need to write out every single foot step as a series of movements for the entire trip.

So some very smart humans invented higher-level languages:

| Level   | Language | Why                                                                                                                           |
| ------- | -------- | ----------------------------------------------------------------------------------------------------------------------------- |
| Lowest  | C        | Very close to hardware and memory. You manage memory manually and interact directly with the OS and CPU concepts.             |
| Low     | C++      | Built on C but adds abstractions like classes, templates, and higher-level features while still allowing low-level control.   |
| Low–Mid | Rust     | Similar systems-level power to C/C++ but with modern safety rules and stronger abstractions.                                  |
| Mid     | Bash     | High-level for operating system tasks, but limited mainly to shell scripting and command orchestration.                       |
| High    | Python   | Highly abstracted, readable, dynamically typed, and focused on developer productivity over hardware control.                  |
| Highest | R        | Extremely high-level and domain-specific, emphasizing statistics, vectors, and data analysis rather than systems programming. |

These let you write things like:

```c
x = y + z;
```

instead of dozens of assembly instructions. This is what we use today in data science, computational biology, and bioinformatics. Higher level programming languages were made to further simplifier the human-computer communication. Allowing more and more people from disparate fields of study to access more and more of the potential of their computational systems.

Think of the level of a programming language as:

- Lower the level of a langauage the closer in communication to the hardware executing it and further from the human writing it.
- Higher the level of a language the closer in communication to the human writing it and the further from the hardware executing it.

---

## The compiler: translation from high-level code to assembly/binary

Just like how assembly needed its assembler to translate to binary code, our high level programming languages like R and Python need even more translation to binary operations. A **compiler/interpreter** translates our human-friendly code into machine-friendly assembly instructions. 

For example:

{% tabs abstraction %}

{% tab abstraction R %}

```R
add <- function(a, b) {
    return(a + b)
}
```

might become assembly like:

```
GETVAR a
GETVAR b
ADD
RETURN
```

R defaults to interpretation of the code which translated the code line-by-line to machine instructions. Think of it like streaming the instructions upon run-time instead of downloading the intructions prior to run time (like a compiler would).

{% endtab %}

{% tab abstraction python %}

```python
def add(a, b):
    return a + b
```

might become assembly like:

```
LOAD_FAST      a
LOAD_FAST      b
BINARY_ADD
RETURN_VALUE
```

{% endtab %}

{% tab abstraction c %}

```c
int add(int a, int b) {
    return a + b;
}
```

might become assembly like:

```
MOV AX, a
ADD AX, b
RET
```

{% endtab %}

{% endtabs %}

Then the assembler turns that into binary.

In general, this chain looks like:

```text
High level code
   ↓
Compiler/Interpreter
   ↓
Assembly
   ↓
Assembler
   ↓
Binary machine code
```

> Of course, there are excepts where compilers skip showing assembly and directly produce machine code. Or, other types I am sure I do not know!

---

## But, what about the Operating System?

Now imagine thousands of programs all trying to use the computer at once.

The **Operating System (OS)** is the brain that controls everything. Think of an air traffic controler in their tower overseeing the local airspace, flight line, takeways, and runways. The controller knows and control:

- what is queued to takeoff on the ground
- what is currently flying in the local airspace
- what is queued to land on the runway

Just like our OSs know:

- what processes are queued to run when resources are available
- what processes are currently running
- what processes are shutting down and closing

There are 3 operating systems to know about:

- Linux (the free, open source)
- Windows
- macOS

OS helps our programs:

- use memory
- access files
- talk to hardware
- share the CPU
- open graphical components like windows
- use peripherial devices like keyboards and mice

Without the OS, every program would need to control hardware directly. The OS simplifies a safer, easier interface for humans to use when communicating with their computational hardware.

---

## How everything fits together

Here is what the whole picture looks like when programming:

```text
You write code in any high level language
        ↓
Compiler translates it to Assembly instructions
        ↓
Assembler converts Assembly to Binary instructions
        ↓
Operating System loads program process
        ↓
CPU executes binary instructions
        ↓
Hardware does work by flipping thousands of tiny switches into different binary states
```

---

## What actually runs on the CPU?

Only binary.

Not Python.
Not C.
Not assembly.

Eventually everything becomes streams of binary digits called bits like:

```text
1100101010110010
```

The CPU fetches those instructions from memory and executes them one after another extremely quickly.

Modern CPUs can do billions of instructions per second.

---

## The important idea

Computers are layers of translation to allow the interface of human thoughts with computational machinary. Each layer of translation is just a set of files containing text in a very specific format! **Humans have created a series of dominos falling to accomplish complex communication via the most simple language imaginable!!!**

<img src="{{ '/assets/images/dominos-falling.png' | relative_url }}" alt="Dominos falling">

```text
Human thoughts
    ↓
Programming languages
    ↓
Compilers/interpreters
    ↓
Assembly
    ↓
Binary
    ↓
Electric signals
    ↓
Hardware
```

Each layer makes computers easier for humans to use. But, we can limit the usage through various means. Graphical User Interfaces (GUIs) shoehorn users into only the tasks the GUI have available. Operating on the command line bypasses any limitation as we now have the entire machine at our finger types!!!

# Install a terminal

Our terminals are the most powerful tool of the computer because it gives us the ability to tell the computer exactly what to do without limitations.

Think of the terminal like a file browser (or any application), but controlled with your keyboard instead of your mouse.

When you open a directories through a user interface, you click:

- directories
- files
- menus

In the terminal, you type commands instead.

The terminal lets you:

- move through directoried
- create, delete, edit, and move files
- run programs
- install software
- automate any number of tasks at any scale the computer can handle

### Accessing a terminal

{% tabs os %}

{% tab os windows %}

Windows does not come with a built-in terminal. Instead, Microsoft opted to use the Windows commmand prompt called `powershell`. For our purposes, most computing clusters use a Unix-based system. Let's ignore Windows idiosyncrasies and download a Unix emulator called `Git Bash`.

* In your browser, go to [https://git-scm.com/install/windows](https://git-scm.com/install/windows).
* Click on *`Click here to download`*.
* Follow the instructions to install Git Bash.
* To launch Git Bash, open the start menu and search for “Git Bash” or select `Programs -> Git Bash`.
* When the Git Bash opens, it will look something like this:

<br>
<img src="{{ '/assets/images/bash.png' | relative_url }}" alt="Bash terminal">

{% endtab %}

{% tab os mac %}

MacOS comes with a terminal built-in. This terminal runs the `zsh` shell and will allow for basic Unix commands to be run.

* Open `terminal` from your installed software.
* When the terminal opens, it will look something like this:

<br>
<img src="{{ '/assets/images/mac_terminal.png' | relative_url }}" alt="Mac terminal">

{% endtab %}

{% endtabs %}

---

