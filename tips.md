![[Pasted image 20231208012202.png]]
![[Pasted image 20231208012218.png]]

if changes pushed to remote rebo and realisez later that its complete garbage 
![[Pasted image 20231208012409.png]]

git stash 
gir pop

git stash save name
git stash list 
git stash apply index - to apply it

git log --graph --oneline --decorate

![[Pasted image 20231208012921.png]]

![[Pasted image 20231208013241.png]]

eg we have a remote repo on github and a local repo on our machine and we want to restore the remote repo to original state 
![[Pasted image 20231208013443.png]]
2nd line overwrites our local code with our remote code so all the changes on the local repo is lost forever
![[Pasted image 20231208013647.png]]
at last run this command to remove untracked files, build artifacts and other unwanted files 