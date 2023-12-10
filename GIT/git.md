- git actually tracks changes and not files, 

- rm -rf .git to remove git from our project

- instead of making a new commit if we want to make changes to the previous commit we made (on git only not github) we can use the command git commit -m "message here" --amend

- to take changes out of staging area - git reset filename/folder name 
   or git reset . 
   or we can use  git checkout -- filename/ .
   
   
- **to go back to a different commit or view the previous version of our code** 
1. use git checkout commit hash 
2. use git checkout commit hash filenames/foldernames/ . to restore all the code 
3. to go to the latest commit -> git checkout master

- to show all the logs use git log --all 

- restoring code to a previous version 

git log --all --graph

to add git ignore file we also need to commit it 

![[Pasted image 20231203175812.png]]

The command `git push -u origin main` pushes your local `main` branch to the remote repository `origin` and sets it as the upstream branch. This means that you can use the `git push` command without specifying the branch name in the future, and Git will automatically push your changes to the `main` branch.

Here's a breakdown of the command:

- `git push`: The command to push local commits to a remote repository
- `-u`: The `-u` flag tells Git to set the upstream branch after pushing
- `origin`: The name of the remote repository
- `main`: The name of the local branch to push


what are these 3 commands for and whats the difference between them 
git push --set-upstream origin main
git push -u origin main
git push origin master -set--upstream 