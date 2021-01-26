---
layout: post
title: A Love Letter to Golang Concurrency
date: 2021-01-26
---

## Lighter

A big problem with Java is that it uses OS threads under the hood for its concurrency, meaning that every Java thread
has a fixed memory overhead. Golang circumvents this problem by implementing userspace threads (goroutines) with their
own dynamic stack.

## Faster

Goroutines are faster because they utilize userspace scheduling. In other words, the Go runtime decides when a
goroutine is ready to do work, using inotify under the hood to track blocking tasks. Because of this application
awareness, Golang can wring more efficiency out of the CPU by ensuring that OS threads are always working on tasks
that can make progress. The cherry on top is that the scheduler keeps goroutines on the same OS thread to prevent
context-switching at the kernel level!

## Friendlier

Golang graciously abstracted all of this inotify and scheduling nonsense away from the developer-- you can just write
plain-old sequential code without having to worry about callbacks. Anyone who has written concurrent software with
Boost::asio (or pre-Promise Javascript for that matter) has horror stories of callback hell. At the same time, Golang
borrowed the channel concept from Boost::asio, which makes writing lock-free concurrent code a breeze
(read: no more deadlocks).

I love the Golang concurrency model, and so should you.
