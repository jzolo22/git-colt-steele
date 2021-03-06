# Terminal Commands Cheatsheet

### **Basic Navigation**
- ```ls``` --> list the contents of the folders
  - ```ls -a``` --> shows hidden files too
- ```open .``` --> opens Mac folder 
- ```ls 'specific folder name'``` see contents of that specific folder
- ```clear``` or ```Cmd + k``` --> clears terminal window
- ```pwd``` --> print working directory
  - prints exactly which folder you're in
- ```cd 'folder-name'``` --> change to different folder location
- ```cd ..``` --> go up one level/folder

### **Creation/Deletion of files/folders**
- ```touch 'file-name'``` --> creates a file in the folder you're currently in
  - can make them in a different location by specifying path
    - i.e. ```touch 'Users/Documents/hello.js'```
- ```mkdir 'folder-name'``` --> creates a folder in the directory you're currently in
- ```rm 'file-name'``` --> *permanently* deletes **file**
- ```rm -rf 'file-name'``` --> *permanently* deletes **folder**
> *For all commands: can make/delete several files/folders at once by separating names by a space
 > - i.e. ```touch hello.js goodbye.js```

### **Git Commands**
- ```git status``` --> shows git status
- ```git init``` --> make the current directory a new git repository
  - run it one time per project!
- ```git log``` --> see record of all previous commits 
- ```git log --pretty``` or ```git log --oneline```
- ```git commit --amend``` --> will open VSCode 
  - allow you to amend the commit message from the previous commit
  - alternately, if you type ```git add``` prior to ```git commit --amend``` then you can just close the file that opens and the file you've added with ```git add``` will be added to that commit as well
- ```git commit -a -m 'message'``` --> commits all unstaged changes


