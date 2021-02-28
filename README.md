**Git by Example**
------------------

**Configuration**

    # Configure your username
    git config --global user.name "Alexandre Arcanjo de Queiroz"
    
    # Configure your e-mail
    git config --global user.email alexandre.queiroz@live.com
    
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

**Manager configuration**

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

**Show Modifications**

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
    $ git fetch
    $ git merge origin/master
    $ git mergetool

    # Update local repository and run mergetool
    $ git pull
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

    # Exibe as branches locais que possuem determinado commit
    $ git branch --contains 014b6f8

    # Exibe as branches locais e remotas que possuem determinado commit
    $ git branch -a --contains 2ddfba3

**Merge**

    # Merge de issue11 em master
    $ git checkout master
    $ git merge issue11
    $ git mergetool
    
    # Merge de issue11 em master
    $ git checkout master
    $ git merge issue11
    $ git mergetool -t meld
    
    # Merge com mensagem
    $ git checkout master
    $ git merge -m '#12345 comment: merge da correcao emergencial' issue11
    $ git mergetool
    
    # Cancelando merge
    $ git checkout master
    $ git merge issue11
    $ git merge --abort

    # Exibe arquivos que precisam de resolução de conflitos
    $ git ls-files -u
    $ git ls-files --unmerged

**Diff**

    # Verifica diferenças na branch atual
    $ vim MyServlet.java
    $ git difftool
    
    # Verifica diferençãs entre branches
    $ git checkout master
    $ git diff v1.1.2

**Revertendo arquivos**

    # Reseta arquivo
    $ git checkout -- MyServlet.java
    
    # Reseta arquivo
    $ git checkout MyServlet.java

**Revertendo commits locais**

    # Reseta branch
    $ git reset
    
    # Reseta arquivo
    $ git reset HEAD ProductDAO.java
    
    # Reseta para commit específico
    $ git reset --hard 7be6504
    
    # Reseta para commit específico
    $ git reset --hard 8a01849306c655ab418b7999b18d6ff5f43928b2
    
    # Reseta para estado da branch remota
    $ git reset --hard origin/master

    # Reverte para o último commit (reseta a staging area e o Working Directory)
    $ git reset --hard HEAD^ 

    # Reverte para o último commit (reseta a staging area e mas não o Working Directory)
    $ git reset --mixed HEAD^ 

    # Reverte para o último commit (não reseta a staging area e o Working Directory)
    $ git reset --soft HEAD^ 

**Revertendo commits empurrados**

    # Revertendo commit empurrado (cria commit de revert)
    $ git revert 9c7532f
    $ git push origin master

**Remove**

    # Remove arquivo
    $ git rm CustomerDAO.java
    
    # Remove arquivo forçado
    $ git rm -f CustomerDAO.java

**Movendo ou renomeando**

    # Renomeando
    $ git mv CustomerDAO.java CustomerDAOImpl.java
    
    # Movendo
    $ git mv CustomerDAO.java dao/CustomerDAO.java

**Ignorando arquivos**

    $ vim .gitignore
    
    **/.classpath
    **/.project
    **/target/
    **/.settings/
    **/.idea/
    **/*/.gitignore
    **/*.class

**Stash (Work In Progress)**

    # Cria stash
    $ git stash
    
    # Aplica stash e remove da pilha
    $ git stash pop
    
    # Lista WIP
    $ git stash list
    
    # Status do primeiro stash
    $ git stash show stash@{0}
    
    # Branch com WIP
    $ git stash branch issue12 stash@{0}
    
    # Apaga WIP
    $ git stash drop stash@{0}
    
    # Aplica stash mas não remove da pilha
    $ git stash apply

**Pesquisas em arquivos**

    # Sintaxe básica
    $ git grep "int i=10"
    
    # Line Number
    $ git grep -n "int i=10"
    
    # Somente na staging area
    $ git grep --cached "int i=10"
    
    # Ignore case
    $ git grep -i "CREATE INDEX"
    
    # Exibe somente o nome do arquivo
    $ git grep --name-only "CustomerService"
    
    # Em branch especifica com extensão específica
    $ git grep "setTimeout" branch7 -- *.js
    
    # Em todas as branches
    $ git rev-list --all | xargs git grep "CustomerServiceImpl"
    
    # Em todas as branches
    $ git grep "CustomerServiceImpl" $(git rev-list --all)

**Repositórios remotos**

    # Exibe informações do repositório remoto
    $ git remote show
    
    # Exibe informações do repositório remoto origin (default)
    $ git remote show origin
    
    # Verbose
    $ git remote show -v
    
    # Verbose
    $ git remote show -v origin
    
    # Adiciona novo repositório remoto
    $ git remote add novo git@bitbucket.org:foo/xpto.git
    
    # Altera a URL do repositório remoto
    $ git remote set-url novo  git@bitbucket.org:bar/foo.git
    
    # Remove referência do repositório remoto
    $ git remote rm old
    
    # Renomeia referência do repositório remoto
    $ git remote rename novo new

**Tags**

    # Exibe as tags existentes
    $ git tag
    
    # Cria tag leve
    $ git tag v1.0.0
    
    # Cria tag anotada
    $ git tag -a v1.1.1 -m 'Criando tag'
    
    # Empurra tags
    $ git push origin master --tags
    
    # Remove tag no repositório local
    $ git tag -d v1.0.0

**Log**

    # Exibe log
    $ git log

    # Exibe log em uma linha
    $ git log --oneline

    # Decorate e graph
    $ git log --decorate --graph --oneline
    
    # Exibe as modificações do commit
    $ git log -p
    
    # Lista por autor
    $ git log --author foo@bar.com
    
    # Busca por texto do commit
    $ git log --grep DAO
    
    # Busca por texto do commit exato
    $ git log -g --grep='Build 0051'
    
    # Exibe somente o nome do arquivo
    $ git log --name-only

    # Exibe o nome e o status do arquivo
    $ git log --name-status
    
    # Busca por commit de texto isEmpty
    $ git log -G "isEmpty" --oneline

    # Busca entre datas na branch master e não exibe merges
    $ git log --author=alexandre --before="2015-06-24 23:59:59" --after="2015-06-24 00:00:00" --no-merges --branches=*/master

    # Log do HEAD
    $ git reflog

**Garbage Collector**

    # Executa o garbage collector
    $ git gc

    # Executa o garbage collector suprimindo objetos antes da data atual (default é de 2 semanas)
    $ git gc --prune=now

    # Conta os objetos
    $ git count-objects

    # Busca por objetos inalcançáveis
    $ git fsck --unreachable
