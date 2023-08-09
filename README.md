# Project boards for CMSSW framework development

## Nomenclature

* *Campaign issue*: High-level issue, could roughly correspond to an issue in [cms-sw/cmssw](https://github.com/cms-sw/cmssw/issues). These are planned and managed in [Campaign view](https://github.com/users/makortel/projects/4)
* *Task issue*: A single work item, managed in the [Task view](https://github.com/users/makortel/projects/5)

A campaign issue is "split" into multiple Task issues, or if it can't or doesn't make sense, it can itself be a Task issue as well.

## Creating Campaign issues

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
* When we decide that we start working on a Campaign issue (ideally in the weekly meeting, can be in between as well; mostly for manager) (TODO from here downwards)
  * In the [Campaign view](https://github.com/makortel/framework/projects/1), the Campaign issue is moved from the priority column to the column of that quarter
  * Assign the Campaign issue to one or more developers
  * If the Campaign issue has a task list (see automation below)
    * Create a milestone with the same name as the Campaign issue, link the two together
    * Create a new Task issue for every item in the task list
      * Make sure each task has a descriptive title also outside of the Campaign issue context
      * Set priority label to be the same as in the Campaign issue
      * Add "Task" label
      * Set the assignees to be the same as in the Campaign issue (or fine-tune manually)
      * Add the Task issue to the project board of the current quarter (should go automatically to "To do" column)
      * Add the Task issue to the milestone corresponding the Campaign issue
  * If the Campaign issue does not have a task list
      * Add "Task" label
      * Add the issue to the project board of the current quarter (should go automatically to "To do" column)

## Working on Task issues

* When a developer starts working on a task in "To do" column, developer moves it to "In progress" column
* If for any reason the work on a task stalls for sufficiently long period of time (say more than week), move the issue to "Paused" column
* Upon completion of a task
  * If the deliverable is a Pull Request, move the Task issue to "In review" column, and make sure to link the Task issue to the PR with one of [the keywords in the PR description](https://docs.github.com/en/github/managing-your-work-on-github/linking-a-pull-request-to-an-issue#linking-a-pull-request-to-an-issue-using-a-keyword). Then the merge of the PR will automatically close the Task issue.
  * Otherwies, close the Task issue. The issue will be automatically moved to the "Done" column of the projeect board.
* When manager notices that a milestone with associated Campaign issue has been completed, the manager closes both the milestone and the associated Campaign issue

## Labels

Label colors have been created with https://colorbrewer2.org/

* ~~Priority: Breaking, High impact, Promised, Annoyance, Wishlist; 5-class YlOrRd~~ (not to be used anymore)
* Kind: Bug, Optimization, Maintenance, New feature, Tool, User request, Documentation, R&D; 8-class Blues
* Type: Campaign, Task, Waiting; 3-class Greens
* Overarching directive: Throughput, Threading efficiency, Heterogeneous computing, Code modernization; 4-class Purples

## Project sizes

TODO
