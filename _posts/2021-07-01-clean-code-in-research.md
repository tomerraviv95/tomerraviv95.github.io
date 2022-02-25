---
layout:     post
title:      Clean Code in Research
date:       2021-07-01 00:00:00
author:     Tomer Raviv
categories: jekyll
thumbnail:  binary
tags:
 - clean code
 - reproducibility
---

**TLDR** What is clean code? How is it applied to research? This post discusses the importance of clean code principles to research applications.

*“The art of programming is the art of organizing complexity”, Edsger Dijkstra.*

Clean code is basic for many software engineers; Be it backend, frontend or full stack developers, they all learn the basic principles that keep the code maintainable and readable (sometimes in the hard way - by making mistakes). 

Some have made the art of clean code their life mission. For example, Robert Martin, the guru of the clean-code community, has courses, videos and books revolving around the subject. He sternly enforces the utmost of logic and organization in one’s code: From proper commenting and no code duplicates, to intention-based methods, constants and variables.

The art of coding is useful for development. One of the key factors that affects your salary is your technical expertise; It is common for one to hone this skill for years and years. But how does the art of coding apply to empirical academic research? This type of research is widely spread among machine-learning and communication practitioners in general.

Empirical research is built on the academic frontier: Reading, reviewing and summarizing papers in your domain. When writing your own paper, you pour this knowledge in, while proposing a solution to a chosen problem. This solution is based on many coded simulations and computations; It is at the heart of the paper. Taking a software-engineer perspective, if the paper is the frontend, the code repository is the backend.

We see many that polish their writing in academics, but not their coding style. The question that I raise here is - Why? 

**Clean Code in Research** Shouldn’t research code be as maintainable as a top-leading project in a high-tech company? Be as readable as a production code that went through dozens of hands?
We often work alone, jumping from project to another, neglecting the rules of clean code. Is it a waste of time? My hope is to convince you that - it is not.

**Reasons** What are the benefits in research? Why would you invest costly time in it? There surely are many reasons, but the ones I see most relevant are: (1) reproducibility (2) readability and (3) extensibility.

**Readability** When focusing on the reader who wants to understand your research, the code should support the architecture and equations. If the code structure is logical, one can easily understand the high level view of the setup and solution, and dive in the code to understand specific parts, such as how mathematical statements appear in practice.
Moreover, readable code is probably the best entry point to a new unknown field. The dots are sometimes easier to connect through a detailed function, rather than through hollow equations.

*“Always code as if the guy who ends up maintaining your code will be a violent psychopath who knows where you live”, Martin Golding.*

**Reproducibility** As I wrote about it in a previous post, I will not elaborate on it again but rather emphasize the advantages. As one who tried to clone outdated and broken repositories, your code should contain either: Entire project, properly documented and working, or a sample that passes run-time compilation. If validating the entire project is too much effort, focus on the second notion and create a minimal viable code that exemplifies your solution and produces one of the graphs in your paper. A small but working example code is preferred to a non-working full project.

**Extensibility** Many times researchers build on their own knowledge and projects, to implement further ideas they had before. If the code is clean, it is much easier to dive in to extend it to new ideas, continuing a previous train-of-thoughts.

As one is probably convinced by now, there are many reasons for keeping the research code clean. Though most of the clean code work is done at the start and end of the project (at least for me), you should soak in the high level principles and apply them to your everyday coding. 

**When To Apply** At the beginning of the project, spend time planning how the architecture will look, which classes to construct and what abstraction level you should instruct. At the end, however, near the submission of the paper, you should wrap it up for future usages (by yourself or others), leaving as little loose undocumented ends as possible. A full-on code-review would be quite responsible.

*"Give me six hours to chop down a tree, and I will spend the first four sharpening the axe", Abraham Lincoln.*

**Principles** What are the principles that apply to research code the best as I see it? These are the main points: (1) Document non-simple functions and blocks of codes, add [type-hints][1] whenever you can. (2) Organize the folders and files - different folders for resources, results and the code itself. Various files for gathering constants, project-relative paths and experimental configuration. (3) Keep the length of the code to a minimum by removing duplicate code, employing [data-classes][2] and wrapping with [decorators][3]. (4) Exploit [design-patterns][4]. The factory and strategy patterns are quite fit to research applications.

[1]: https://docs.python.org/3/library/typing.html

[2]: https://docs.python.org/3/library/dataclasses.html 

[3]: https://realpython.com/primer-on-python-decorators/ 

[4]: https://refactoring.guru/design-patterns
