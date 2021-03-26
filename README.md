# Beta test for CMSSW framework project boards

## Nomenclature

* *Campaign issue*: High-level issue, could roughly correspond to an issue in [cms-sw/cmss](https://github.com/cms-sw/cmssw/issues). These are planned and managed in [Campaign view](https://github.com/makortel/framework/projects/1)
* *Task issue*: A single work item, managed in the [quarterly project boards](https://github.com/makortel/framework/projects/1)

A campaign issue is "split" into multiple Task issues, or if it can't or doesn't make sense, it can itself be a Task issue as well.

## Creating issues

* Create new issue (anyone)
  * On the right, select from "Labels" if it is a "Bug fix", "New feature", "Maintenance", or "User request"
  * From "Labels" select "Campaign"
  * From "Projects" select "Campaign view" (it should automatically go to the "Priority not yet assigned" column)
* Assign priority (manager, or in a meeting)
  * Go to the [Campaign view](https://github.com/makortel/framework/projects/1) project board
  * Set the priority label
  * Move the card to the corresponding priority column
    * If "Critical", move to the column of current quarter
* Planning on Campaign issue (anyone)
  * As long as a Campaign issue sits in the priority column, it can be planned with a task list in the issue description. The number of items in the task list can be used to estimate the effort needed to complete the campaign.
  * Campaign issue can be assigned to a developer at this stage, but it is not necessary
* When we decide that we start working on a Campaign issue (ideally in the weekly meeting, can be in between as well; mostly for manager)
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

* Priority: Breaking, High impact, Promised, Annoyance, Wishlist; 5-class YlOrRd
* Kind: Bug, Maintenance, New feature, Tool, User request, R&D; 6-class Blues
* Type: Campaign, Task, Waiting; 3-class Greens
* Overarching directive: Throughput, Threading efficiency, Heterogeneous computing, Code modernization; 4-class Purples


## Automation possibilities

### Creation of task issues from the campaign issue

The creation of task issues from the campaing issue could be largely automated:
* Create a Milestone with the same name as the Campaign issue
  * In the Milestone description, add text `Tracking #<campaign issue number>`
  * In the Campaign issue description, add text `Progress tracked in <link to milestone>`
* For each (top-level) item in the task list in the Campaign issue task list create a new (Task) issue
  * Title of the Task issue should come from the content of the task list item
     * Could be useful to have an option to add an arbitrary short prefix to the Task issue title
  * Set priority label to be the same as in the Campaign issue
  * Add "Task" label
  * Set the assignees to be the same as in the Campaign issue (if any)
  * Add the Task issue to the project board of the latest quarter ("To do" column)
  * Add the Task issue to the Milestone corresponding the Campaign issue
  * In the Task issue description, add `Part of #<campaign issue number>`.
  * If the item in the Campaign issue task list has sub-items, copy the item and the sub-items to a task list in the Task issue description
* Remove the task list from the Campaign issue description

### Make priority labels follow the assignment in project board columns

It would make life a bit easier if the priority labels would be assigned automatically based on the low/medium/high priority column (in the [Campaign view](https://github.com/makortel/framework/projects/1)) in which an issue is moved to. If an issue is moved from any of these to a quarterly column, the priority label should not be changed.
