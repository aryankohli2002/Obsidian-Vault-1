- At a high-level, Git can be thought of as a timeline management utility. 
- Commits capture the state of a project at that point in time. Git Snapshots are always committed to the local repository. 

1. This is fundamentally different from SVN, wherein the working copy is committed to the central repository. 

2. In contrast, Git doesn’t force you to interact with the central repository until you’re ready. 

Just as the staging area is a buffer between the working directory and the project history, each developer’s local repository is a buffer between their contributions and the central repository.

This changes the basic development model for Git users. Instead of making a change and committing it directly to the central repo, Git developers have the opportunity to accumulate commits in their local repo. This has many advantages over SVN-style collaboration: it makes it easier to split up a feature into atomic commits, keep related commits grouped together, and clean up local history before publishing it to the central repository. It also lets developers work in an isolated environment, deferring integration until they’re at a convenient point to merge with other users. While isolation and deferred integration are individually beneficial, it is in a team's best interest to integrate frequently and in small units. For more information regarding best practices for Git team collaboration read how teams structure their [Git workflow](https://www.atlassian.com/git/tutorials/comparing-workflows).