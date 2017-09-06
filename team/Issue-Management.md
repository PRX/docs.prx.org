# Overview
Issues are filed in GitHub to the corresponding and related repository. We use [ZenHub](https://www.zenhub.io/) boards to view and manage the issues through their workflow. After installing the ZenHub Chrome Extension a new icon should show up on the GitHub repository, the ZenHub board icon should appear below the `<>` code icon. ZenHub uses "Pipelines" to help organize issues.

We are following the process described here: https://www.zenhub.io/blog/how-the-zenhub-team-uses-zenhub-boards-on-github/ This document will only cover differences, clarifications or modifications that are specific to PRX.

# Pipelines
We use the same pipelines as ZenHub:
* New Issues --> Ice Box | Backlog <--> In Progress <--> Review/QA --> Done --> Closed

# How do I create a New Issue?
Go to the appropriate repository and select "New Issue". Provide a meaningful title and enough of a description to help people review and understand the issue for triage. The most helpful part of the description is any acceptance criteria for the issue. For example:

> We'll know this issue is done when
>  * [ ] the URL https://foobar.prx.org/ returns a 200 response
>  * [ ] the content of the response includes `hello world`

A new issue should default to the `New Issues` Pipeline. The following metadata are also available.

## Assignee

When `New Issues` are created they are typically un-assigned, unless you are creating the issue specifically to track your own task.

## Milestone

Do not assign to a **Milestone** ([Sprint](Sprints.md)), unless you are assigning the issue to yourself.

## Priority

Feel free to assign a priority label of `low`, `medium` or `high`. Note that the priority may change during grooming.

## Estimate

ZenHub offers the Estimate field that vanilla GitHub does not. Feel free to assign an Estimate if you feel confident about the level of effort required to accomplish the issue. An Estimate must be set before the issue is moved to the `Backlog` Pipeline.

# Grooming

The goal of the grooming exercise is to move issues from the `New Issues` Pipeline to the `Backlog`. In order to be in the `Backlog`, an issue should have an **Estimate** and a **Priority**.

Sometimes issues just aren't clear enough in their description, or are an idea that we don't want to lose, or aren't yet high enough priority to move into the `Backlog`. We use the `Ice Box` as a place to hold onto those issues.

## Estimate
We use T-shirt sizes to gauge the level of effort estimated for an issue. ZenHub uses numbers, so we mentally map them like this:
```
1: Extra small
2: Small
3: Medium
5: Large
8: Extra large
```

## Priority
We use labels to assign a Priority of `high`, `medium` or `low`. The Priority should reflect both business and technical need for a particular issue. In theory, all `high` issues should receive attention before `medium` issues, etc.

# Need input or review on an issue?
Issues that might require more information should have the label `reviewplx` added to them. We use @mentions to draw the attention of people to the issue.

# What does it mean for an issue to be in the Done pipeline?
The issue has been completed, but is not yet deployed to production.

# Closed issues
Once a `Done` issue has been deployed, it can be closed.

# How do I know if a ticket has been deployed?
Deployment notifications are sent as messages to the #ops-deploys Slack channel with the date and time of deployment. 

# How are issues assigned?
Tickets are assigned during Sprint Planning, but may be adjusted later.
