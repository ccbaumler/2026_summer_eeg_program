---
layout: module
title: "Install, Setup, and Familiarize R/RStudio"
permalink: /modules/r/setup
nav_order: 1
parent: R modules
grand_parent: Modules
---

<!-- hidden notes 

-->

## Table of contents

{: .no_toc .text-delta }

1. TOC
{:toc}

# Set-up

Before we get started, it is important that you spend time making sure that your computer is set-up and ready to go. The first step in this is basic maintenance; i.e. clean up your desktop and update your OS. Having lots of files on your desktop or multiple tabs open can negatively impact your computer’s performance. Data scientists are neat and tidy! Spend time getting yourself organized.

In order to get setup a standard R tool stack, you need to do two things:

1. Download the most recent version of R and install

    R is open source and constantly changing. Make regular version checks part of your routine. R will run on a variety of platforms, but there are slight differences between Mac, Windows, and Linux versions.

    Download the latest version of [R here and install](https://ftp2.osuosl.org/pub/cran/).
    > Starting with R version 4.0.0, R for Windows uses a toolchain bundle called rtools4. If you are installing on a Windows device, [go here and install the latest version of RTools](https://cran.r-project.org/bin/windows/Rtools/).

2. Download the most recent version of RStudio and install

RStudio is an integrated development environment, or [IDE](https://en.wikipedia.org/wiki/Integrated_development_environment). An IDE allows for intuitive usage of a programming language through numerous additional features. All of our work will be done in RStudio.

Download the latest version of [RStudio here and install](https://posit.co/products/open-source/rstudio).

## Familiarizing

### R

R is a high level programming language born from the S statistical programming language in 1993. As a mature software, R is widely known as a stattistical programming language with an impressive data manipulation and visualization suite of tools.

R is traditionally run in the terminal in a REPL (read-eval-print-loop). Now-a-days, it is mainly use through the IDE preferred by the programmer. R code is stored in a `.r` file and may be run through the command line interface (CLI) or through an IDE of choice.

### RMarkdown

Markdown is a specific type of markup language with the file extension `.md`. Markdown focuses on readability and simplicity. The raw markdown file is easily readable by a human. Unlike other markup languages like xml or html. There is limited syntax to remember but that allow for a well-formatted final document like this one which was written entirely in markdown! Markdown's simplicity and plain text formatting allows it to be extremely portable. A markdown file is language agnostic, or it can be read on any operating system (OS) and in any editor software. This also means that a markdown file is very unlikely to become out-dated or corrupted. In otherwords, markdown documents are future-proof.

RMarkdown files have the extension .Rmd and can be created in RStudio by going to `File > New File > RMarkdown`. RMarkdown files allow you to combine text, code, and output in a single document.

### Knitting

RMarkdown files need to be knit in order to produce a final document. This is done by clicking the Knit button at the top of the RStudio window. Knitting produces a final document in HTML format. You will turn in all homework assignments as knitted HTML files. If your code does not work, then the file will not knit.


## Acknowledgements

Material credited to Dr. Joel M Ledford's BIS 015 L course
