---
categories:
- reference
description: Reference documentation for Issu's CLI
title: CLI
---

{{% snippet cli_arguments %}}

{{% snippet cli_commands Issu %}}

### `add`

Create a new issue, optionally specifying labels to include with it.

### `after`

Move an issue's priority after another issue's priority.

{{% cli_autocomplete %}}

### `before`

Move an issue's priority before another issue's priority.

{{% snippet cli_config %}}

### `del`

Delete issues matching a filter.

{{% snippet cli_docs %}}

### `edit`

Interactively edit issues matching a filter

{{% snippet cli_eula Issu %}}

{{% snippet cli_jq %}}

### `label`

List all known labels.

### `lint`

Lint issues and exit if errors are found.  Useful for CI/CD pipelines.

### `list`

List issues as a table or a JSON array.

### `org`

Organize issues by adding default labels and normalizing positions.

### `pom`

Start a Pomodoro timer and track the time against an issue.

### `set`

Set a label and value for issues that match a filter.

{{% cli_version %}}
