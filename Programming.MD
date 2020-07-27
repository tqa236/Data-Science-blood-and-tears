Tips and tricks

* [Ignore all binary files without extension](https://stackoverflow.com/questions/5711120/gitignore-without-binary-files)

```
# Ignore all
*

# Unignore all with extensions
!*.*

# Unignore all dirs
!*/
```

* Use `re.DOTALL` to match a newline character.

* Delete all local git branch except several ones

```
git branch --no-merge | grep -v <BRANCH_1> | grep -v [BRANCH_2] | xargs git branch -D
```
