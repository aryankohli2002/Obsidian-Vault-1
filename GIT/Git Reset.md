git reset can be used to previous commit and can be used on current commit to clean the working and the staging area.

the repo doesn't change its only the working area and the staging index that changes, be it soft, mix, or hard reset

<font color="#ff0000">command</font>: git ls-files
# reset -MIXED 

it operates on the staging index, it does not delete the files from the working directory but only deletes it from the commit history and  files from staging index

after performing a mixed reset if we want to go back to our commit which we reset
steps 
1. git log --oneline
2. git reflog
3. find the hash we want to restore to
4. then git reset commit hash
5. git status