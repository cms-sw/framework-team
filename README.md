# Project boards for CMSSW framework development

## Nomenclature

* *Campaign issue*: High-level issue, could roughly correspond to an issue in [cms-sw/cmssw](https://github.com/cms-sw/cmssw/issues). These are planned and managed in [Campaign view](https://github.com/users/makortel/projects/4)
* *Task issue*: A single work item, managed in the [Task view](https://github.com/users/makortel/projects/5)

A campaign issue is "split" into multiple Task issues, or if it can't or doesn't make sense, it can itself be a Task issue as well.

## Managing Campaign issues

* Create new issue (anyone)
  * On the right, select from "Labels" if it is a "Bug fix", "New feature", "Maintenance", or "User request"
  * From "Labels" select "Campaign" (this should lead the issue to be automatically added to the Campaign project with the "New" status)
* Assign priority (manager, or in a meeting)
  * The priority is set within the [Campaign view](https://github.com/users/makortel/projects/4) project. When the priority is set, the issue's status should be changed from "New" to "Backlog". 
    * The priority issue labels should not be set anymore
  * There are many ways to set the priority and status, some examples
    * [Backlog view](https://github.com/users/makortel/projects/4/views/1) in the project
    * [By priority view](https://github.com/users/makortel/projects/4/views/2) in the project
    * Within the issue itself (the project assignment on the right)
* Planning on Campaign issue (anyone)
  * The Campaign issue is planned with a task list in the issue description
  * Campaign issue can be assigned to a developer at this stage, but it is not necessary
* When a Campaign issue becomes relevant to be worked on (ideally in the weekly meeting, can be in between as well; mostly for manager)
  * In the [Campaign view](https://github.com/users/makortel/projects/4), move the status of the Campaign issue from "Backlog" to "Ready"
  * Assign the Campaign issue to one or more developers
  * Set the Quarter of the Campaign issue to the current quarter
  * If the Campaign issue has a task list, convert the elements of the task list that could be worked on to issues.
    * Click a circle at the right edge of the element. This creates a new issue
    * In the new issue, from "Labels" select "Task" (this should lead the issue to be automatically added to the [Task project]([url](https://github.com/users/makortel/projects/5)) with the "Ready" status)
    * Set the Quarter of the Task issue to the current quarter
  * If the Campaign issue consists from a single task, add the "Task" label to the Campaign issue, which then becomes a Task issue as well
* When the work on a Campaign issue actually starts
  * In the [Campaign view](https://github.com/users/makortel/projects/4), move the status of the Campaign issue from "Ready" to "In progress"
  * Set the "Began" date to the date when the work started
  * Set the "Finished" date to the estimated end date
    * The estimate can be crude, e.g. end of current month, end of current quarter, end of current year etc.
* When the last Task issue of the Campaign issue has been closed
  * Close the Campaign issue (the status is automatically set to "Done")
  * Set the "Finished" date to the date when the work was finished (e.g. last PR was merged, documentation was written, presentation was given)
* If a Campaign issue becomes dormant, e.g. no work in a few weeks
  * In the [Campaign view](https://github.com/users/makortel/projects/4), move the status of the Campaign issue from "In progress" to "Paused"
  * The paused Campaign issues should be revisited regularly, e.g. to
    * Decide if/when the work could continue (keep the issue paused), or
    * If the remaining work is not that relevant/important anymore, in which case the Campaign issue should be split
      * Move the remaining tasks into a new Campaign issue with "Backlog" status and proper prioritization
      * Close the old Campaign issue
      * Set the "Finished" date to the the date when the work was finished

## Working on Task issues

* When a developer starts working on a Task issue with "Ready" status, developer changes the status to "In progress"
  * If this is the first task of a Campaign to be worked on, the status of the Campaign issue should be updated as well (see above)
* If for any reason the work on a task stalls for sufficiently long period of time (say more than week), set the Task issue status to "Paused"
* Upon completion of a task
  * If the deliverable is a Pull Request
    * Change the Task issue status to "In review"
    * Link the PR to the task issue with one of [the keywords in the PR description](https://docs.github.com/en/github/managing-your-work-on-github/linking-a-pull-request-to-an-issue#linking-a-pull-request-to-an-issue-using-a-keyword). While merging of the PR will not cause the Task issue to be automatically closed (because of the PR repository being in different organization than the project), having the Task issue linked to the PR is helpful.
    * When the PR is merged, either the developer or the manager closes the Task issue.
  * Otherwies, close the Task issue. The issue will be automatically moved to the "Done" column of the projeect board.
* When the last Task issue of the Campaign issue is closed, the Campaign issue needs to be closed too (see above).

## What to do when new quarter starts?

* In [Campaign view](https://github.com/users/makortel/projects/4), update the quarter of all non-Done Campaign issues that had the quarter set to the previous quarter
* In [Task view](https://github.com/users/makortel/projects/5), update the quarter of all non-Done Task issues that had the quarter set to the previous quarter

## Campaign statuses

* **New**: Campaign issue has been newly added to the project, priority has not yet been assigned
* **Backlog**: Campaign issue's priority has been assigned, but is not planned to be worked on in the current quarter
* **Ready**: Campaign issue is planned to be worked on, and in principle is open for anyone to work on, but the work has not started yet
* **Paused**: Work was started, but got stopped for long time for any reason. Need to be followed up periodically.
* **In progress**: Campaign is being worked on
* **Done**: Campaign has been finished

## Campaign sizes

The campaign size is a very crude estimate of time needed (assuming FTE)

* **Tiny**: up to a day
* **Small**: up to a week
* **Medium**: up to a month
* **Large**: up to half a year
* **X-Large**:: more than half a year

## Labels

Label colors have been created with https://colorbrewer2.org/

* ~~Priority: Breaking, High impact, Promised, Annoyance, Wishlist; 5-class YlOrRd~~ (not to be used anymore)
* Kind: Bug, Optimization, Maintenance, New feature, Tool, User request, Documentation, R&D; 8-class Blues
* Type: Campaign, Task, Waiting; 3-class Greens
* Overarching directive: Throughput, Threading efficiency, Heterogeneous computing, Code modernization; 4-class Purples

