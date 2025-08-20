---
categories:
- feature
description: Issu makes it easy to have your tasks and to-dos live within your source code.
title: Contextual Issues
type: docs
---

## Developer Experience
Stop battling with unwieldly web interfaces!  Issu ensures your source code history reflects the underlying issue changes that prompted the change.  `git diff` now includes relevant context for why the change was made, making pull requests easier to understand:

```bash
$ git diff origin/main
diff --git a/go/lib/app/app_test.go b/go/lib/app/app_test.go
index 9e2b1a66..a2706c1a 100644
--- a/go/lib/app/app_test.go
+++ b/go/lib/app/app_test.go
@@ -40,9 +40,7 @@ func TestAppInitMacros(t *testing.T) {
                        },
                        Flags: map[string]MacroFlag{
                                "a": {
-                                       Default: []string{
-                                               "1",
-                                       },
+                                       Default: "1",
                                        Options: []string{
                                                "2",
                                        },
index c91871b1..0cc01732 100644
--- a/issues/159.md
+++ b/issues/159.md
@@ -8,7 +8,10 @@
   name: 'Fix test flakes',
   priority: '4 - Gotta Have It',
   rank: '1:aaaaaaaaaababaaa',
-  status: '1 - To Do',
+  status: '4 - Done',
+  time: [
+    '2025-06-17=6m20s',
+  ],
   type: 'Feature',
 }
 ---
@@ -24,12 +27,12 @@
-- [ ] Fix test flake with app_test
+- [x] Fix test flake with app_test
```

## Linting

Issu can also lint your issues during CI/CD to ensure they have the correct metadata, and optionally add missing metadata:

```bash
$ issu lint

ERROR Linting errors found

/candiddev/engineering/issues/159.md:
    value does not match values for label: difficulty: 5 - Heroic
```
