---
categories:
- guide
description: How to track time with Issu
title: Time Tracking
---

Issu's built-in Pomodoro timer makes time tracking and management easy.

## Pomodoro

[Pomodoro Technique](https://wikipedia.org/wiki/Pomodoro_Technique) is a time management technique where you work in intervals with short breaks in-between, culminating in a long break after a certain number of intervals.

By default, Issu's Pomodoro is configured for:

- 25 minutes of work (a Pomodoro)
- 5 minute break after each Pomodoro
- After 4 Pomodoros, a 20 minute break

All of these values can be configured under {{% config pomodoro %}} or within the {{% cli pom %}} command.  When a timer is hit, a terminal bell will ring reminding you to take a break or start working.  These breaks can be delayed and Issu will track how long the delay was and adjust things accordingly.

## Time Tracking

Using {{% cli pom %}} and specifying an issue ID at the end will cause Issu to track the Pomodoro time within the `time` label for the issue:

```bash
$ issu pomodoro 159
$ issu list id=159
RANK   ID    NAME      TIME
----   ---   -------   -------
11     159   Issu GA   1h6m20s
```

The `time` label is a list of dates and time spent:

```json
{
  "time": [
    "2025-06-17=1h6m20s",
    "2025-06-18=39m7s"
  ]
}
```
