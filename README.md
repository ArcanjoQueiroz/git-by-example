**Git by Example**
------------------

**Configuration**

    # Configure your username
    git config --global user.name "Alexandre Arcanjo de Queiroz"
    
    # Configure your e-mail
    git config --global user.email alexandre@queiroz.com
    
    # Configure meld as difftool
    git config --global diff.tool meld
    git config --global difftool.prompt false
    
    # Configure meld as mergetool
    git config --global merge.tool meld
    git config --global mergetool.keepbackup false
    
    # Configure post buffer size
    git config --global http.postBuffer 524288000
    
    # Ignore SSL
    git config --global http.sslVerify false
    
    # Configure git grep line number
    git config --global grep.lineNumber true

    # Set vim as default commit editor
    git config --global core.editor "vim"

    # Configure prune auto for git fetch and git pull
    git config --global remote.origin.prune true

    # Configure git rebase after git pull
    git config --global pull.rebase true

    # Configure alias
    git config alias.lg 'log --pretty="%C(yellow)%h %<(10) %C(cyan)%ad %<(25) %C(green)%an %<(30) %C(reset)%s" --date=short --decorate --no-merges --all'    

**Manage configuration**

    # List global configuration
    $ git config --global --list

    # Edit global configuration in default commit editor
    $ git config --global -e

    # List system configuration
    $ git config --system --list

    # List local configuration
    $ git config --local --list

    # Remove global configuration
    $ git config --global --unset my.own.config

    # Configure commit template
    $ git config --global commit.template $HOME/.gitcommitmsg.txt
    
**Creating git repository**

    # Create git repository
    $ git init

**Cloning git repository**

    # Clone git repository
    $ git clone https://github.com/foo/bar.git
    
    # Clone specific branch
    $ git clone -b v1.1.2 https://github.com/foo/bar.git

**Status**

    # Show status
    $ git status

    # Show only modified files
    $ git status -sb

**Adding files**

    # Add file into staging area
    $ git add MyServlet.java
    
    # Remove file from staging area
    $ git rm --cached MyServlet.java

    # Add all files
    $ git add -A

**Committing files**

    # Commit
    $ git commit
    
    # Write a simple commit message
    $ git commit -m '#1234 comment: Fixing TreeSet implementation'
    
    # Git add + commit
    $ git commit -am '#4567 comment: Fixing ActiveMQ configuration'

    # Amend last commit
    $ git commit --amend

**Resetting files**

    # Cancel last commit
    $ git reset HEAD~1

    # Reset to origin state
    $ git reset --hard origin/master

    # Reset to a specific commit
    git reset --hard 8a01849306c655ab418b7999b18d6ff5f43928b2

**Show modifications**

    # Show specific commit
    $ git show 3e0c4a6

    # Show specific commit in oneline
    $ git show --oneline --name-status 0a7bb41ad4bf9afe45bef2c48984cea8d8c3ca30

    # Show blame
    $ git blame README.md

**Push** 

    # Push
    $ git push

    # Forced push (not recommended)
    $ git push -f origin v1.1.2

    # Push to origin branch master
    $ git push origin master

    # Push commits to a new branch and set the upstream
    $ git push -u origin newBranch

    # Push commits to a new branch and set the upstream
    $ git push origin newBranch
    $ git branch --set-upstream newBranch origin/newBranch

**Diff**

    # Open difftool
    $ vim MyServlet.java
    $ git difftool

    # Show differences (name) between two remote branches
    $ git diff --name-only origin/v1.1 origin/master 

    # Show differences (name and status) between two remote branches
    $ git diff --name-status origin/v1.1 origin/master 

    # Show only deleted and added files between two remote branches
    $ git diff --name-status --diff-filter=DA origin/v1.1 origin/master 

    # Show differences between a local and a remote branch
    $ git diff master origin/master

    # Show files between a specific commit and HEAD
    $ git diff --name-only 2cb4c91..HEAD

    # Show deleted files between a specific commit and HEAD
    $ git diff --name-only --diff-filter=D 2cb4c91..HEAD

    # Show difftool between two remote branches
    $ git difftool origin/v1.1 origin/master

    # Show difftool between a local and a remote branch
    $ git difftool master origin/master

**Updating local repository**

    # Update local repository and run mergetool
    $ git pull
    $ git mergetool

    # Update local repository and run mergetool
    $ git fetch
    $ git merge origin/master
    $ git mergetool

    # Prune deleted branches in remote repository
    $ git fetch --prune
    
    # Merge with no fast forward
    $ git fetch origin
    $ git merge --no-ff origin/master
    $ git mergetoo

**Branch information**

    # Show branches
    $ git branch
    
    # Show only remote branches
    $ git branch -r
    
    # Show all branches
    $ git branch -a
    
    # Create and checkout a branch 
    $ git branch issue11
    $ git checkout issue11
    
    # Create and checkout a branch 
    $ git checkout -b issue11
    
    # Create a branch from commit
    $ git branch foo 691679d8b0c1c7b5a1528ffc94be5d15bbd5e420
    $ git checkout foo

    # Create a branch from tag
    $ git checkout -b newBranch myTag
    
    # Rename local branch
    $ git branch -m foo

    # Remove local branch
    $ git branch -d issue11

    # Remove remote branch
    $ git push origin :myRemoteBranch

    # Remove remote branch
    $ git push origin --delete myRemoteBranch
    
    # Remove remote branch
    $ git push origin -D myRemoteBranch

    # Exibe origem da branch no reflog
    $ git reflog show v1.1.2

    # Cria branch e seta o remote upstream
    $ git checkout -b remoteBugFix --track origin/stable-3.2

    # Configure a new upstream of the current branch
    $ git branch --set-upstream-to=origin/stable-3.2
    $ git branch -u origin/stable-3.2

    # Show local branches which contains a specific commit
    $ git branch --contains 014b6f8

    # Show all local branches which contains a specific commit
    $ git branch -a --contains 2ddfba3

**Merge**

    # Merge issue11 into master
    $ git checkout master
    $ git merge issue11
    $ git mergetool
    
    # Merge issue11 into master
    $ git checkout master
    $ git merge -m '#12345 comment: Fix' issue11
    $ git mergetool
    
    # Abort merge
    $ git checkout master
    $ git merge issue11
    $ git merge --abort

    # Show unmerged files
    $ git ls-files -u
    $ git ls-files --unmerged

    # Find the most recent common ancestor of two branches
    $ git merge-base develop master

**Discarding modifications**

    # Discard modification
    $ git checkout -- MyServlet.java
    
    # Discard modification
    $ git checkout MyServlet.java

**Removing files**

    # Removing file
    $ git rm CustomerDAO.java
    
    # Removing file (forced)
    $ git rm -f CustomerDAO.java

**Moving and renaming files**

    # Renaming file
    $ git mv CustomerDAO.java CustomerDAOImpl.java
    
    # Moving file
    $ git mv CustomerDAO.java dao/CustomerDAO.java

**Ignoring files**

    $ vim .gitignore
    
    **/.classpath
    **/.project
    **/target/
    **/.settings/
    **/.idea/
    **/*/.gitignore
    **/*.class

**Stashing (Work In Progress)**

    # Save stash
    $ git stash

    # Save stash
    $ git stash save myStash
    
    # Pop last stash
    $ git stash pop
    
    # Lista stash list
    $ git stash list
    
    # Show stash info
    $ git stash show -p 0
    $ git stash show -p 1
    $ git stash show 0
    $ git stash show 1
    $ git stash show stash@{0}
    
    # Create branch from stash
    $ git stash branch issue12 stash@{0}
    
    # Drop stash
    $ git stash drop stash@{0}
    
    # Apply stash
    $ git stash apply stash@{0}

**Searching**

    # Grep files by text
    $ git grep "int i=10"

    # Show line number
    $ git grep -n "int i=10"
    
    # Grep files only in staging area
    $ git grep --cached "int i=10"
    
    # Ignore case
    $ git grep -i "CREATE INDEX"
    
    # Show only file name
    $ git grep --name-only "CustomerService"
    
    # Grep only js files in a specific branch
    $ git grep "setTimeout" branch7 -- *.js
    
    # Grep in all branches
    $ git rev-list --all | xargs git grep "CustomerServiceImpl"
    
    # Grep in all branches
    $ git grep "CustomerServiceImpl" $(git rev-list --all)

**Remote repository**

    # Show remote repositories
    $ git remote show
    
    # Show remote repository info
    $ git remote show origin
    
    # Verbose
    $ git remote show -v
    
    # Verbose
    $ git remote show -v origin
    
    # Add new remote repository
    $ git remote add bitbucket git@bitbucket.org:foo/xpto.git
    
    # Set new remote repository URL
    $ git remote set-url bitbucket git@bitbucket.org:bar/foo.git
    
    # Remove remote repository
    $ git remote rm bitbucket
    
    # Rename remote repository reference
    $ git remote rename bitbucket legacy

**Tags**

    # Show tags
    $ git tag
    
    # Create simple tag
    $ git tag v1.0.0
    
    # Create annotated tag
    $ git tag -a v1.1.1 -m 'Criando tag'
    
    # Push tags
    $ git push origin master --tags
    
    # Remove local tag
    $ git tag -d v1.0.0

**Log**

    # Show log
    $ git log

    # Show log in one line
    $ git log --oneline

    # Decorate and graph
    $ git log --decorate --graph --oneline
    
    # Show log with patch
    $ git log -p
    
    # List by author
    $ git log --author foo@bar.com
    
    # List by commit message
    $ git log --grep DAO
    
    # Show name only
    $ git log --name-only

    # Show name and status
    $ git log --name-status
    
    # Show by modification
    $ git log -G "isEmpty" --oneline

    # Show between dates
    $ git log --author=alexandre --before="2015-06-24 23:59:59" --after="2015-06-24 00:00:00" --no-merges --branches=*/master

    # Show reflog
    $ git reflog

**Garbage Collector**

    # Run Garbage Collector
    $ git gc

    # Run Garbage Collector and prune now
    $ git gc --prune=now

    # Count objects
    $ git count-objects

    # Find for unreachable objects
    $ git fsck --unreachable
