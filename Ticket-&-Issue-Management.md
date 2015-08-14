# Overview
Issues are filed in GitHub to the corresponding and related repository. We use [ZenHub](https://www.zenhub.io/) boards to view and manage the issues through their workflow. After installing the ZenHub Chrome Extension a new icon should show up on the GitHub repository, the ZenHub board icon should appear below the < > code icon. ZenHub uses "Pipelines" to help organize issues.

We are following the process described here: https://www.zenhub.io/blog/how-the-zenhub-team-uses-zenhub-boards-on-github/ This document will only cover differences, clarifications or modifications that are specific to PRX.

### Issue Pipelines
We use the same pipelines as ZenHub:
* New Issues --> Ice Box --> Backlog <--> In Progress <--> Review/QA --> Done --> Closed

### How do I create a New Issue?
Go to the appropriate repository and select "New Issue". Provide a meaningful title and enough of a description to help people review and understand the issue for triage. When New Issues are created they **MUST be associated with the Global**, and **should NOT be assigned to anyone**. The engineering team will review the New Issues and either move them into Backlog for estimation, fleshing out and planning for a milestone. Sometimes issues are duplicates of existing issues, we'll close those out and ideally reference the existing issue.

Sometimes issues just aren't clear enough, are an idea that we don't want to lose or aren't yet high enough priority to move into the **Backlog**. We use the **Ice Box** as a place to hold onto those issues.

### Need input or review on an issue?
Issues that might require more information should have the label "reviewplx" added to them. We use @mentions to draw the attention of people to the issue. 

### What is a Milestone?
Issues that are at the top of the Backlog are grouped into a Milestone. Some organizations use Milestones as Sprints and they are used to chunk work on issues into one week or two week periods. We don't operate that way.

We use Milestones to group issues that relate to a common business value so that we may track the progress toward completion. Milestones should not be longer than a few weeks in length and should have due dates associated with them. We use the issue effort estimates to help determine how long a Milestone is, and what might exist in a Milestone.

### What does it mean for an issue to be in the Done pipeline?
The issue has been deployed to production and customers are deriving the 

### Closed issues

### How do I know if a ticket has been deployed?
All deployment notifications are sent as messages to the #deploys Slack channel with the date and time of deployment. Reviewing the closed issues for the corresponding repository and sorting by recently updated should provide you with an overview of what has recently been deployed.

### How are issues assigned?

### How do we use estimates?

## Labels
### Milestone Goal
Used to identify the issue that provides a high level overview for a milestone.
### reviewplx
Waiting on input from the current assignee. If you need someone to review 
### estimateplx
Issues with this label are needing an effort estimate from the current assignee.