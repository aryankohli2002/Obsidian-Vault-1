<span style="background:#fff88f">To see files in the git index</span> <font color="#ff0000">command:</font> git ls-files

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
5. git status shows working tree clean
# reset - SOFT
git reset hash --soft
files still in working area and also in git index but we are pointing to the first commit, so soft resetdoesnt change anything.

Soft reset takes us back to the state such as-> if we had added files to staging area and we are ready to commit
![[Pasted image 20231210183352.png]]

# reset - HARD

git reset hash --hard
will remove file from both the working area and the staging index

------------------------------------------------------

The main difference between **git reset --soft**, **--mixed**, and **--hard** lies in how they handle the working directory, staging area, and HEAD pointer. Here's a breakdown:

**1. Git reset --soft:**

- **Working directory:** Unchanged.
- **Staging area:** Unchanged.
- **HEAD pointer:** Moved to the specified commit.

This essentially leaves your working directory and staging area untouched, but pretends that you've just checked out the specified commit. This is useful for discarding unstaged changes while keeping your staged changes and working directory intact.

**2. Git reset --mixed (default):**

- **Working directory:** Unchanged.
- **Staging area:** Reset to match the specified commit.
- **HEAD pointer:** Moved to the specified commit.

This is similar to --soft, but it also discards any staged changes. This is useful for reverting both staged and unstaged changes to a specific point in history.

**3. Git reset --hard:**

- **Working directory:** Reset to match the specified commit.
- **Staging area:** Discarded.
- **HEAD pointer:** Moved to the specified commit.

This is the most aggressive option. It discards all staged and unstaged changes, resetting your working directory to match the specified commit completely. This is useful for completely undoing changes and starting fresh from a specific point.

Here's a table summarizing the differences:

|Option|Working directory|Staging area|HEAD pointer|
|---|---|---|---|
|--soft|Unchanged|Unchanged|Moved|
|--mixed (default)|Unchanged|Reset|Moved|
|--hard|Reset|Discarded|Moved|

Here are some additional points to remember:

- **Untracked files are not affected by any reset command.**
- **Be careful when using --hard, as it can be difficult to recover from accidental changes.**
- Always use the appropriate option for your specific needs.

Here are some resources that you might find helpful:

- **Git reset documentation:** [https://git-scm.com/docs/git-reset](https://git-scm.com/docs/git-reset)
- **Comparison of soft, mixed, and hard resets:** [https://stackoverflow.com/questions/3528245/whats-the-difference-between-git-reset-mixed-soft-and-hard](https://stackoverflow.com/questions/3528245/whats-the-difference-between-git-reset-mixed-soft-and-hard)
- **Interactive Git reset tutorial:** [https://stackoverflow.com/questions/3528245/whats-the-difference-between-git-reset-mixed-soft-and-hard](https://stackoverflow.com/questions/3528245/whats-the-difference-between-git-reset-mixed-soft-and-hard)