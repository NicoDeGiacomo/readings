---
layout: entry
title: "Distributed Systems: Concepts and Design"
author: "George Coulouris, Jean Dollimore, Tim Kindberg, Gordon Blair"
year: 2011
format: book
topic: distributed-systems
source: https://www.pearson.com/en-us/subject-catalog/p/distributed-systems-concepts-and-design/P200000003187
---

## Why I read this

Mandatory reading for me at university. Extremely useful for going from zero to competent in distributed systems.

## Key ideas

- **Foundations**: communication primitives — interprocess messaging, RPC, indirect/event-based communication — are what turn independent nodes into a cooperating system.
- **Middleware**: higher-level abstractions (objects, services, P2P) hide communication details so applications can treat remote components as if they were local.
- **System services**: naming, security, and file systems need explicit distributed designs — location transparency, access control, and fault tolerance can't be bolted on after the fact.
- **Distributed algorithms**: without a global clock, processes must agree on ordering, leadership, and consensus using only messages — the core theoretical problem of DS.
- **Shared data**: transactions across nodes require coordination (2PC, replication, concurrency control) to preserve consistency despite partial failures.

## Personal takeaways

Gave me a foundational mental model of how the internet actually works.
