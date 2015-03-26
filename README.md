#Version Control Workshop using Git for WordPress Development

##Exercise: Repository/Init/Cloning 

###Create Workshop Directory
We need to create a directory _(or folder)_ to contain our workshop files.

On Mac or Linux _(in Terminal, **case is important**):_ 

	mkdir ~/Sites
	mkdir ~/Sites/git-workshop
	cd ~/Sites/git-workshop
	
On Windows _(in Cmd):_ 

    md C:\Sites
    md C:\Sites\git-workshop
    cd C:\Sites\git-workshop
    

###Run Git to Verify it is Installed
On Mac or Linux _(in Terminal, **case is important**):_ 

	clear
	git
	
On Windows _(in Cmd):_ 

	cls
	git
    

###Initialize a Repository

	git init

###Configure Git to Know You
Be sure to **replace** the placeholders with your own information:

    git config --global user.name 'Your Name Here'
    git config --global user.email 'your_email@here.com'

##Exercise: Status/Commit/Add/Log

###Check Status of your Repository

	git status

Notice you are on branch `master`.

###Create a File
On Mac or Linux _(in Terminal, **case is important**):_ 

	echo 'Hello' > hello.txt
	ls
	git status
	
On Windows _(in Cmd):_ 

	echo 'Hello' > hello.txt
	dir
	git status
    
###Add the File to Files Ready to Commit

	git add hello.txt
	git status
	
###Commit the File

	git commit -m "My First Commit"
	git status

###Change the File
On Mac or Linux _(in Terminal, **case is important**):_ 

	echo 'Hello World' > hello.txt
	cat hello.txt
	git status
	
On Windows _(in Cmd):_ 

	echo 'Hello' > hello.txt
	type hello.txt
	git status
    
###Add the File Again and Commit

	git add hello.txt
	git commit -m "Add Hello to World"
	git status

###List Changes Storied in the Repository

	git log

###Add Another File and Commit

	echo 'More Info' > another.txt
	git add another.txt
	git commit -m "Adding another file"
	git log

		commit f97bc7c12e5487b66e5caa76d1d6a48720149424
		Author: Alejandra <alejandra@newclarity.net>
		Date:   Sun Mar 22 15:49:33 2015 -0400
		
			 Adding another file
		
		commit 4f00d7193a036b41d8b01b588c8ea4b759e50e32
		Author: Alejandra <alejandra@newclarity.net>
		Date:   Sun Mar 22 15:44:25 2015 -0400
		
			 Add World to Hello
		
		commit 2163cb170cab1e3541bba71ab6dd3c5206e485a9
		Author: Alejandra <alejandra@newclarity.net>
		Date:   Sun Mar 22 15:37:42 2015 -0400
		
			 My First Commit


##Exercise: Checkout/Head/Branch

###Checkout State of First Commit
Run the first command where <commit_id> is replaced with **your** specific commit ID from the `git log` command above.

	git checkout <commit_id>
	
i.e.

	git checkout 2163cb170cab1e3541bba71ab6dd3c5206e485a9

####List Files in Directory
On Mac or Linux _(in Terminal, **case is important**):_ 

	ls
	
On Windows _(in Cmd):_ 

	dir
    
The only file is `hello.txt`. We will call this state of files `first`.

###Create a Branch named `first`

	git branch first
	git status

###Checkout Branch `first`

	git checkout first
	git status
	git branch
	

###Add a Line to `hello.txt` on Branch `first`
i.e. Consider this a bug fix.

On Mac or Linux _(in Terminal, **case is important**):_ 

	echo 'Goodbye World' >> hello.txt
	cat hello.txt
	ls
	git commit -m "Fixing Lack of Goodbye (Bug)"
	
On Windows _(in Cmd):_ 

	echo 'Goodbye World' >> hello.txt
	type hello.txt
	dir
	git commit -m "Fixing Lack of Goodbye (Bug)"

###Oops, we need to Add before we can Commit

	git add hello.txt
	git commit -m "Fixing Lack of Goodbye (Bug)"


##Exercise: Merge/Conflict/Reset

###Checkout `master`
	git checkout master
	ls
	cat hello.txt
	
###Merge `first` into `master`
	git status
	git merge first
	ls
	cat hello.txt


###Create and Checkout New Branch `second`
i.e. Consider this a feature for a new version.

	git checkout -b second

Use your text editor to search and replace _"World"_ to _"People"_ in `hello.txt` _(you may need to reload the file.)_.  Now:
	

	git add hello.txt
	git commit -m "Changed World to People"
	
####Run commands to see changes

	git log -n3
	git branch
	ls
	cat hello.txt
	
####Checkout Branch `master`

	git checkout master
	
####Run commands to see changes

	git log -n3
	git branch
	ls
	cat hello.txt

####Change _"World"_ to _"Everyone"_ in  `master`
i.e. Consider this a concurrent change by another developer.

Use your text editor to search and replace _"World"_ to _"Everyone"_ in `hello.txt` _(you may need to reload the file.)_  Now:

	git add hello.txt
	git commit -m "Changed World to Everyone"
	
####Run commands to see changes

	git log -n3
	git status

####Merge Branch `second` into `master`

	git merge second
	
####Fix Conflict

Use your text editor to fix the following conflict _(keep just the Hello/Goodbye People):_

		<<<<<<< HEAD
		Hello Everyone
		Goodbye Everyone
		=======
		Hello People
		Goodbye People
		>>>>>>> second

####Add then Commit fixed conflict 

	git add hello.txt
	git commit -m "Fixed Conflict of Everyone and People"
	
####Run commands to see changes

	git log -n3
	git status


###Add New File `mistake.txt` 

	echo 'This is a mistake.' > mistake.txt
	git add mistake.txt
	git commit -m "Committed by mistake"


###Rollback Last Commit

	git reset --soft HEAD^
	git log -n3



##Exercise: Stash/Remove/Remote

###Add New File `new-file.txt` 

	echo 'This is a new file.' > new-file.txt
	git add *
	git status

###Oops, Forgot to Remove mistake.txt

	rm mistake.txt 
	git rm mistake.txt 
	git status

###Now Stash your New File

	git stash
	git stash list
	git status

###Now Checkout `second`
Imagine we want to work on the new feature again.

	git checkout second
	git log -n3

Imagine you did some changes, committed and are ready to return to master.

### Checkout `master`

	git checkout master
	git stash pop
	git stash list


##Exercise: Pantheon
Create account at:
- [pantheon.io](http://pantheon.io)
- Remember your password! 
	Write it down
	
Create your first site
- Follow the prompts
- Start with Core
	- Install WordPress
- _"Welcome to Pantheon"_
	- "_Developer with git pushes"_
		- 	https://pantheon.io/docs/articles/local/starting-with-git/
- Visit Website
- Configure WordPress Site Name, etc.
- Bookmark site URL
- See Dashboard
	- Dev
	- Test
	- Live

- Rename `.git` directory

        mv .git .git-save

- Open in Sublime (if Mac) 	    

- Switch Connection Mode to Git in Pantheon Dashboard
- Copy the SSH URL 

        
 	    git clone <ssh_url>
 	    

- Accept the fingerprint

##More Useful Git Terms

###Push
You **Push** uncommitted changes so a remote Git server to make your changes available to other developers.

###Pull
You **Pull** committed changes other developers have pushed to the Git server to synchronize their changes to your local repo.


##Exercise: Push/Pull

###Go to Admin/Plugins/Installed Plugins

###Go to WordPress directory in Sublime

###Delete this plugin in Sublime:
		
		wp-content/plugins/hello.php
		
###In Terminal, remove files from Git repo:

	cd <your_repo>
	git rm wp-content/plugins/hello.php
	git status
	git commit -m "Remove Hello plugin"


###Push Changes to the Remote Git Server at Pantheon

	git push

###Set "Push" Behavior to "Simple"

	git config --global push.default simple

###Look at Pantheon Dashboard
###Look at the WordPress Installed Plugins

###Get a Team Member and Add to your Pantheon Account

###Clone your team member's site to `git2`

###Modify your team member's site:
- Add the following to `index.php`

		<font size="7" color="red">I'm in your themes hacking your Internets!</font>

###Add Commit and Push
	
	git add *
	git commit -m "Adding my hack"
	git push
	
###Have them check out their website

###Check your website

###Now Pull Your Team Member's Changes

	git pull
	
Fix the hack using Sublime.

	git add *
	git commit -m "Fixed their hack"
	git push

###Check your website

## End of Part 1









	