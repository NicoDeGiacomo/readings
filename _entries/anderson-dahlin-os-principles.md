---
layout: entry
title: "Operating Systems: Principles and Practice"
author: "Thomas Anderson, Michael Dahlin"
year: 2014
format: book
topic: operating-systems
source: http://ospp.cs.washington.edu/
---

## Why I read this

Mandatory reading for me at university. Extremely useful for going from zero to competent in operating systems.

## Key ideas

- **Kernels and processes**: the kernel/user-mode boundary enforces isolation so buggy or malicious programs can't crash or take over the system.
- **Concurrency**: correct concurrent programs need disciplined synchronization — locks, condition variables, monitors — built on top of low-level context switching.
- **Memory management**: each process sees a private virtual address space; hardware and OS cooperate to translate, page, and protect memory.
- **Persistent storage**: file systems turn unreliable, slow disks into durable, crash-consistent, hierarchical namespaces.

## Personal takeaways

Improved my understanding of how servers actually work — what it means to host software, what Docker is, how virtualization differs from containerization, what a distroless image is. None of those are the book's main topic, but all of them clicked once the underlying OS primitives did.
