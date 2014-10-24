/* Set up Git Configuration */

git config --global user.email "thiagoyudifukunaga@gmail.com"

git config --global user.name "Thiago Yudi Fukunaga"

git config --global core.editor "vi"

git config --global color.ui true

/* See Git configuration */

git config --list

/*  to initialise a local repository */

git init 

/*  adds a file to the repo */

git add 

/* commit the change to git */

git commit -m "Message goes here" 

/*  see the commits */

git log 

/*  Git has a 3 Tier Architecture:  Working - Staging Index - Respository

Changes to files are put in a Checksum SHA-1 hash 40digit value containing parent hash, author and message.

HEAD is the latest commit of the checked out branch */

/*  Basic Commands  */

git status  /*  the command 'git status' tells which files are not added or committed from Working to Staging to Repository */

git commit -m "" /*  Commits and changes to all files that are in Staging Tier into Repository  */

git diff /*  show changes between Working and Repository, no file supplied shows all files  */

git diff --staged /*  shows changes between Staged and Respository  */

git rm file.txt /*  will remove file from working then git commit -m "" to also remove from Repo */

git mv /*  rename or move files - then git commit -m "" to move to Repo */

git commit -am "text goes here" /* adds all files straight to Repo from Staging if they have changes - meaning they skip git add */

git checkout -- file.txt /*  restore Repo file to Working Directory using current branch  */

git reset HEAD file.txt /*  Move a Stage file out of Stage back to Working */

git commit --amend -m "message" file.txt /* Change last commit to Repo (only last one can change) */

/* Reverting --soft --mixed --hard */
git log /* gets the sha1s so you can see the coomits where you want to back to  */

git reset --soft sha /* changes Repo but not STaging or Working */

git reset --mixed sha /* changes Repo and STaging but not Working */

git reset --hard sha /* changes all 3 Tiers */

git clean -f /* remove untracked files from Working  */

.gitignore /* ignores files to track in Working / track the .gitignore file */

Global Ignore /* create in home folder  */ 
.gitignore_global
/* Add in  */
.DS_Store
.Trashes
.Spotlight_V100



git config --global core.excludesfile ~/.gitignore_global /* add to gitconfig */

/* Stop tracking changes */

rm --cached file.txt /* leaves copy in Repo and Working */


/* Track Folders changes

Add an invisble file to a folder like .gitkeeper then add and commit */

/* Commit Log  */
git ls-tree HEAD
git ls-tree master
git log --oneline
git log --author="Neil"
git log --grep="temp"

/* Show Commits */

git show dc094cb /*  show SHA1 */

/* Compare Commits

Branches */

git branch /*  Show local branches * is the one we are on */

git branch -r /* Shows remote branches */

git branch -a /* Shows local and remote */

git branch newbranch /* creates a new branch */

git checkout newbranch /* switch to new branch */

git checkout -b oldbranch /* creates and switches to new branch  */


/* Diff in Branches */

git diff master..otherbranch /*  shows diff */

git diff --color-words master..otherbranch /*  shows diff in color */

git branch --merged /*  shows any merged branches */

/* Rename Branch */

git branch -m oldname newname

/* Delete  Branch */

git branch -d nameofbranch

/* Merge Branch  */

git merge branchname /* be on the receiver branch */

/* Merge Conflicts between the same file on 2 branches are marked in HEAD and other branch */

git merge --abort /*  Abort basically cancels the merge */

/* Manually Fix Files and commit

The Stash */

git stash save "text message here"

git stash list /* shows whats in stash */

git stash show -p stash@{0} /* Show the diff in the stash */

git stash pop stash@{0} /*  restores the stash deletes the tash */

git stash apply stash@{0} /*  restores the stash and keeps the stash */

git stash clear /*  removes all stash */

git stash drop stash@{0}

/* Remotes
You fetch from the remote server, merge any differences - then push any new to the remote - 3 branches work remote server branch, local origin master and local master

Create a repo in GitHub, then add that remote to your local repo */

git remote add origin https://github.com/neilgee/genesischild.git /*  origin can be named whatever followed by the remote */

git remote /* to show all remotes */

git remote remove origin /* to remove remote */

git remote rm origin /* to remove remote */

/* Push to Remote from Local */

git push -u origin master

/* Cloning a GitHub Repo - create and get the URL of a new repository from GitHub, then clone that to your local repo, example below uses local repo named 'nameoffolder' */

git clone https://github.com/neilgee/genesischild.git nameoffolder

/* Push to Remote from Local - more - since when we pushed the local to remote we used -u parameter then the remote branch is tracked to the local branch and we just need to use... */

git push

/* Fetch changes from a cloned Repo */

git fetch origin /*  Pulls down latest committs to origin/master not origin, also pull down any branches pushed to Repo

Fetch before you work
Fetch before you pull
Fetch often */

/* Merge with origin/master */

git merge origin/master

/* git pull = git fetch + git merge

Checkout/Copy a remote branch to local */

git branch branchname origin/branchname /*  this will bring the remote branch to local and track with the remote */

/* Delete branch */

git branch -d branchname

/* Checkout and switch branch and track to remote */

git checkout -b nontracking origin/nontracking

/* Remove remote branch */

git push origin --delete branch
