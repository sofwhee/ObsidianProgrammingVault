#Git 

When you tell git to make a branch, it's just like a tree. A new budding branch is made and now you're going to be going down that branch and leaving any other branches attached to your current git circle alone.
## syntax

```$ git branch newBranch```
```$ git checkout newBranch```

(shorthand)
```git checkout -b newBranch```

(delete)
 `git branch -d newBranch`
## best practices

- clean working state (no uncommited changes)
- when you switch branches, git changes everything to match the most recent commit on that branch
- the end goal of a branch is to re-[[Git merge|merge]] 
- Always [[Git branch|create a branch]] for each feature ([[Git merge|merge]] them back later).