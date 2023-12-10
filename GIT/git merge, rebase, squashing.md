#**TO UPDATE OUR FEATURE BRANCH**

git merge
![[Pasted image 20231208004453.png]]
- git merge ties a knot (F) b/w the main and feature branch, called merge commit
- F - new merge commit when we want to keep our feature branch updated with the main branch, if we use git merge it will create a new merge commit in the history named F. 
- gives complete details of commit history and branch evolution

git rebase
![[Pasted image 20231208004715.png]]
![[Pasted image 20231208010748.png]]
- git rebase tidies up history by moving commits to the main branch tip
- git rebase gives us a clean commit history by changing the base of the feature branch to the latest commit on main

#**TO UPDATE OUR MAIN BRANCH**

git merge
![[Pasted image 20231208005141.png]]
if we do it a lot, it will make the commit history messy

git rebase (Fast forward merge performed here)
![[Pasted image 20231208005502.png]]
![[Pasted image 20231208005521.png]]

Squash commit 
squashing commits consolidates all the commits into one, providing clean linear history in the main branch, but at the cost of detaile commit history
![[Pasted image 20231208010320.png]]
here all the feature branch commits are sqeezed into a single commit and merged intio main, creating a single merge commit.

- cleaner merge history in main branch
- but fine details of individual feature commits are lost

![[Pasted image 20231208011015.png]]