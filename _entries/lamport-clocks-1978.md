---
layout: entry
title: "Time, Clocks, and the Ordering of Events in a Distributed System"
author: "Leslie Lamport"
year: 1978
format: paper
topic: distributed-systems
source: https://lamport.azurewebsites.net/pubs/time-clocks.pdf
---

## Why I read this

Read it for a university project. It's the foundational paper on logical time in distributed systems — the source of happens-before and Lamport clocks.

## Key ideas

- In a distributed system, it's sometimes impossible to say which of two events happened first — so "happened before" is only a *partial* ordering of events, not a total one.
- **Logical clocks**: each process tracks a monotonically increasing counter, bumped on every local event and synchronized via message timestamps. This gives every event a number consistent with happens-before, without needing a shared wall clock.
- **Physical clocks**: real (wall-clock) clocks on each node drift relative to each other. The second half of the paper bounds that drift so physical timestamps still respect happens-before.
- **Message travel time**: propagation delay is non-zero, so a message's send timestamp can arrive "ahead" of the receiver's current clock. Lamport shows that with bounded clock drift and bounded transmission delay, physical clocks can be kept synchronized tightly enough that delivery still respects the causal order.

## Personal takeaways

Something as simple as "X happened before Y" has to be carefully redefined in a distributed system. It joins a cluster of problems — consensus, shared timelines, shared memory — that seem trivial on a single machine but aren't across many.
