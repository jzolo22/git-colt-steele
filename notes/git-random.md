# Random Git Things

### **Git Ignore**
- Why we'd need a git ignore folder:
  - secrets, API keys, credentials
  - log files
  - OS files
  - dependencies & packages
- Add file to root of directory (repo) called ```.gitignore```
  - inside it, write patterns to ignore certain files/folders, e.g.
    -  ```.DS_Store``` for that specific file
    - ```folderName/``` for a whole folder
    - ```*.log``` anything that ends with .log ( * is a wildcard)

> gitignore.io --> for help/suggestions setting up the gitignore file

### **HEAD**
- pointer that refers to the current "location" in the repository
  - points to a particular branch reference

### **Branches w/ Unstaged Changes**
- if a new file has been added to a branch, then branch is changed without committing that file, the file will follow you to different branches

### **Git Diff** 
- ```git diff``` --> lists all the changes in our working directory that are NOT staged for the next commit
- unless specified otherwise, git will be comparing 2 versions of the same file & names them a & b
- @@ --> start of a "chunk"
  - the first 2 numbers refer to old version, second to new
  - first number is line at which the chunk starts, second number is how many lines
- ```git diff --staged``` or ```git diff --cached``` --> i.e. show me what what will be included in my commit if I run git commit right now
  - shows all STAGED file changes
- ```git diff HEAD``` --> lists all changes in the working tree since your last commit
  - staged AND unstaged changes
  - as a reminder, HEAD just points to the last commit

> for all these commands, can follow with name of a specific file (or multiple separated by space) to see only changes in that file

- ```git diff branchA..branchB``` or ```git diff branchA branchB```  will compare changes between branches
- ```git diff commitA..commitB``` or ```git diff commitA..commitB``` will compare changes between commits
  - need to provide the commit hashes of the requested commits to be compared
    - can get by running git log --oneline & copying the number

### **Stash**
- If you make changes that are not committed on a branch and try to switch to a different branch, one of two things will happen:
  - changes will come with you to the different branch OR
  - git won't let you switch if there are potential conflicts with those changes and the different branch
- ```git stash``` or ```git stash save``` will take all uncommitted changes (staged & unstaged) and stash them, reverting the changes in your working copy. 
- ```git stash pop``` to remove the last stashed piece of code and apply it to the working directory
- ```git stash apply``` --> kind of like ```git stash pop``` but it applies the changes to your branch AND keeps them in your stash so you could apply your stashed changes to multiple branches if you wanted.
  - will assume that you want to apply the most recent stash
  - CAN specify which stash to apply by using ```git stash apply stash@{1}```
- ```git stash list``` --> will show all stashed items
- ```git stash drop stash@{1}``` --> remove a specific stash from stash
- ```git stash clear``` --> remove everything from the stash
