#Version Control Workshop using Git for WordPress Development

##Prerequisites 

###Install Git
####**Mac:** 

- Go here http://git-scm.com/download/mac 
- Follow instructions to install
- Use Spotlight to open `terminal`
- Type `git` to verify that Git is installed

####**Windows:** 
Go here and follow instructions: 
- http://git-scm.com/download/win

###**Linux:** 
Go here and follow instructions: 
- http://git-scm.com/book/en/v2/Getting-Started-Installing-Git

- Create GitHub and BitBucket Accounts 
- Install Sublime 2
- Install Gitflow
- Install SourceTree

##Definitions

###WordPress Developers work on:
- Themes, 
- Plugins, 
- and the Database.

###Themes and Plugins are comprised of _"Source Code"_
- HTML
- CSS
- PHP
- Javascript
- Maybe other(?)

###Professional Workflow
Professional workflow for development WordPress sites uses a series of servers for the process:
- Develop source code on a local **_"Development"_** computer _(a best practice)_
- Test code on **_"Testing"_** server _(to discover code bugs)_
- Users use and enter content on a **_"Staging"_** server _(to discover usability issues)_
- Deploy working source code to a **_"Live"_** a.k.a. **_"Production"_** server.

###Why Development on a Local Computer a Best Practice?
- We shall soon see.


##What is _"Version Control?"_
- **Version control** is a system _(e.g. Git)_ that records changes to a file or set of files over time so that you can recall specific versions later. 

###Why is Version Control Important?
####To restore earlier versions of source code for bugs fixes
**Checkout specific earlier code:** _i.e. If an older version of the source code for a site is the live site and development on the next version is in progress, version control allows you to recover the source code that is running on the live server back to your development machine, fix a bug, redeploy to the live site, and then return back to working on the next version of the site._

####To Allow _"What If?"_ Development
**Branch the current code:** _"i.e. You want to implement an new feature but are not sure how to do it and do not want to fear breaking the working source code when you first try to implement."_

####To Recover Lost Source Code
**Clone the repository:** _i.e. you forget to backup the source code. Doh! With version control, the source code is never lost; you just recover from version control."_
	
####To Working Efficient in a Team
**Merge different commits:** "_If more than one person is changing source code at a time -- i.e. a backend developer, a front-end themer and a Javascript developer -- then chances are great one person will overwrite code that another has written. Version control acts as the traffic cop for multiple developers._

##Which Version Control to Use?  _Git_
**Git** - [git-scm.com](http://git-scm.com)
- Command line tool
- Open-source, free to everyone
- Works on Mac, Windows, Linux
- Most widely used version control today.	

##Initial Git Terminology

###Repository:
A **Repository** is a directory that contains all of the project files _(including documentation)_, and stores each file's revision history.

###Initializing:
To create a **New** repository on the local computer.

###Cloning:
**Cloning** is the process of copying a repository of source code from a remote computer to your local computer.

##Basic Git Tutorial, Part 1

####Create Workshop Directory
We need to create a directory _(or folder)_ to contain our workshop files.

On Mac or Linux _(in Terminal, **case is important**):_ 

	mkdir ~/Sites
	mkdir ~/Sites/git-workshop
	cd ~/Sites/git-workshop
	
On Windows _(in Cmd):_ 

    md C:\Sites
    md C:\Sites\git-workshop
    cd C:\Sites\git-workshop
    

####Run Git to Verify it is Installed
On Mac or Linux _(in Terminal, **case is important**):_ 

	clear
	git
	
On Windows _(in Cmd):_ 

	cls
	git
    

####Initialize a Repository

	git init

####Configure Git to Know You
Be sure to **replace** the placeholders with your own information:

    git config --global user.name 'Your Name Here'
    git config --global user.email 'your_email@here.com'

##More Git Terminology

###Status:
The **Status** of the repository is the current state of all the files under development.

###Adding:
**Adding** a file or files to the list of files ready to be committed to the repository.

###Commit:
A **Commit** is a process that applies a set of files changes to the repository.


##Basic Git Tutorial, Part 2

####Check Status of your Repository

	git status

Notice you are on branch `master`.

####Create a File
On Mac or Linux _(in Terminal, **case is important**):_ 

	echo 'Hello' > hello.txt
	ls
	git status
	
On Windows _(in Cmd):_ 

	echo 'Hello' > hello.txt
	dir
	git status
    
####Add the File to Files Ready to Commit

	git add hello.txt
	git status
	
####Commit the File

	git commit -m "My First Commit"
	git status

####Change the File
On Mac or Linux _(in Terminal, **case is important**):_ 

	echo 'Hello World' > hello.txt
	cat hello.txt
	git status
	
On Windows _(in Cmd):_ 

	echo 'Hello' > hello.txt
	type hello.txt
	git status
    
####Add the File Again and Commit

	git add hello.txt
	git commit -m "Add Hello to World"
	git status

####List Changes Storied in the Repository

	git log

####Add Another File and Commit

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

##Even More Git Terminology

###Checkout:
**Checkout** is a process to pull earlier versions of source code out of the repository to create a new state of files in the directory.

###Head:
The **Head** is a pointer to the most recent commit of your repository.

###Detached Head:
When you have a **Detached Head** the **Head** pointer points to the specific commit ID and not a named branch. 

###Branch:
A **Branch** is a named collection of the files changes that have been committed to that branch. 

_If you commit to a detached head you may loose your changes later because no names point to your list of commits._

##Basic Git Tutorial, Part 3

####Checkout State of First Commit
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

####Create a Branch named `first`

	git branch first
	git status

####Checkout Branch `first`

	git checkout first
	git status
	git branch
	

####Add a Line to `hello.txt` on Branch `first`
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

####Oops, we need to Add before we can Commit

	git add hello.txt
	git commit -m "Fixing Lack of Goodbye (Bug)"




##Another Git Term

###Merge:
A **Merge** is to take one branch of code and merge its state into another branch of code.

##Basic Git Tutorial, Part 3

####Checkout `master`
	git checkout master
	ls
	cat hello.txt
	
####Merge `first` into `master`
	git status
	git merge first
	ls
	cat hello.txt

##Yet Another Git Term

###Merge Conflict:
A **Merge Conflict** is what happens when the same files in the two branches being merged have had their same line of code changed. 

##Basic Git Tutorial, Part 4
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


##Yet Another Git Term

###Reset
A **Reset** rolls back changes to a previous set of commits. NEVER reset when you have already `push`ed code to a remote server.


##Basic Git Tutorial, Part 5

###Add New File `mistake.txt` 

	echo 'This is a mistake.' > mistake.txt
	git add mistake.txt
	git commit -m "Committed by mistake"


###Rollback Last Commit

	git reset --soft HEAD^
	git log -n3



##Another Set of Useful Git Terms

###Stash
You **Stash** uncommitted changes so Git will allow you to checkout an existing branch, otherwise your changes might conflict with the branch.

###Remove
You **Remove** changes from the list of files to commit so Git will not commit them on the next commit.

##Basic Git Tutorial, Part 6

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


##Working in Teams with Remote Git Hosts

###What is a _"Remote Repository?"_

_**Remote Repositories** are versions of your project that are hosted on the Internet or on your network somewhere on a **"Git Server."**_ 

###How to Host Your Git Repositories

####Run your own Git Server 
But who really wants to do that?

####Use a Commercial Git Host
The two (2) best known commercial Git hosts are:

- **GitHub.com**
	- Free for open-source repositories 
	- Charges fee for private/controlled access repos.
	- Generally Charges per repo
	- Most popular for open-source
	
- **Bitbucket.org**
	- Free for open-source repositories 
	- Free for private/controlled access repos.
	- Four (4) or Five (5) users are free.
	- Charges fee for number of users. 
	- Most popular for small teams

Also, for WordPress Developers: 

- The Pantheon Web Host
	- Deploy via Git _(vs. FTP)_
	- Free for development and testing
	- Pay when you deploy to a live site


###Create Pantheon Account
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


##Intermediate Git Tutorial, Part 1

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


##TODO
- Save Password somehow
- Create GitHub and BitBucket Accounts
	- Clone and set up keys
- GitFlow
- SourceTree
- WordPress Workflow
	- WordPress Core
	- Content Directory
		- Site Theme
		- Site Plugin
		- Other Plugins




















	