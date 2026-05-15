---
categories:
- reference
description: Reference documentation for Issu's configuration
title: Config
---

{{% snippet config_format Issu issu %}}

## Configuration Values

### `archive` {#archive}

Configurations for archiving old issues.

{{% snippet config_key "archive_include" %}}

Boolean, determines if archived issues are parsed.  Enabling this may decrease performance.

**Default:** `false`

{{% snippet config_key "archive_path" %}}

String, the path to the folder where issues will be archived to.  If this doesn't start with a `/`, it will be relative to the {{% config issuesPath %}}.

**Default:** `"archive"`

{{% snippet config_key "archive_rule" %}}

String, an {{% expr %}} for evaluating whether an issue will be archived.  The object passed to it will be a `map[string]any` of the Issue labels.  If the expression returns `true`, the issue will be archived.

**Default:** `"status == \"Done\""`

By default, Issue will archive any issues if the label `status` has the value of `Done`.

{{% snippet "config_cli" issu orange %}}

{{% snippet "config_httpClient" Issu %}}

{{% snippet config_key "issuesPath" %}}

String, the relative or absolute path to the directory containing issues.  Will be created if it doesn't exist.

**Default:** `"issues"`

{{% snippet "config_jsonnet" true %}}

### `labels` {#labels}

Labels is a map of label names to configurations that define labels/metadata for issues.  See [Labels]({{% ref "/docs/guides/manage-labels" %}}) for more details.

**Default:**
```json
{
  "labels": {
    "complete": {
      "expression": "tasks == 0 ? \"\" : sprintf(\"%v%%\", round((tasks_done / (tasks == 0 ? 1 : tasks)) * 100))",
      "type": "text"
    },
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
    "tasks": {
      "expression": "tasks_done + tasks_todo",
      "type": "text"
    },
    "tasks_done": {
      "expression": "countMatches(description, ` \\[(x|X)\\] `)",
      "type": "text"
    },
    "tasks_todo": {
      "expression": "countMatches(description, ` \\[ \\] `)",
      "type": "text"
    },
    "time": {
      "type": "time"
    }
  }
}
```

#### `labels_[label]_default` {#labels_default}

Single or list of default string values that are added to issues during [creation]({{% ref "/docs/references/cli#add" %}}) or [organize]({{% ref "/docs/references/cli#org" %}}) for the label, if it's [required](#labels_required).  Must match [regexp](#labels_regexp) and [values](#labels_values), if they're defined.

**Default:** `[]`

#### `labels_[label]_expression` {#labels_expression}

String, a {{% expr %}} to dynamically create labels based on other labels or issue data.  These labels are not saved with issues and are always recalculated.  Labels can reference other dynamic labels--Issu will determine the proper order to calculate labels automatically.  Issu will report errors if there is a dependency cycle.

**Default:** `""`

By default, Issu configures a few dynamic labels (`complete`, `tasks`, `tasks_done`, and `tasks_todo`).  These labels are used to track progress for issues based on Markdown tasks (`- [ ] `).

#### `labels_[label]_required` {#labels_required}

Boolean, determines if the label is required.  Issues that do not have this label will cause [linting failures]({{% ref "/docs/guides/linting-issues" %}}).

**Default:** `false`

#### `labels_[label]_regexp` {#labels_regexp}

String, a valid Regular Expression to check label values against.  Issues that do not have an appropriate value will cause [linting failures]({{% ref "/docs/guides/linting-issues" %}}).

**Default:** `""`

#### `labels_[label]_type` {#labels_type}

String, the type of the underlying Label.  See [Labels]({{% ref "/docs/guides/manage-labels" %}}) for supported values.

**Default:** `""`

#### `labels_[label]_values` {#labels_values}

Single or list of allowed string values for the label.  Issues that do not have a value from this list will cause [linting failures]({{% ref "/docs/guides/linting-issues" %}}).

**Default:** `[]`

{{% snippet config_licenseKey Issu %}}

{{% snippet config_key lintRules %}}

Map of string keys with {{% expr %}} values for evaluating whether an issue is correct.  The object passed to expressions will be a `map[string]any` of the Issue labels.  If any rule returns `true`, the issue will fail linting.

**Default:**

```json
{
  "lintRules": {
    "if status is done, all tasks are completed": "status == \"Done\" && tasks_todo != 0"
  }
}
```

By default, issues that have the label `status` with the value of `Done` but still have Markdown tasks (`- [ ]`) outstanding will fail linting.

### `list` {#list}

Configuration options for {{% cli list %}}

{{% snippet config_key "list_columns" %}}

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

{{% snippet config_key "list_filter" %}}

String, the default filter to apply when listing issues.

**Default:** `"status!=Done"`

{{% snippet config_key "list_limit" %}}

Number, the default number of issues to display when listing.

**Default:** `10`

{{% snippet config_key "list_sort" %}}

List of label names to sort by default when listing issues.  Issues will be sorted by each label sequentially.  `!` can be prepended to the label name to invert the sort.

**Default:** `[]`

### `pomodoro` {#pomodoro}

Configuration for the [Pomodoro timer]({{% ref "/docs/references/cli#pomodoro" %}}).  See [Time Tracking]{{% ref "/docs/guides/time-tracking" %}} for more information.

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
