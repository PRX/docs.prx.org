# Overview
Issues are filed in GitHub to the corresponding and related repository. We use [ZenHub](https://www.zenhub.io/) boards to view and manage the issues through their workflow. After installing the ZenHub Chrome Extension a new icon should show up on the GitHub repository, the ZenHub board icon should appear below the `<>` code icon. ZenHub uses "Pipelines" to help organize issues.

We are following the process described here: https://www.zenhub.io/blog/how-the-zenhub-team-uses-zenhub-boards-on-github/ This document will only cover differences, clarifications or modifications that are specific to PRX.

### Issue Pipelines
We use the same pipelines as ZenHub:
* New Issues --> Ice Box | Backlog <--> In Progress <--> Review/QA --> Done --> Closed

### How do I create a New Issue?
Go to the appropriate repository and select "New Issue". Provide a meaningful title and enough of a description to help people review and understand the issue for triage. When New Issues are created they **MUST be associated with the Global** milestone, and **SHOULD be unassigned**. The engineering team will review the New Issues weekly and either move them into Backlog for more detail, estimation, prioritizing and planning for a milestone. Sometimes issues are duplicates of existing issues, we'll close those out and ideally reference the existing issue.

Sometimes issues just aren't clear enough, are an idea that we don't want to lose or aren't yet high enough priority to move into the **Backlog**. We use the **Ice Box** as a place to hold onto those issues.

### Need input or review on an issue?
Issues that might require more information should have the label "reviewplx" added to them. We use @mentions to draw the attention of people to the issue. 

### What is a Milestone?
Issues that are at the top of the Backlog are grouped into a Milestone. Some teams use Milestones  to organize Sprints that are chunked by time. We use Milestones to group related issues to a customer business value objective so that we may track the progress toward completion. Milestones should not be longer than a few weeks in length and should have due dates associated with them. We use the issue effort estimates to help determine what we can accomplish in a Milestone, or if it needs to be split.

### How do I check on the status of an issue or Milestone?
Milestones have the following states:
* ON HOLD
* EXPECTED START DATE
* IN PROGRESS

Each milestone description should link to an issue that acts as an overview for the milestone. These issues have the label "milestone goal" applied. The best way to determine how much progress has been made in a milestone is to view is sorted by [most complete](https://github.com/PRX/www.prx.org/milestones?direction=desc&sort=completeness&state=open).

### What does it mean for an issue to be in the Done pipeline?
The issue has been deployed to production and customers are deriving the 

### Closed issues

### How do I know if a ticket has been deployed?
Deployment notifications are sent as messages to the #deploys Slack channel with the date and time of deployment. @farski did we come to some ~final way to determine this?

### How are issues assigned?

### How do we use estimates?

## Issue Labels
### Milestone Goal
Used to identify the issue that provides a high level overview for a milestone.
### reviewplx
Waiting on input from the current assignee. If you need someone to review 
### estimateplx
Issues with this label are needing an effort estimate from the current assignee.