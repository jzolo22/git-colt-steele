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

### **Undoing Changes & Time Traveling**
- "Detached HEAD state" 
  - if you do ```git checkout <commit hash>```, you have "traveled back in time" and can make changes without affecting the current "future" commits
    - can also do ```git checkout HEAD~1``` or ```git checkout HEAD~2``` --> those refer to one & two commits before HEAD, respectively (can use any number)
  - normally HEAD points to a branch reference (i.e. master) and the branch points to the most recent commit
    - so HEAD only changes when we switch branches
    - OR if we checkout a specific commit, in which case HEAD points to that actual commit, rather than a branch reference
- What we can do in "Detached HEAD":
  - stay in detached HEAD to examine the contents of the old commit. Poke around, view the files, etc.
  - leave and go back to where you were before ("reattach the HEAD")
  - create a new branch and switch to it. You can now make and save changes since HEAD is no longer detached (rather, pointing to a new branch reference)
- To get out of this state, simply switch to a branch.
  - ```git switch -``` will take you back to the branch you were on before entering "detached HEAD" state
  - HEAD will now point to a branch reference (and last commit) again
  
#### **Discarding Changes**
- ```git checkout HEAD <file name>``` OR ```git checkout -- <file name>```
  - will revert a file back to whatever it looked like when you last committed
- ```git restore <file name>```  
  - returns file to whatever a file looked like when you last committed (same as above)
  - can use ```git restore --source HEAD~1 home.html```
    - would restore the contents of home.html to its state from the commit prior to HEAD (can also use a specific commit hash as the source)

#### **Unstaging Files with Restore**
- ```git restore --staged <file name>```
  - if you accidentally added a file to the staging area with ```git add```, you can remove it from staging by using this command

#### **Git Reset**
- ```git reset <commit-hash>```
  - if you've made commits on master branch but meant to make them on a separate branch instead, can undo those commits
  - DOESN'T UNDO THE CHANGES IN THE WORKING DIRECTORY
  - then can switch to a new branch and commit the changes there instead
- ```git reset --hard <commit-hash>``` OR ```git reset --hard HEAD~1```
  - will delete the commits AND the associated changes

#### **Git Revert**
- ```git revert <commit-hash>```
  - removes the changes from a commit and saves it into a NEW commit

