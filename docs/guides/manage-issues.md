---
categories:
- guide
description: How to manage issues
title: Manage Issues
---

Within Issu, issues are [Markdown files](https://wikipedia.org/wiki/Markdown) within a directory specified by {{% config issuesPath %}}.  Issu's primary purpose is to manage these files--organize them, edit them, and display them.

## Issue Format

Issu files are broken up into two parts:

- **Front Matter** \
A block of [Jsonnet]({{% ref "/docs/references/jsonnet" %}}) containing the [Labels]({{% ref "/docs/guides/manage-labels" %}}) for the issue contained within `---`.
- **Markdown** \
The actual text and details of the issue.

An example issue looks like this:

```markdown
---
{
  apps: [
    'Issu',
  ],
  created: '2025-01-28',
  difficulty: '3 - Heroic',
  name: 'Issu GA',
  priority: '4 - Gotta Have It',
  rank: '11',
  status: '4 - Done',
  time: [
    '2025-06-17=1h6m20s',
    '2025-06-18=39m7s',
  ],
  type: 'Feature',
}
---

# 159 - Issu GA

## TODO

- [x] [2](./2.md)
- [x] replace places that can set multiple values (like config -x) with comma separated handling?
- [ ] Setup hugo website for issu.dev
- [x] Setup GitHub repository for issu
- [ ] Add issu release pipeline
- [ ] Deploy to stg/prd
- [ ] Add to google search indexing
```
## Listing Issues

{{% cli list %}} is a powerful command for querying and displaying issues in various formats (default is table, but it can also display as JSON).

`list` supports an advanced filtering syntax based on issue labels, such as `Status=!Done && Name=issu`.  The first part of the filter must be a label name, and the second part is any valid [Go Regular Expression Syntax](https://github.com/google/re2/wiki/Syntax):

```bash
$ issu list 'status != Done && name = "(?i)issu"'
RANK   ID    NAME                                                                                                 TIME
----   ---   --------------------------------------------------------------------------------------------------   ----
55     189   As an issu user, I want to trigger scripts from the Pomodoro timer so I can do interesting things    
```

Default values for `list` can be configured, such as the {{% config listColumns "default columns" %}}.

## Prioritizing Issues

Issues can have their priorities changed using {{% cli after %}} and {{% cli before %}}.  These commands will move the priority label (default: `rank`) before/after the issue specified.

## Editing Issues

Issues can be edited using {{% cli edit %}}--Issu will open the issue within your $EDITOR variable.  Additionally, issues can have labels bulk-edited using {{% cli label %}}.
