---
layout: entry
title: "Transactional Outbox Pattern"
author: "Chris Richardson"
year: 2018
format: blog
topic: microservices
source: https://microservices.io/patterns/data/transactional-outbox.html
---

## Why I read this

A pattern for turning non-transactional cross-system actions — like writing to a DB and publishing an event — into something that behaves transactionally. Worth reading if you've hit dual-write problems.

## Key ideas

- Outbox table + worker: inside the same DB transaction, insert a row describing the action you need to dispatch (event, external call, etc.). A separate continuously-running worker reads those rows and performs the action, retrying until it succeeds.

## Personal takeaways

Used this pattern many times — in university projects and at work.
