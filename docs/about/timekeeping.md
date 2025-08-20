---
categories:
- feature
description: Issu makes time tracking and break management easy and effortless
title: Timekeeping
type: docs
---

Issu includes time tracking and a [Pomodoro Timer](https://wikipedia.org/wiki/Pomodoro_Technique) to easily track time within your issues.

## Pomodoro

The Pomodro timer within Issu is completely customizable and allows you to set the lengths and intervals appropriate for you:

```bash
Usage: issu <global flags> pom <command flags> [issue id to track time against]

Starts a Pomodoro timer--work for a certain amount of time (called a Pomodoro), take a short break, repeat this a few times, then take a long break, and repeat.

Command Flags:
-i [intervals]
   Number of Pomodori to complete before a long break.
   Default: 4
-l [duration]
   Length of a long break.
   Default: 20m
-s [duration]
   Length of a short break.
   Default: 5m
-t [duration]
   Length of Pomodoro.
   Default: 25m
```

## Time Tracking

The Pomodoro timer can log time automatically against an issue ID, just set it and forget it:

```bash
$ issu pomodoro 159
$ issu list id=159
RANK   ID    NAME      TIME
----   ---   -------   -------
11     159   Issu GA   1h6m20s
```
