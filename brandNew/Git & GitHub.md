## Git
 - Set name 
		- ![[Pasted image 20230605173553.png]]
 - view name -
	 - ![[Pasted image 20230605173639.png]]
 - set mail
	 - ![[Pasted image 20230605173722.png]]
 - view email
	 - ![[Pasted image 20230605173751.png]]
 - view all git details 
	 - ![[Pasted image 20230605173902.png]]
	 - ![[Pasted image 20230605173952.png]]
 - git config files
	 - normal details are stored in .gitconfig file in the home directory
		 - ![[Pasted image 20230605174121.png]]
 - view the status of git folder
	 ![[Pasted image 20230605175717.png]]
	 - what happens if u run that command in a folder where it is not started yet?
		 - ![[Pasted image 20230605175805.png]]
	 - what happens if u run that command in a folder with git ?
		 - ![[Pasted image 20230605175914.png]]
 - start a git repository
	 - before starting a git repo check whether it already has a git repo. otherwise youll run into problems
	 - ![[Pasted image 20230605175940.png]]
	 - ![[Pasted image 20230605180003.png]]
	- https://git-scm.com/docs 
	- git track all the subdirectories inside it 
 - staging Area
	 ![[Pasted image 20230605185924.png]]

- git commit
	- ![[Pasted image 20230605220207.png]]
- git ignore 
	- To use a `.gitignore` file in Git, follow these steps:

		1. Create a `.gitignore` file: In your project's root directory, create a file named `.gitignore`. The leading dot (`.`) is important to make it a hidden file.
    
		2. Edit the `.gitignore` file: Open the `.gitignore` file in a text editor and add rules for files or directories you want Git to ignore. Each rule should be on a separate line. You can use various patterns and wildcards to specify the files or directories to ignore. Here are some examples:
		  - ![[Pasted image 20230607092030.png]]

- git add
	- ![[Pasted image 20230606111626.png]]
- git branching
	- How normally git works?
		- ![[Pasted image 20230608151626.png]]
	- why we need branching?
		- ![[Pasted image 20230608151941.png]]
		- ![[Pasted image 20230608152150.png]]
	- Master Branch
		- ![[Pasted image 20230609174530.png]]
		- ![[Pasted image 20230609174638.png]]
		- ![[Pasted image 20230609174546.png]]
		- ![[Pasted image 20230609175321.png]]
		- What is Head?
			- ![[Pasted image 20230609180212.png]]
			- ![[Pasted image 20230609175933.png]]
			- Even though we can have multiple bookmarks only one place can be opened at  a time
			- ![[Pasted image 20230609180325.png]]
			- when I switch to another branch head will move
			- ![[Pasted image 20230609180411.png]]
			- ![[Pasted image 20230609180437.png]]
			- ![[Pasted image 20230611154041.png]]
			- inside refs folder there's files for each branch inside those files there are commit hashes
			- ![[Pasted image 20230611155019.png]]
			- ![[Pasted image 20230611155140.png]]
			- 
		- what happens when you do branching?
			- ![[Pasted image 20230611144032.png]]
			- you create a branch called dark mode 
			- ![[Pasted image 20230611144054.png]]
			- it still refers to the same commit as master. they are two branches pointing at the same thing. and head is pointing to dark mode
			- ![[Pasted image 20230611144233.png]]
			- but after commiting thing differes.
			- ![[Pasted image 20230611144318.png]]
			- ![[Pasted image 20230611144344.png]]
		- How to view the branches?
			- ![[Pasted image 20230611144444.png]]
			- ![[Pasted image 20230611144528.png]]
			- to get out press 'Q'
		- How to create a branch?
			- ![[Pasted image 20230611144707.png]]
			- ![[Pasted image 20230611145248.png]]
			- ![[Pasted image 20230611145307.png]]
			- ![[Pasted image 20230611145326.png]]
			- ![[Pasted image 20230611150409.png]]
			- ![[Pasted image 20230611150433.png]]
			- ![[Pasted image 20230611150444.png]]
			- ![[Pasted image 20230611150508.png]]
			- ![[Pasted image 20230611150513.png]]
			- ![[Pasted image 20230611150528.png]]
		- How to switch the branches ?
			- swtich
				- ![[Pasted image 20230611150603.png]]
				- ![[Pasted image 20230611151032.png]]
				- ![[Pasted image 20230611150632.png]]
				- ![[Pasted image 20230611150639.png]]
				- ![[Pasted image 20230611150649.png]]
				- ![[Pasted image 20230611150849.png]]
				- ![[Pasted image 20230611150921.png]]
				- ![[Pasted image 20230611151019.png]]
				- ![[Pasted image 20230611151032.png]]
			- checkout
				- ![[Pasted image 20230611152007.png]]
			- Create and switch at once 
				- ![[Pasted image 20230611152052.png]]
				- ![[Pasted image 20230611152115.png]]
			- change branches without commiting 
				- ![[Pasted image 20230611152511.png]]
				- if u create a new file and switch branches without commiting that file will come with u to what ever branch u go. 
		- Delete branch
			- ![[Pasted image 20230611153231.png]]
			- u can't delete the branch that you are currently on 
			- ![[Pasted image 20230611153309.png]]
			- don't allow us to delete without merging. we have to use -D
			- ![[Pasted image 20230611153415.png]]
		- Rename branch
			- change to the branch that we want to rename
			- ![[Pasted image 20230611153602.png]]
			- ![[Pasted image 20230611153614.png]]
			- ![[Pasted image 20230611153644.png]]
			- how head works
			- ![[Pasted image 20230611153625.png]]
			- 
## GitHub
-  Configuring ssh
	- https://docs.github.com/en/authentication/connecting-to-github-with-ssh
	- ![[Pasted image 20230606132902.png]]
	- ![[Pasted image 20230606133639.png]]
-  Get the code in Github
		1. Existing Repo's in Local Machine
			- ![[Pasted image 20230606134504.png]]
		2. Start a Project from Scratch
			- ![[Pasted image 20230606134532.png]]
		- Remote repository
			![[Pasted image 20230606150534.png]]
			- view Remote
				- ![[Pasted image 20230606150616.png]]
				- ![[Pasted image 20230606150928.png]]
			- Add Remote
				- ![[Pasted image 20230606151000.png]]
				- ![[Pasted image 20230606151023.png]]
				- ![[Pasted image 20230606151045.png]]
				- ![[Pasted image 20230606151116.png]]
- if you don't wanna type password everytime
	- credential.helper
		- ![[Pasted image 20230607060203.png]]
		- above cache command will keep the username and password for around few minutes. if you want to store it permately then instead of cache use store.
		- after you .gitconfig file would look like this 
			- ![[Pasted image 20230607060716.png]]
		- otherwise it would look like this 
			- ![[Pasted image 20230607060818.png]]
		- if you want to unset it use this 
			- ![[Pasted image 20230607060954.png]]
	- Use the personal access token with url (not secure)
		- ![[Pasted image 20230607093545.png]]
- Anytime you can change the access of these tokens or delete it
			- ![[Pasted image 20230607090844.png]]
- Git push
	![[Pasted image 20230607053527.png]]
	we don't always want to push our local master branch to github master branch
	![[Pasted image 20230607062041.png]]
	![[Pasted image 20230607062151.png]]
	![[Pasted image 20230607062522.png]]
	![[Pasted image 20230607062542.png]]
	![[Pasted image 20230607062553.png]]
	- it created a new branch called cats. but we want to push cats in to master branch.  
	- ![[Pasted image 20230607062717.png]]
	- look at the arrow key it shows the direction
	- ![[Pasted image 20230607062742.png]]
- -u option 
	- ![[Pasted image 20230607062841.png]]
	- ![[Pasted image 20230607063017.png]]
	- ![[Pasted image 20230607063228.png]]
	- but after specifying upstream
	- ![[Pasted image 20230607063351.png]]
	- now it works
	- ![[Pasted image 20230607063403.png]]
	- don't use below thing often. but it works
	- ![[Pasted image 20230607063531.png]]
	- you will run into some merging issues if you pushing from multiple branches to the same remote branch
-  Remote Tracking Branches
	- ![[Pasted image 20230607081417.png]]
	- ![[Pasted image 20230607081438.png]]
	- ![[Pasted image 20230607081307.png]]
	- ![[Pasted image 20230607081554.png]]
	- ![[Pasted image 20230607081622.png]]
	- ![[Pasted image 20230607081657.png]]
	- ![[Pasted image 20230607081438.png]]
	- ![[Pasted image 20230607081824.png]]
	- ![[Pasted image 20230607081835.png]]
	- ![[Pasted image 20230607081850.png]]
	- ![[Pasted image 20230607082114.png]]
	- ![[Pasted image 20230607082235.png]]
	-  ![[Pasted image 20230607104553.png]]
	- ![[Pasted image 20230607105456.png]]
	- ![[Pasted image 20230607105430.png]]
	- ![[Pasted image 20230607105521.png]]
	- ![[Pasted image 20230607105618.png]]
	- ![[Pasted image 20230607113636.png]]
	- ![[Pasted image 20230607113656.png]]
## working with remote branches
- ![[Pasted image 20230608114001.png]]
- ![[Pasted image 20230608114052.png]]
- ![[Pasted image 20230608114207.png]]
- ![[Pasted image 20230608114300.png]]
- ![[Pasted image 20230608132014.png]]
- ![[Pasted image 20230608132123.png]]
