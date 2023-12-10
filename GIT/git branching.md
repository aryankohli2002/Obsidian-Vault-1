
1. Integration branches - long running 
    often named develope or staging- represents states in a projects release or deployment process
3. release
4. feature - short lived and deleted after integrated, bug fix, new feature, experiment, based on long running branch.
5. master - long running 

never directly commit in log running branches only through rebase or merges

two eg of branching strategies 
1. github flow
![[Pasted image 20231208000026.png]]
3. git flow
![[Pasted image 20231208000050.png]]
- here the main branch is reflection of current production state
- all other branches will be merged back into develope branch 
![[Pasted image 20231208000644.png]]
	 