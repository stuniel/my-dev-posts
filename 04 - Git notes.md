## Fetch

### Create and move to new local branch

```
git checkout -b [branch]
```

### Fetch remote branch

```
git fetch origin
git checkout --track origin/<remote_branch_name>
```

`--track` is shorthand for `git checkout -b [branch] [remotename]/[branch]`.
