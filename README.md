# Data Science 3

## PART I: DEEP LEARNING

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/wikiti/pandoc-book-template/blob/master/LICENSE.md)

#### Chapter 1: Introduction to Deep Learning and AI

#### Chapter 2: History of Deep Learning and AI

#### Chapter 3: Math PRIMER

#### Chapter 4: Tensorflow

#### Chapter 5: Introduction to Deep Learning 

#### Chapter 6: Deep Neural Network

#### Chapter 7: Convolutional neural networks 

#### Chapter 8: Re-current Neural Network-LSTM 

#### Chapter 9: Word Embedding 

#### Chapter 10: Recommendation-engine 

#### Chapter 11: Reinforcement Learning 

#### Chapter 12: Graph Theory-Social media analytic - Course Wrap Up 


## PART II: Environmental Data Sciences

### Section I: DESCRIPTIVE MODELLING
#### Chapter 1: Introduction to the course Introduction to R
#### Chapter 2: Basic programming in R
#### Chapter 3: Data Manipulation
#### Chapter 4: Explorative Data Analysis
#### Chapter 5: Summary Statistics,Data Visualization
#### Chapter 6: Summary Statistics, Documentation and Report with RMarkdown
### Section II: DETERMINISTIC MODELLING
#### Chapter 7: Deterministic Function
#### Chapter 8: Models by function fitting: Fitting Linear Models
#### Chapter 9: Models by function fitting: non linear models, arbitrary curves
#### Chapter 10: Models by function fitting: arbitrary curves
#### Chapter 11: Recap of determinstic modelling, RBookdown
### Section II: PROBABILISTIC MODELLING
#### Chapter 12: Probability Basics
#### Chapter 13: Discrete Distributions
#### Chapter 14: Continuous Distributions
### Section III: TRADITIONAL MACHINE LEARNING
### Section IV: DEEP LEARNING





This report evolves from the course I taugh at McMaster University, APU. and the following sites:

http://introtodeeplearning.com/

http://introtodeeplearning.com/2021/index.html

http://courses.cms.caltech.edu/cs154/

https://ctme.caltech.edu/programs-for-individuals/data-analytics-open/ai-machine-learning-bootcamp-certificate-open

https://cs230.stanford.edu/

Resources & References:

RNN

http://www.hexahedria.com/2015/08/03/composing-music-with-recurrent-
neural-networks/

http://colah.github.io/posts/2015-08-Understanding-LSTMs/

https://github.com/Kulbear/deep-learning-

coursera/blob/master/Sequence%20Models/Building%20a%20Recurrent%
20Neural%20Network%20-%20Step%20by%20Step%20-%20v2.ipynb

http://karpathy.github.io/2015/05/21/rnn-effectiveness/

On the difficulty of training Recurrent Neural Networks

https://arxiv.org/pdf/1211.5063.pdf

## Description

This repository contains a simple template for building [Pandoc](http://pandoc.org/) documents;
Pandoc is a suite of tools to compile markdown files into readable files (PDF, EPUB, HTML...).
I (Q) copied it from this repo https://github.com/alessandrocucci/book-template

## Usage

### Installing

Please, check [this page](http://pandoc.org/installing.html) for more information. On ubuntu, it
can be installed as the *pandoc* package:

```sh
sudo apt-get install pandoc
```

This template uses [make](https://www.gnu.org/software/make/) to build the output files, so don't
forget to install it too:

```sh
sudo apt-get install make
```

To export to PDF files, make sure to install the following packages:

```sh
sudo apt-get install texlive-fonts-recommended texlive-xetex
```

### Folder structure

Here's a folder structure for a Pandoc book:

```
my-book/         # Root directory.
|- build/        # Folder used to store builded (output) files.
|- chapters/     # Markdowns files; one for each chapter.
|- images/       # Images folder.
|  |- cover.png  # Cover page for epub.
|- metadata.yml  # Metadata content (title, author...).
|- Makefile      # Makefile used for building our books.
```

### Setup generic data

Edit the *metadata.yml* file to set configuration data (note that it must start and end with `---`):

```yml
---
title: My book title
author: Alessandro Cucci
rights:  MIT License
language: it-IT
tags: [book, my-book, etc]
abstract: |
  Your summary text.
mainfont: DejaVu Sans
---
```

You can find the list of all available keys on
[this page](http://pandoc.org/MANUAL.html#extension-yaml_metadata_block).

### Creating chapters

Creating a new chapter is as simple as creating a new markdown file in the *chapters/* folder;
you'll end up with something like this:

```
chapters/01-introduction.md
chapters/02-installation.md
chapters/03-usage.md
chapters/04-references.md
```

Pandoc and Make will join them automatically ordered by name; that's why the numeric prefixes are
being used.

All you need to specify for each chapter at least one title:

```md
# Introduction

This is the first paragraph of the introduction chapter.

## First

This is the first subsection.

## Second

This is the second subsection.
```

Each title (*#*) will represent a chapter, while each subtitle (*##*) will represent a chapter's
section. You can use as many levels of sections as markdown supports.

#### Manual control over page ordering

You may prefer to have manual control over page ordering instead of using numeric prefixes.

To do so, replace `CHAPTERS = chapters/*.md` in the Makefile with your own order. For example:

```
CHAPTERS += $(addprefix ./chapters/,\
 01-introduction.md\
 02-installation.md\
 03-usage.md\
 04-references.md\
)
```

#### Links between chapters

Anchor links can be used to link chapters within the book:

```md
// chapters/01-introduction.md
# Introduction

For more information, check the [Usage] chapter.

// chapters/02-installation.md
# Usage

...
```

If you want to rename the reference, use this syntax:

```md
For more information, check [this](#usage) chapter.
```

Anchor names should be downcased, and spaces, colons, semicolons... should be replaced with hyphens.
Instead of `Chapter title: A new era`, you have: `#chapter-title-a-new-era`.

#### Links between sections

It's the same as anchor links:

```md
# Introduction

## First

For more information, check the [Second] section.

## Second

...
```

Or, with al alternative name:

```md
For more information, check [this](#second) section.
```

### Inserting objects

Text. That's cool. What about images and tables?

#### Insert an image

Use Markdown syntax to insert an image with a caption:

```md
![A cool seagull.](images/seagull.png)
```

Pandoc will automatically convert the image into a figure (image + caption).

If you want to resize the image, you may use this syntax, available in Pandoc 1.16:

```md
![A cool seagull.](images/seagull.png){ width=50% height=50% }
```

Also, to reference an image, use LaTeX labels:

```md
Please, admire the gloriousnes of Figure \ref{seagull_image}.

![A cool seagull.\label{seagull_image}](images/seagull.png)
```

#### Insert a table

Use markdown table, and use the `Table: <Your table description>` syntax to add a caption:

```md
| Index | Name |
| ----- | ---- |
| 0     | AAA  |
| 1     | BBB  |
| ...   | ...  |

Table: This is an example table.
```

If you want to reference a table, use LaTeX labels:

```md
Please, check Table /ref{example_table}.

| Index | Name |
| ----- | ---- |
| 0     | AAA  |
| 1     | BBB  |
| ...   | ...  |

Table: This is an example table.\label{example_table}
```

#### Insert an equation

Wrap a LaTeX math equation between `$` delimiters for inline (tiny) formulas:

```md
This, $\mu = \sum_{i=0}^{N} \frac{x_i}{N}$, the mean equation, ...
```

Pandoc will transform them automatically into images using online services.

If you want to center the equation instead of inlining it, use double `$$` delimiters:

```md
$$\mu = \sum_{i=0}^{N} \frac{x_i}{N}$$
```

[Here](https://www.codecogs.com/latex/eqneditor.php)'s an online equation editor.

### Output

This template uses *Makefile* to automatize the building process. Instead of using the *pandoc cli
util*, we're going to use some *make* commands.

#### Export to PDF

Use this command:

```sh
make pdf
```

The generated file will be placed in *build/pdf*.

Please, note that PDF file generation requires some extra dependencies (~ 800 MB):

```sh
sudo apt-get install texlive-xetex ttf-dejavu
```

#### Export to EPUB

Use this command:

```sh
make epub
```

The generated file will be placed in *build/epub*.

#### Export to HTML

Use this command:

```sh
make html
```

The generated file(s) will be placed in *build/html*.

#### Extra configuration

If you want to configure the output, you'll probably have to look the
[Pandoc Manual](http://pandoc.org/MANUAL.html) for further information about pdf (LaTeX) generation,
custom styles, etc.

## References

- [Pandoc](http://pandoc.org/)
- [Pandoc Manual](http://pandoc.org/MANUAL.html)
- [Wikipedia: Markdown](http://wikipedia.org/wiki/Markdown)

## Contributors

This project has been developed by:

| Avatar | Name | Nickname | Email |
| ------ | ---- | -------- | ----- |
| ![](http://www.gravatar.com/avatar/2ae6d81e0605177ba9e17b19f54e6b6c.jpg?s=64)  | Daniel Herzog | Wikiti | [info@danielherzog.es](mailto:info@danielherzog.es)
|   | Alessandro Cucci | alessandrocucci | [alessandro.cucci@gmail.com](mailto:alessandro.cucci@gmail.com)
