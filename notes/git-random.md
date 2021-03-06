# Random Git Things

### **Git Ignore**
- Why we'd need a git ignore folder:
  - secrets, API keys, credentials
  - log files
  - OS files
  - dependencies & packages
- Add file to root of directory (repo) called .gitignore
  - inside it, write patterns to ignore certain files/folders, e.g.
    -  ".DS_Store" for that specific file
    - "folderName/" for a whole folder
    - "*.log" anything that ends with .log ( * is a wildcard)

> gitignore.io --> for help/suggestions setting up the gitignore file

### **HEAD**
- pointer that refers to the current "location" in the repository
  - points to a particular branch reference

### **Branches w/ Unstaged Changes**
- if a new file has been added to a branch, then branch is changed without committing that file, the file will follow you to different branches

### **Stash**
