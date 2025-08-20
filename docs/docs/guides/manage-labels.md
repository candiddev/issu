---
categories:
- guide
description: How to manage labels
title: Manage Labels
---

Labels are a key component for organizing issues within Issu.  Labels are defined within your {{% config labels configuration %}}, and added to issues automatically or manually.

## Adding Labels

Labels are defined under {{% config labels %}}.  Issu ships with default labels, but these can be modified to suit your needs (especially for localization).  Issu supports these types of labels:

- `date`\
A label that represents the date of something, such as when the issue was created or when it needs to be completed.

- `multi`\
A label that can contain multiple values, such a list of teams affected.

- `name`\
A label representing the name of an issue.  Only one label can have this type.

- `rank`\
A label representing the ranking of an issue.  Only one label can have this type.

- `text`\
A label representing a single text value.

- `time`\
A label that contains time tracking details for the issue.  Only one label can have this type.


### Label Validators

Additionally, labels can support various controls around their usage:

- {{% config labels_default %}}\
Set a default value for the label.  Certain labels only support a specific value for the default:
  - `date`: `today`
  - `rank`: `first` or `last`

- {{% config labels_required %}}\
Require the label to be set.  This will cause issues missing this label to [fail linting]({{% ref "/docs/guides/linting-issues" %}}).

- {{% config labels_regexp %}}\
A valid [Go Regular Expression Syntax](https://github.com/google/re2/wiki/Syntax) to match against label values within issues.  Not supported for `date` or `rank` labels.  Any issues that do not match the regexp check will [fail linting]({{% ref "/docs/guides/linting-issues" %}}).

- {{% config labels_values %}}\
A list of valid values for the label.  Only supported by `multi` and `text` labels.  Any issues that do not match a value within the list will [fail linting]({{% ref "/docs/guides/linting-issues" %}}).

## Organize Issue Labels

Issu can organize the labels on issues automatically using {{% cli org %}}.  This command will:

- Add missing default labels
- Correct misspelled labels
- Renumber any positional labels so they are sequential (1, 2, 3 instead of 1:aaaa)

Issu org can create a lot of diffs, but the changes should be minor and not impact the git history of the issue.
