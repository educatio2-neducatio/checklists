# Git Workflow

## Starting a new feature (working branch)

Did I?

- [ ] Branch the current state-of-the-art branch (master by default, another feature branch if neeeded)
- [ ] Work on it and do some commits
- [ ] Publish your branch when ready

## Asking for review:

Did I?

- [ ] Create a PR against master 
- [ ] Assign a teammate to the PR 

If the parent branch is not master:

- [ ] Mention in description that this PR depends on another branch with `"Depends on: #pr-number"`

## Reviewing a PR:

> :warning: Do not review a PR that depends on an unclosed PR

> :warning: Never merge a branch on a feature branch - you will get crazy trying to squash your commits, and you will probably lose some work

- [ ] Checkout the feature branch
- [ ] Rebase on master
- [ ] Push the feature branch
- [ ] Make comments/review on the diff

## Merging a PR:

* Checkout the feature branch
* Rebase on master
* Rebase -i and squash in only one commit
* Push —force the feature branch
* Checkout master
* Merge FF the feature branch
* Push master
* Delete branch

## Commit format

Commit messages on master should be short and to the point (no useless word). Forbid: "Implements", "Add the possibility",  "Make ... possible", etc...

For feature commit, use the short story format (preferrably from Trello):

* Bad: "Implement the hangup of an expert call when the call is finished." ('Implement' is useless)
* Bad: "As an experts, I hang up when the call is finished" (this is the long story format)
* Good: "Experts hang up when the call is finished"

### Other formats:

#### Chore commits (purely technical or configuration)
Format : [Verb] [Action done by the commit]

* Bad: "listenChannel => listenToChannel in messages.js + remove some useless code" (too long, shoud contain only one action)
* Good: "Refactor chat module" (to the point, high level)

#### Bug commits
Format : [Verb] [Problem fixed by the commit]

Good: "Avoid to send anonymous ember-cli data"

#### Design commits

> No design commit. Design should support features. There should be a Trello card with a User Story for design stories.
