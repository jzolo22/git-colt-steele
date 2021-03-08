# Git Workflow

### **Workflow**
1. Work on stuff (Working Directory)
   - make new files, edit files, delete files, etc
2. Add changes (Staging Area)
   - group specific changes together in preparation to commit
3. Commit (Repository)
   - everything that was added in step 2

### **What is Committing**
- adding a "snapshot" or "checkpoint"
- *Atomic Comits* - when possible, a commit should encompass a *single* change, feature or fix
- for commit messages:
  - git recommends imperative voice (i.e. "make x do y" instead of "made x do y")

### **Branching**
- "alternative timelines" for a project
- enable us to create separate contexts to try different things without breaking the main branch
- the default branch is "master" but has no special powers or anything. It doesn't *have* to exist and doesn't have to be the SSOT for your codebase - you can decide for yourself what you want to do with it/ how you want to use it
- creating branches
  - ```git branch new-branch-name```
    - creates it based on the current HEAD
    - DOESN'T ACTUALLY CHECK IT OUT, JUST CREATES IT
  - ```git switch branch-name``` 
  - ```git switch -c branch-name``` --> make a new branch and switch right away
    - ```-c``` --> short for create 
- **deleting/renaming branches**
  - ```git branch -d branch-name``` --> delete branch
    - can't do that while on the branch being deleted
  - ```git branch -m new-branch-name``` --> rename branch
    - must be on the branch to rename
- ```git branch -v``` --> provides additional information about each branch (e.g. last commit) 

### **Merging**
- we merge *branches*, not specific commits
- we always merge to the current HEAD branch
- follow 2 steps to merge:
  - switch to the branch that should *receive* the changes
  - use ```git merge bugfix``` to merge changes from ```bugfix``` into the receiving branch
- if there are no new commits (since branching) on the receiving branch, it's called a "fast-forward" merge, since it's just bringing the receiving branch up to the pointer of the bugfix one

### **Resolving Merge Conflicts**
- 3 steps:
  - open file(s) with merge conflicts
  - edit the file(s) to remove the conflicts
    - decide which branch's content you want to keep in each conflict or keep the content from both
  - remove the conflict "markers" in the doc
  - add your changes and then make a commit

