to configure the default branche:

```Bash
git config --global init.defaultBranch main //'main' is the nmae of the default branch
```

git help:

```Bash
git command -h 
git help command
```

Initialize repository:

```Bash
git init
```

get the deffirence between modifyed file:

```Bash
git diff
```

restore staged file after adding them to stageing:

```Bash
git restore --staged file
```

bypass staging and commit:

```Bash
git commit -a -m "message"
```

restore deleted file:

```Bash
git restore file 
```

rename file:

```Bash
git mv "file" "new name"
```

reset to pervius commit:

```Bash
git reset c1929829 //commit id
```

modify the output of log ect…

```Bash
git rebase -i --root
```

get logs:

```Bash
git log
git log --oneline
```

amend commit:

```Bash
git commit -m "message" --amend
```

create another branch

```Bash
git branch branchname
git branch //to show all bracnhes
```

switch to another branch

```Bash
git switch branchname
```

merge two branches (to the master branche)

```Bash
git merge -m "Message" branche_name;
```

delete a branch

```Bash
git branch -d branch_name
```

create and switch to a branch

```Bash
git switch -c branch_name
```