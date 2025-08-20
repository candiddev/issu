---
categories:
- guide
description: How to lint issues
title: Linting Issues
---

Issu can lint issue files to ensure the frontmatter labels are correct and consistent.

## Performing Linting

You can lint all files under the {{% config issuesPath %}} using {{% cli lint %}}.  Lint will scan all files, check their labels against {{% config labels %}}, and exit 1 if there are any issues with them:

```bash
$ issu lint

ERROR Linting errors found

/candiddev/engineering/issues/159.md:
    value does not match values for label: difficulty: 5 - Heroic
```

**For Continuous Delivery/Continuous Integration Usage**, it's highly recommended to run linting for every {{% config issuesPath %}} change.

## Fixing Linting Issues

If the linting issue is due to a missing label, and that label has a default, Issu can automatically fix the problem by [Organizing the Labels]({{% ref "/docs/guides/manage-labels#organize-labels" %}}){{% cli org %}}.  This command will .
