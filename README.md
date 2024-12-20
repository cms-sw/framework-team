# Project boards for CMSSW framework development

## Nomenclature

* *Task issue*: A single work item, managed in the [Tasks project](https://github.com/orgs/cms-sw/projects/10).
* *Activity issue*: High-level issue, could roughly correspond to an issue in [cms-sw/cmssw](https://github.com/cms-sw/cmssw/issues). These are planned and managed in [Activities project](https://github.com/orgs/cms-sw/projects/11)
  * Consists of many Task issues, or if it can't or doesn't make sense, it can itself be a Task issue as well.
* *Umbrella issue*: Even higher-level issue to collect information on many related Activities. There is no specific planning for Umbrellas.
  * These are long-lasting development topics that consist of multiple Activities
  * Must have an ending, which makes Umbrella distinct from Overarching themes

The overarching themes are a rough classification of activities, and do not have a clear ending.

Maintenance Tasks are not part of any Activity, but have `Task` and `Maintenance` labels.

Documentation Tasks can be part of an Activity, or separate to any Activities. In either case, they have `Task` and `Documentation` labels.

## Activity properties in the [Activities project](https://github.com/orgs/cms-sw/projects/11)

Each activity should be assigned a priority. Each activity may also
have a size, that is a very crude estimate` of the FTE time needed
(will probably be incorrect, but that's life). The names of both
priorities and sizes should be self-explanatory.

### Status

* **New**: Activity issue has been newly added to the project, priority has not yet been assigned
* **Backlog**: Activity issue's priority has been assigned, but is not planned to be worked on in the current quarter
* **Ready**: Activity issue is planned to be worked on, and in principle is open for anyone to work on, but the work has not started yet
* **Paused**: Work was started, but got stopped for long time for any reason. Need to be followed up periodically.
* **In progress**: Activity is being worked on
* **Done**: Activity has been finished

## Labels

Label colors have been created with https://colorbrewer2.org/

* ~~Priority: Breaking, High impact, Promised, Annoyance, Wishlist; 5-class YlOrRd~~ (not to be used anymore, to be removed)
* Kind: Bug, Optimization, Maintenance, New feature, Tool, User request, Documentation, R&D; 8-class Blues
* Type: Umbrella, Activity, Task; 3-class Greens
* Overarching theme: Throughput, Threading efficiency, Heterogeneous computing, Code modernization; 4-class Purples

## Walkthroughs

* [Creating a new Activity](New_activity.md)
* [Updating the plan of an Activity](Activity_plan_update.md)
* [Starting to work on a Task](Task_begin.md)
* [Maintenance fix or documentation update](Task_maintenance_documentation.md)
* [Finalizing an existing Task](Task_finish.md)
* [Bookkeeping backport PRs](Task_backport_pr.md)
* [Adding oneself to an existing Activity](Activity_add_oneself.md)
* [Change status of an Activity or a Task](Activity_task_change_status.md)

## Reference

### Managing Activity issues

* Create new issue (anyone)
  * On the right, select from "Labels" if it is a "Bug fix", "New feature", "Maintenance", or "User request"
  * From "Labels" select "Activity" (this should lead the issue to be automatically added to the Activity project with the "New" status)
* Assign priority (manager, or in a meeting)
  * The priority is set within the [Activities project](https://github.com/orgs/cms-sw/projects/11). When the priority is set, the issue's status should be changed from "New" to "Backlog". 
    * The priority issue labels should not be set anymore
  * There are many ways to set the priority and status, some examples
    * [Backlog view](https://github.com/orgs/cms-sw/projects/11/views/1) in the project
    * [By priority view](https://github.com/orgs/cms-sw/projects/11/views/2) in the project
    * Within the issue itself (the project assignment on the right)
* Planning on Activity issue (anyone)
  * The Activity issue is planned with a task list in the issue description
  * An Activity issue can be assigned to a developer at this stage, but it is not necessary
* When an Activity issue becomes relevant to be worked on (ideally in the weekly meeting, can be in between as well; mostly for manager)
  * In the [Activities project](https://github.com/orgs/cms-sw/projects/11), move the status of the Activity issue from "Backlog" to "Ready"
  * Assign the Activity issue to one or more developers
  * Set the Quarter of the Activity issue to the current quarter
  * If the Activity issue has a task list, convert the elements of the task list that could be worked on to issues.
    * Click a circle at the right edge of the element. This creates a new issue
    * In the new issue, from "Labels" select "Task" (this should lead the issue to be automatically added to the [Tasks project](https://github.com/orgs/cms-sw/projects/10) with the "Ready" status)
    * Set the Quarter of the Task issue to the current quarter
  * If the Activity issue consists from a single task, add the "Task" label to the Activity issue, which then becomes a Task issue as well
* When the work on a Activity issue actually starts
  * In the [Activities project](https://github.com/orgs/cms-sw/projects/11), move the status of the Activity issue from "Ready" to "In progress"
  * Set the "Began" date to the date when the work started
  * Set the "Finished" date to the estimated end date
    * The estimate can be crude, e.g. end of current month, end of current quarter, end of current year etc.
* When the last Task issue of the Activity issue has been closed
  * Close the Activity issue (the status is automatically set to "Done")
  * Set the "Finished" date to the date when the work was finished (e.g. last PR was merged, documentation was written, presentation was given)
* If a Activity issue becomes dormant, e.g. no work in a few weeks
  * In the [Activities project](https://github.com/orgs/cms-sw/projects/11), move the status of the Activity issue from "In progress" to "Paused"
  * The paused Activity issues should be revisited regularly, e.g. to
    * Decide if/when the work could continue (keep the issue paused), or
    * If the remaining work is not that relevant/important anymore, in which case the Activity issue should be split
      * Move the remaining tasks into a new Activity issue with "Backlog" status and proper prioritization
      * Close the old Activity issue
      * Set the "Finished" date to the the date when the work was finished

### Working on Task issues

* When a developer starts working on a Task issue with "Ready" status, developer changes the status to "In progress"
  * If this is the first task of an Activity to be worked on, the status of the Activity issue should be updated as well (see above)
* If for any reason the work on a task stalls for sufficiently long period of time (say more than week), set the Task issue status to "Paused"
* Upon completion of a task
  * If the deliverable is a Pull Request
    * Change the Task issue status to "In review"
    * Link the PR to the task issue with one of [the keywords in the PR description](https://docs.github.com/en/github/managing-your-work-on-github/linking-a-pull-request-to-an-issue#linking-a-pull-request-to-an-issue-using-a-keyword). While merging of the PR will not cause the Task issue to be automatically closed (because of the PR repository being in different organization than the project), having the Task issue linked to the PR is helpful.
    * When the PR is merged, either the developer or the manager closes the Task issue.
  * Otherwies, close the Task issue. The issue will be automatically moved to the "Done" column of the projeect board.
* When the last Task issue of the Activity issue is closed, the Activity issue needs to be closed too (see above).

### What to do when new quarter starts?

* In the [Activities project](https://github.com/orgs/cms-sw/projects/11), update the quarter of all non-Done Activity issues that had the quarter set to the previous quarter
* In the [Tasks project](https://github.com/orgs/cms-sw/projects/10), update the quarter of all non-Done Task issues that had the quarter set to the previous quarter

### Updating framework team group members

Access to the [`framework-team` repository](https://github.com/cms-sw/framework-team) and [Activities](https://github.com/orgs/cms-sw/projects/11) and [Tasks](https://github.com/orgs/cms-sw/projects/10) projects is controlled via GitHub teams:
* Members of [`core-l2`](https://github.com/orgs/cms-sw/teams/core-team) team are the admins
* Members of [`core-team`](https://github.com/orgs/cms-sw/teams/core-team) team have write access (e.g. can open issues and change their states in the projects)
* Everyone else (including public) has read access

The teams are updated via PRs to [`cms-bot`](https://github.com/cms-sw/cms-bot), see e.g. [cms-bot#1245](https://github.com/cms-sw/cms-bot/pull/1245), [cms-bot#2330](https://github.com/cms-sw/cms-bot/pull/2330), [cms-bot#2332](https://github.com/cms-sw/cms-bot/pull/2332). GitHub then sends a confirmation message to the added users that they should accept in order to become members of the team.

## Earlier project instances

* Q1 2021
  * [Activities](https://github.com/cms-sw/framework-team/projects/1)
  * [Tasks](https://github.com/cms-sw/framework-team/projects/2)
* Q2 2022 - Q2 2023
  * [Activities](https://github.com/cms-sw/framework-team/projects/4)
  * [Tasks](https://github.com/cms-sw/framework-team/projects/6)
* From Q3 2023 to Q2 2024
  * [Activities](https://github.com/users/makortel/projects/4)
  * [Tasks](https://github.com/users/makortel/projects/5)
