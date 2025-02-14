# Project boards for CMSSW framework development

## Nomenclature

* *Category issue*: Category is a loose collection of related Objective or other Category issues. There is no specific planning for Categories. Use of Categories is optional.
  * These are long-lasting development topics that consist multiple Objectives
  * Must have an ending, which makes Categories distinct from Overarching themes (see below)
* *Objective issue*: High-level issue, could roughly correspond to an issue in [cms-sw/cmssw](https://github.com/cms-sw/cmssw/issues). These are planned and managed in [Objectives project](https://github.com/orgs/cms-sw/projects/11)
  * Consists of many Task issues, or if it can't or doesn't make sense, it can itself be a Task issue as well.
  * Can consists of zero or more Aspect issues. If an Objective contains exactly one Aspect issue, the Objective should contain also Task issue(s) directly.
  * A Pull Request can be linked to (i.e. the PR can close) an Objective issue, if none of the contained Aspect or Task issues are linked to any PR.
* *Aspect issue*: Optional sub-division of an Objective, that consists of multiple Tasks. There is no specific planning for Aspects.
  * A Pull Request can be linkd to (i.e. the PR can close) an Aspect issue, if none of the contained Task issues are linked to any PR.
* *Task issue*: A single work item, managed in the [Tasks project](https://github.com/orgs/cms-sw/projects/10).
  * Ideally something taking a few hours to a week of wall clock time. If a task takes longer than a week, think if it could be split into smaller pieces that would make sense.


The overarching themes are a rough classification of Objectives or Categories, and do not have a clear ending.

Maintenance Tasks are not part of any Objective, but have `Task` and `Maintenance` labels.

Documentation Tasks can be part of an Objective or Aspect, or they can separate from any Objectives. In either case, they have `Task` and `Documentation` labels.

## Objective properties in the [Objectives project](https://github.com/orgs/cms-sw/projects/11)

Each objective should be assigned an importance, and ideally a
needed-by date. Each objective may also have a size, that is a very
crude estimate of the FTE time needed (will probably be incorrect,
but that's life). The names of both importances and sizes should be
self-explanatory.

### Status

* **New**: Objective issue has been newly added to the project, importance has not yet been assigned
* **Backlog**: Objective issue's importance has been assigned, but is not planned to be worked on in the current quarter
* **Ready**: Objective issue is planned to be worked on, and in principle is open for anyone to work on, but the work has not started yet
* **Paused**: Work was started, but got stopped for long time for any reason. Need to be followed up periodically.
* **In progress**: Objective is being worked on
* **Done**: Objective has been finished

## Labels

Label colors have been created with https://colorbrewer2.org/

* Kind: Bug, Optimization, Maintenance, New feature, Tool, User request, Documentation, R&D; 8-class Blues
* Type: Category, Objective, Aspect, Task; 4-class Greens
* Overarching theme: Throughput, Threading efficiency, Heterogeneous computing, Code modernization; 4-class Purples

## Walkthroughs

* [Creating a new Activity](New_activity.md) (needs to be updated)
* [Updating the plan of an Activity](Activity_plan_update.md) (needs to be updated)
* [Starting to work on a Task](Task_begin.md) (needs to be updated)
* [Maintenance fix or documentation update](Task_maintenance_documentation.md) (needs to be updated)
* [Finalizing an existing Task](Task_finish.md) (needs to be updated)
* [Bookkeeping backport PRs](Task_backport_pr.md) (needs to be updated)
* [Adding oneself to an existing Activity](Activity_add_oneself.md) (needs to be updated)
* [Change status of an Activity or a Task](Activity_task_change_status.md) (needs to be updated)

## Reference

### Managing Objective issues

* Create new issue (anyone)
  * On the right, select from "Labels" if it is a "Bug fix", "New feature", "Maintenance", or "User request"
  * From "Labels" select "Objective" (this should lead the issue to be automatically added to the Objective project with the "New" status)
* Assign importance (manager, or in a meeting)
  * The importance is set within the [Objectives project](https://github.com/orgs/cms-sw/projects/11). When the importance is set, the issue's status should be changed from "New" to "Backlog". 
    * The importance issue labels should not be set anymore
  * There are many ways to set the importance and status, some examples
    * [Backlog view](https://github.com/orgs/cms-sw/projects/11/views/1) in the project
    * [By importance view](https://github.com/orgs/cms-sw/projects/11/views/2) in the project
    * Within the issue itself (the project assignment on the right)
* Planning on Objective issue (anyone)
  * The Objective issue is planned with a task list in the issue description
  * An Objective issue can be assigned to a developer at this stage, but it is not necessary
* When an Objective issue becomes relevant to be worked on (ideally in the weekly meeting, can be in between as well; mostly for manager)
  * In the [Objectives project](https://github.com/orgs/cms-sw/projects/11), move the status of the Objective issue from "Backlog" to "Ready"
  * Assign the Objective issue to one or more developers
  * Set the Quarter of the Objective issue to the current quarter
  * If the Objective issue has a task list, convert the elements of the task list that could be worked on to issues.
    * Click a circle at the right edge of the element. This creates a new issue
    * In the new issue, from "Labels" select "Task" (this should lead the issue to be automatically added to the [Tasks project](https://github.com/orgs/cms-sw/projects/10) with the "Ready" status)
    * Set the Quarter of the Task issue to the current quarter
  * If the Objective issue consists from a single task, add the "Task" label to the Objective issue, which then becomes a Task issue as well
* When the work on a Objective issue actually starts
  * In the [Objectives project](https://github.com/orgs/cms-sw/projects/11), move the status of the Objective issue from "Ready" to "In progress"
  * Set the "Began" date to the date when the work started
  * Set the "Finished" date to the estimated end date
    * The estimate can be crude, e.g. end of current month, end of current quarter, end of current year etc.
* When the last Task issue of the Objective issue has been closed
  * Close the Objective issue (the status is automatically set to "Done")
  * Set the "Finished" date to the date when the work was finished (e.g. last PR was merged, documentation was written, presentation was given)
* If a Objective issue becomes dormant, e.g. no work in a few weeks
  * In the [Objectives project](https://github.com/orgs/cms-sw/projects/11), move the status of the Objective issue from "In progress" to "Paused"
  * The paused Objective issues should be revisited regularly, e.g. to
    * Decide if/when the work could continue (keep the issue paused), or
    * If the remaining work is not that relevant/important anymore, in which case the Objective issue should be split
      * Move the remaining tasks into a new Objective issue with "Backlog" status and proper prioritization
      * Close the old Objective issue
      * Set the "Finished" date to the the date when the work was finished

### Working on Task issues

* When a developer starts working on a Task issue with "Ready" status, developer changes the status to "In progress"
  * If this is the first task of an Objective to be worked on, the status of the Objective issue should be updated as well (see above)
* If for any reason the work on a task stalls for sufficiently long period of time (say more than week), set the Task issue status to "Paused"
* Upon completion of a task
  * If the deliverable is a Pull Request
    * Change the Task issue status to "In review"
    * See below about linking the Pull Request to the Task issue
    * When the PR is merged, either the developer or the manager closes the Task issue.
  * Otherwies, close the Task issue. The issue will be automatically moved to the "Done" column of the projeect board.
* When the last Task issue of the Objective issue is closed, the Objective issue needs to be closed too (see above).

### Linking Pull Requests to Objective, Aspect, or Task issues

If the deliverable of an Objective, an Aspect, or a Task is a single Pull Request, link the PR to the Objective/Aspect/Task issue with one of [the keywords in the PR description](https://docs.github.com/en/github/managing-your-work-on-github/linking-a-pull-request-to-an-issue#linking-a-pull-request-to-an-issue-using-a-keyword). If the PR is in a repository in the [cms-sw](https://github.com/cms-sw) organization, the merging of the PR will (in some situations) automatically close the issue. Even when the PR does not automatically close the issue, linking the PR and the issue is helpful

### What to do when new quarter starts?

* In the [Objectives project](https://github.com/orgs/cms-sw/projects/11), update the quarter of all non-Done Objective issues that had the quarter set to the previous quarter
* In the [Tasks project](https://github.com/orgs/cms-sw/projects/10), update the quarter of all non-Done Task issues that had the quarter set to the previous quarter

### Updating framework team group members

Access to the [`framework-team` repository](https://github.com/cms-sw/framework-team) and [Objectives](https://github.com/orgs/cms-sw/projects/11) and [Tasks](https://github.com/orgs/cms-sw/projects/10) projects is controlled via GitHub teams:
* Members of [`core-l2`](https://github.com/orgs/cms-sw/teams/core-team) team are the admins
* Members of [`core-team`](https://github.com/orgs/cms-sw/teams/core-team) team have write access (e.g. can open issues and change their states in the projects)
* Everyone else (including public) has read access

The teams are updated via PRs to [`cms-bot`](https://github.com/cms-sw/cms-bot), see e.g. [cms-bot#1245](https://github.com/cms-sw/cms-bot/pull/1245), [cms-bot#2330](https://github.com/cms-sw/cms-bot/pull/2330), [cms-bot#2332](https://github.com/cms-sw/cms-bot/pull/2332). GitHub then sends a confirmation message to the added users that they should accept in order to become members of the team.

## Earlier project instances

* Q1 2021
  * [Activities](https://github.com/cms-sw/framework-team/projects/1) (now called Objectives)
  * [Tasks](https://github.com/cms-sw/framework-team/projects/2)
* Q2 2022 - Q2 2023
  * [Activities](https://github.com/cms-sw/framework-team/projects/4) (now called Objectives)
  * [Tasks](https://github.com/cms-sw/framework-team/projects/6)
* From Q3 2023 to Q2 2024
  * [Activities](https://github.com/users/makortel/projects/4) (now called Objectives)
  * [Tasks](https://github.com/users/makortel/projects/5)
