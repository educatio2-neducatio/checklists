# How to write commits

Commit messages on master should be short and to the point (no useless word). Forbid: "Implements", "Add the possibility",  "Make ... possible", etc...

For feature commit, use the short story format (preferrably from Trello):

* Bad: "Implement the hangup of an expert call when the call is finished." ('Implement' is useless)
* Bad: "As an experts, I hang up when the call is finished" (this is the long story format)
* Good: "Experts hang up when the call is finished"

## Chore commits (purely technical or configuration)
Format : [Verb] [Action done by the commit]

* Bad: "listenChannel => listenToChannel in messages.js + remove some useless code" (too long, shoud contain only one action)
* Good: "Refactor chat module" (to the point, high level)

## Bug commits
Format : [Verb] [Problem fixed by the commit]

Good: "Avoid to send anonymous ember-cli data"

## Design commits

> No design commit. Design should support features. There should be a Trello card with a User Story for design stories.
