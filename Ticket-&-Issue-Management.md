# Overview
Issues are filed in GitHub to the corresponding and related repository. We use [ZenHub](https://www.zenhub.io/) boards to view and manage the issues through their workflow. After installing the ZenHub Chrome Extension a new icon should show up on the GitHub repository, the ZenHub board icon should appear below the < > code icon. ZenHub uses "Pipelines" to help organize issues.

Some of the information below is adapted from: https://www.zenhub.io/blog/how-the-zenhub-team-uses-zenhub-boards-on-github/

### Issue Pipelines
We use the following pipelines:
* New Issues --> Ice Box --> Backlog <--> In Progress <--> Review/QA --> Done --> Closed

How do I see the progress for a Milestone?
https://github.com/PRX/www.prx.org/milestones?direction=desc&sort=completeness&state=open

### How do I create a New Issue?
Go to the appropriate repository and select "New Issue". Provide a meaningful title and enough of a description to help people review and understand the issue for triage. When New Issues are created they **should NOT be associated with a Milestone**, and **should NOT be assigned to anyone**.

### How does an issue in the New Issue pipeline move to Backlog?
We don’t want issues to stay in the New Issue pipeline very long. The New Issues pipeline relates to the concept of triage: all issues in this pipeline require a decision. The product owner and CTO review issues that are in the New Issue pipeline and triage them to determine if there is enough information to warrant them moving into the Backlog.

Issues that might require more information before moving into the Backlog should have the label "reviewplx" added to them and be assigned to the person who created the ticket. Sometimes issues won't make it into the Backlog (duplicates, can't be reproduced) and should be closed. 

### What happens to an issue once it is in Backlog?
Issues in Backlog are not a current focus. For example, they may be feature requests or ideas for the next version of your product.

In the Backlog pipeline, add more information (like requirements and outlines) into each issue. It’s useful to get ideas out of your head, even if you will not be touching them for a while.

Prioritize issues by dragging and dropping their placement in the pipeline. Issues higher in the pipeline are higher priority; accordingly, they should contain all the information necessary to get started when the time comes. Low-priority issues should still contain at least a short description.

The product owner will review issues that are in the Backlog, collecting more information, asking for effort estimates, and then prioritizing and grouping issues into related work, a Milestone. To assist the product owner with the prioritization process, issues may be assigned to someone, with the label "estimateplx" or "reviewplx". The assignee uses the ZenHub effort estimate feature to provide the product owner with additional information to assist with prioritization.

### How does an issue move from Backlog to To Do?
This is the team’s current focus, and issues should be well-defined. Issues in To Do will flow into the In Progress pipeline, so order them by priority and assign keepers using the Assignee function. Issues that exist in the To Do pipeline should belong to a Milestone.

### How are issues added to a Milestone?
Issues that are at the top of the Backlog are grouped into a Milestone. We use Milestones to group business value related issues and track the progress toward completion. Milestones should not be longer than a few weeks in length and should have due dates associated with them. We use the issue effort estimates to help determine how long, and what might exist in a Milestone.

### What does it mean for an issue to exist in the In Progress pipeline?
This is the answer to, “What are you working on right now?” Ideally, this pipeline should not contain more issues than members of your team; each team member should be working on one thing at a time.

This pipeline is a good candidate for WIP (work-in-progress) limits. WIP limits help ensure your work flows smoothly, and help bring to light any blockers or bottlenecks. Adjust WIP limits according to the size of your team.

### What does it mean for an issue to be in the Done pipeline?

### Closed issues

### How do I know if a ticket has been deployed?
All deployment notifications are sent as messages to the #deploys Slack channel with the date and time of deployment. Reviewing the closed issues for the corresponding repository and sorting by recently updated should provide you with an overview of what has recently been deployed.

Once an issue has been verified to be working as expected in the deployed environment the "verified" label should be added to the issue.

### How are issues assigned?

### How do we use estimates?

## Labels
### reviewplx
Waiting on input from the current assignee. If you need someone to review 
### estimateplx
Issues with this label are needing an effort estimate from the current assignee.
### verified
Applied to issues that have been verified to be working as expected in the deployed environment.