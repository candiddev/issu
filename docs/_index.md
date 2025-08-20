---
description: Issu is the easiest way to manage issues from within your code repositories.  Create, label, and organize your issues in whatever way makes you the most productive.  Issu makes it easy to maintain context within your repositories.
title: Issu | Track Tasks and Issues in Your Code Repos
---

{{% blocks/section color="white" %}}
<h1 style="border-bottom: 2px solid var(--bs-orange)"><b>Build Better, Track Smarter with Issu</b></h1>
<h1>CLI Issue Management for Code Repositories</h1>
<div style="align-items: center; display: flex; justify-content: center; padding-top: 40px; width 100%">
  <a class="button button--orange" href="/docs/guides/install-issu">Download</a>
</div>
{{% /blocks/section %}}

{{< blocks/section color="white" type=row >}}
{{% blocks/feature icon="fa-file-code" title="Contextual Issue Tracking" %}}
Issu seamlessly integrates your tasks and to-dos directly within your source code repositories. Every issue lives alongside the code it impacts, facilitating better understanding and pull request reviews.
{{% /blocks/feature %}}

{{% blocks/feature icon="fa-brain" title="AI-Powered Issue Resolution" %}}
Issu’s design lets GenAI agents leverage rich metadata and code context for smarter fixes and automated tasks – boosting your productivity.
{{% /blocks/feature %}}

{{% blocks/feature icon="fa-code" title="Simple Developer Experience" %}}
Easily expose services with one-line CLI or deploy reusable proxy configurations within your codebase and developer environments.
{{% /blocks/feature %}}

{{% blocks/feature icon="fa-stopwatch" title="Built-in Pomodoro & Timekeeping" %}}
Boost your productivity with Issu’s Pomodoro timer and automatic timekeeping – seamlessly logging time against each issue you’re working on.
{{% /blocks/feature %}}

{{< /blocks/section >}}

{{< blocks/section color=white >}}
<h2 style="border-bottom: 2px solid var(--bs-orange)"><b>CLI-based, Markdown Powered</b></h2>
<h3>Manage markdown files within your code repositories</h3>
{{< highlight markdown>}}
---
{
  created: '2025-01-28',
  name: 'Issu GA',
  rank: '1',
  status: 'In Progress',
  type: 'Feature',
}
---

# 159 - Issu GA

## Pre-GA

- [x] Design logo
- [x] Finalize MVP
- [ ] Create landing pages and website
- [ ] Setup release pipeline

## Post-GA

- [ ] Setup GitHub repository

{{< /highlight >}}

<h2 style="border-bottom: 2px solid var(--bs-orange); padding-top: 50px"><b>Organize and Prioritize</b></h2>
<h3>Use labels to filter, group, and plan your work</h3>
{{< highlight bash>}}
RANK   ID    NAME                                                                                          TIME
----   ---   -------------------------------------------------------------------------------------------   -------
1      1     Bugs/Small Features                                                                           
11     159   Issu GA                                                                                       1h6m20s
15     23    As a user, I want to revamp Homechart backups so they're more useful                          
16     69    As a user, I want to have disposable budget categories so I can save up for specific things   
17     59    As a user, I want Homechart to be an OIDC provider so I can use it for SSO                    
19     8     As a user, I want to replace Makefile with Etcha so I can use Etcha for everything            
30     173   As a user, I want to bring my own templates to YAML8n so I can use it with anything
35     171   As a user, I want to have expirations on Inventory Items so I can track when to replace things
{{< /highlight >}}

<h2 style="border-bottom: 2px solid var(--bs-orange); padding-top: 50px"><b>Track Time While Working Hard</b></h2>
<h3>Customizable Pomodoro timer tracks time and schedules breaks</h3>
{{< highlight bash >}}
$ issu pomodoro 159
Jun 1 09:20:00 Pomodoro 1/4 (20m)
Jun 1 09:40:00 Short Break 1/3 (5m)
Jun 1 09:45:00 Pomodoro 2/4 (20m)
Jun 1 10:05:00 Short Break 2/3 (4m)
Jun 1 10:09:00 Pomodoro 3/4 (15m)
Jun 1 10:24:00 Short Break 3/3 (3m)
Jun 1 10:27:00 Pomodoro 4/4 (20m)
Jun 1 10:47:00 Long Break (3s)
Remaining: 19m57s
Start Pomodoro? [ENTER]
{{< /highlight >}}
{{< /blocks/section >}}
