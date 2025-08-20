---
categories:
- reference
description: Reference documentation for Issu's configuration
title: Config
---

{{% snippet config_format Issu issu %}}

## Configuration Values

{{% snippet "config_cli" issu %}}

{{% snippet "config_httpClient" Tunlr %}}

{{% snippet config_key "issuesPath" %}}

String, the relative or absolute path to the directory containing issues.  Will be created if it doesn't exist.

**Default:** `"issues"`

{{% snippet "config_jsonnet" true %}}

{{% snippet config_key "labels" %}}

Labels is a map of label names to configurations that define labels/metadata for issues.  See [Labels]({{% ref "/docs/guides/manage-labels" %}}) for more details.

**Default:**
```json
{
  "labels": {
    "created": {
      "default": ["today"],
      "required": true,
      "type": "date"
    },
    "name": {
      "required": true,
      "type": "name"
    },
    "rank": {
      "default": ["last"],
      "type": "positional"
    },
    "status": {
      "required": true,
      "type": "text",
      "values": [
        "To Do",
        "In Progress",
        "Done",
      ]
    },
    "time": {
      "type": "time"
    }
  }
}
```

### `labels_[label]_default` {#labels_default}

Single or list of default string values that are added to issues during [creation]({{% ref "/docs/references/cli#add" %}}) or [organize]({{% ref "/docs/references/cli#org" %}}) for the label, if it's [required](#labels_required).  Must match [regexp](#labels_regexp) and [values](#labels_values), if they're defined.

**Default:** `[]`

### `labels_[label]_required` {#labels_required}

Boolean, determines if the label is required.  Issues that do not have this label will cause [linting failures]({{% ref "/docs/guides/linting-issues" %}}).

**Default:** `false`

### `labels_[label]_regexp` {#labels_regexp}

String, a valid Regular Expression to check label values against.  Issues that do not have an appropriate value will cause [linting failures]({{% ref "/docs/guides/linting-issues" %}}).

**Default:** `""`

### `labels_[label]_type` {#labels_type}

String, the type of the underlying Label.  See [Labels]({{% ref "/docs/guides/manage-labels" %}}) for supported values.

**Default:** `""`

### `labels_[label]_values` {#labels_values}

Single or list of allowed string values for the label.  Issues that do not have a value from this list will cause [linting failures]({{% ref "/docs/guides/linting-issues" %}}).

**Default:** `[]`

{{% snippet config_licenseKey Issu %}}

{{% snippet config_key "listColumns" %}}

List of label names to show by default when listing issues.

**Default:**

```json
{
  "listColumns": [
    "rank",
    "id",
    "name",
    "time",
  ]
}
```

{{% snippet config_key "listFilter" %}}

String, the default filter to apply when listing issues.

**Default:** `"status!=Done"`

{{% snippet config_key "listLimit" %}}

Number, the default number of issues to display when listing.

**Default:** `10`

{{% snippet config_key "listSort" %}}

List of label names to sort by default when listing issues.  Issues will be sorted by each label sequentially.  `!` can be prepended to the label name to invert the sort.

**Default:** `[]`

{{% snippet config_key "pomodoro" %}}

Configuration for the [Pomodoro timer]({{% ref "/docs/references/cli#pom" %}}).  See [Time Tracking]{{% ref "/docs/guides/time-tracking" %}} for more information.

{{% snippet config_key pomodoro_durationBreakLong %}}

String, the duration for a Pomodoro long break.  {{% config_duration %}}

**Default:** `"20m"`

{{% snippet config_key pomodoro_durationBreakShort %}}

String, the duration for a Pomodoro short break.  {{% config_duration %}}

**Default:** `"5m"`

{{% snippet config_key pomodoro_durationPomodoro %}}

String, the duration for a Pomodoro working session.  {{% config_duration %}}

**Default:** `"25m"`

{{% snippet config_key pomodoro_intervals %}}

Number, how many Pomodoro intervals until a long break.

**Default:** `4`

{{% snippet config_key pomodoro_nagSeconds %}}

Number, how many seconds until a nag notification is emitted repeatedly.

**Default:** `15`
