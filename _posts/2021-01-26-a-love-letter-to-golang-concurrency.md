---
layout: post
title: A Love Letter to Golang Concurrency
date: 2021-01-26
---

### Lighter

A big problem with Java is that it uses OS threads under the hood for its concurrency, meaning that every Java thread
has a fixed memory overhead. Golang circumvents this problem by implementing userspace threads (goroutines) with their
own dynamic stack.

### Faster

Goroutines are faster because they utilize userspace scheduling. In other words, the Go runtime decides when a
goroutine is ready to do work, using `inotify` under the hood to track blocking tasks. Because of this application
awareness, Golang can wring more efficiency out of the CPU by ensuring that OS threads are always working on tasks
that can make progress. The cherry on top is that the scheduler keeps goroutines on the same OS thread to prevent
context-switching at the kernel level!

### Friendlier

Golang graciously abstracted all of this `inotify` and scheduling nonsense away from the developer-- you can just write
plain-old sequential code without getting into callback hell. Golang also employs the channel concept from Tony Hoare's
CSP model of concurrency, which makes writing lock-free interprocess communication a breeze (read: no more deadlocks).

This is just a subset of what sets Golang apart, but the point stands: **I love the Golang concurrency model, and
so should you.**
