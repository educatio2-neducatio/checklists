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

Did I?

- [ ]  Checkout the feature branch
- [ ]  Rebase on master
- [ ]  Rebase -i and squash in only one commit
- [ ]  Push —force the feature branch
- [ ]  Checkout master
- [ ]  Merge FF the feature branch
- [ ]  Push master
- [ ]  Delete branch
