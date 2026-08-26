---
title: "Learning to Code"
page_type: resources
---

Students often ask me how they should learn to code, what language they should learn, and which tools they should use. There isn't a single correct route, but the advice and resources below are what I generally recommend.

This is deliberately a curated rather than comprehensive list. There are many excellent languages, tools and learning resources that aren't included here.

## How I recommend learning

### Learn by writing code

Programming is a practical skill. Tutorials and books are useful for getting started, but you learn to program by writing programs.

Once you understand the basic syntax of a language, start building things. Small projects that interest you are usually more valuable than working through increasingly advanced tutorials without applying what you have learned.

### Start with one language

Don't worry about learning several programming languages at once. The important concepts—variables, functions, data structures, control flow, decomposition and debugging—transfer between languages.

For most students who ask me where to start, I recommend Python. It has relatively accessible syntax, excellent teaching material, and is widely used in research, data analysis and scientific computing.

Once you are comfortable programming in one language, learning another becomes considerably easier.

### Learn to solve problems, not just write syntax

Knowing the syntax for a for loop is different from recognising when you need one.

Try to move progressively from exercises that tell you exactly what to do towards problems where you have to decide how to structure the solution yourself.

### Learn to debug

Errors are a normal part of programming. Being able to investigate why a program doesn't work is at least as important as being able to write one in the first place.

Read error messages carefully. Learn to inspect intermediate values, reduce problems to smaller examples, and test your assumptions about what the program is doing.

### Learn to use documentation

You don't need to memorise everything. Professional programmers routinely look things up.

Learning how to navigate documentation and find the information you need is itself an important programming skill.

### Use AI as a tool, not a substitute for understanding

AI tools can be useful for explaining unfamiliar concepts, interpreting error messages, suggesting approaches, and reviewing code.

They can also produce code that is subtly—or completely—wrong. If you use generated code, you should be able to explain what it does and have some way of determining whether it is correct.

[TODO: Expand/adjust this section to reflect my own guidance on AI-assisted programming.]

## Getting started

If you have never programmed before, I generally recommend starting with Python.

You need to learn the fundamentals:

- variables and basic data types;
- conditional statements;
- loops;
- functions;
- lists, dictionaries and other collections;
- reading and writing files;
- importing and using libraries;
- basic error handling.

You don't need to master Python before starting to write useful programs.

## Introductory resources

[RESOURCE: Preferred introductory Python course]Add 1–2 sentences explaining why I recommend it and who it is suitable for.

[RESOURCE: Preferred introductory Python book/tutorial]Add 1–2 sentences explaining its strengths and how I suggest using it.

[RESOURCE: Python documentation/tutorial]Possibly include the official Python tutorial here, with a note that it may be better as a reference once the basics are familiar.

## What should I learn next?

Once you can write simple programs, I would broadly suggest progressing through the following areas:

```text
Programming fundamentals → small projects → Git → debugging and testing → packages and environments → larger projects
```

This isn't a rigid curriculum. You'll encounter many of these topics naturally as your programs become more substantial.

### Build something

Choose a small problem that actually interests you. For example:

- automate a repetitive task;
- analyse a dataset;
- process a collection of files;
- reproduce a figure from a paper;
- implement a simple algorithm;
- build a small command-line tool.

A project forces you to make decisions that carefully constructed exercises often make for you.

### Learn Git

Learn version control relatively early. At minimum, understand repositories, commits, branches and how to inspect the history of your work.

GitHub is useful for hosting and sharing Git repositories, but Git and GitHub are not the same thing: Git is the version-control system; GitHub is one service built around it.

[RESOURCE: Good introductory Git resource]

### Learn testing

As your programs become larger, you need a systematic way of establishing whether they behave as expected.

For Python, I generally recommend pytest.

You don't need to become an expert in software testing immediately. Start by learning how to write small tests for functions whose expected behaviour you understand.

[RESOURCE: Introductory testing/pytest resource]

### Learn about packages and environments

Eventually, your code will depend on software written by other people. Learn what dependencies and virtual environments are and how to record the dependencies required to run a project.

[TODO: Add preferred Python environment/dependency recommendation and resource.]

## A small toolkit

There are usually many good tools for the same job. These are intended as sensible starting points, not claims that they are universally the best choices.

| Purpose | Suggestion |
|---|---|
| Programming language | Python |
| Code editor | VS Code |
| Version control | Git |
| Git hosting/collaboration | GitHub |
| Python environments/dependencies | uv |
| Testing | pytest |
| Linting/formatting | Ruff |
| Interactive computing | Jupyter |
| Documentation | MkDocs |

Don't feel that you need to learn all of these before you can start programming. Adopt tools when they solve a problem you actually have.

[TODO: Add links and perhaps one-sentence descriptions for tools where useful.]

## Programming for research

If you are learning programming in order to do research, there is a point at which a collection of scripts becomes research software.

Code used to produce research results should be understandable, reproducible and sufficiently reliable for the conclusions you draw from it.

Depending on your work, useful Python libraries may include:

| Purpose | Suggestion |
|---|---|
|NumPy | numerical arrays and computation|
|pandas / Polars / Pyspark | tabular data|
|Matplotlib / seaborn | plotting|
|SciPy | scientific and numerical algorithms|
|Jupyter / Marimo | interactive exploration and notebooks|
|Pytorch / Sklearn | machine learning |

These aren't things you need to learn simply because you are learning Python. Learn the tools that are relevant to the problems you are trying to solve.

As your research code grows, I recommend paying particular attention to:

- version control;
- reproducible environments;
- separating reusable code from individual analyses;
- testing important calculations;
- documenting assumptions and methods;
- recording the versions of dependencies;
- making computational results reproducible from the underlying data and code.

## Research software resources

[RESOURCE: Software Carpentry / relevant Carpentries lesson]

[RESOURCE: Reproducible research resource]

[RESOURCE: Research software engineering best-practice resource]

[TODO: Add any resources I regularly recommend to students/researchers.]

## Recommended resources

A few resources that I particularly recommend.

Programming

[RESOURCE NAME]What it covers, who it is for, and why I recommend it.

[RESOURCE NAME]What it covers, who it is for, and why I recommend it.

Git and software development

[RESOURCE NAME]What it covers, who it is for, and why I recommend it.

Scientific and research computing

[RESOURCE NAME]What it covers, who it is for, and why I recommend it.

## A final piece of advice

Don't wait until you feel that you know enough to start a project. Choose something small, start writing it, and learn what you need as you encounter problems.

The objective isn't to know every feature of a programming language or every available tool. It's to become increasingly capable of turning a problem into a program that you—and eventually other people—can understand, test and maintain.