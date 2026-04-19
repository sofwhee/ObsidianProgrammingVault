#Git
## syntax

(first checkout the branch you're trying to merge into, usually 'master'/'main')
```$ git checkout branchToMergeInto```
```Switched to branch 'branchToMergeInto'```
```$ git merge branchToMerge```

## conflicts

- Both branches made different changes to the same part of same file
- Use [[git status]] to see unmerged files after a conflict
- Use [[git mergetool]] for a visual merge tool 