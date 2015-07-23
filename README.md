**Git by Example**
------------------

**Configuração**

    # Configura usuário
    $ git config --global user.name "Alexandre Arcanjo de Queiroz"
    
    # Configura e-mail
    $ git config --global user.email alexandre.queiroz@live.com
    
    # Configura difftool Meld
    $ git config --global diff.tool meld
    $ git config --global difftool.prompt false
    
    # Configura mergetool Meld
    $ git config --global merge.tool meld
    $ git config --global mergetool.keepbackup false
    
    # Configura post buffer size
    $ git config --global http.postBuffer 524288000
    
    # Configura para ignorar verificação SSL
    $ git config --global http.sslVerify false
    
    # Configura line number no git grep
    $ git config --global grep.lineNumber true
    
    # Exibe configurações global
    $ git config --global --list

    # Exibe configuração do sistema
    $ git config --system --list

    # Exibe configurações local
    $ git config --local --list

    # Remove configuração
    $ git config --global --unset my.own.config

    # Configura commit template
    $ git config --global commit.template $HOME/.gitcommitmsg.txt

    # Configura rebase depois do git pull
    $ git config --global pull.rebase true

**Criando repositório**

    # Cria repositório git
    $ git init

**Clonando repositório**

    # Clona repositório com todas a branches
    $ git clone https://github.com/foo/bar.git
    
    # Clona uma branch específica do repositório
    $ git clone -b v1.1.2 https://github.com/foo/bar.git

**Status**

    # Status do repositório local
    $ git status

**Adicionando arquivos**

    # Adiciona arquivo na staging area
    $ git add MyServlet.java
    
    # Remove somente da staging area
    $ git rm --cached MyServlet.java

**Commit**

    # Efetua commit
    $ git commit
    
    # Informa mensagem
    $ git commit -m '#1234 comment: correcao de estrutura de dados'
    
    # Atalho para add
    $ git commit -am '#4567 comment: correcao da configuracao do ActiveMQ'
    
    # Cancela último commit
    $ git reset HEAD^
    
    # Cancela último commit
    $ git reset HEAD~1

    # Emenda último commit
    $ git commit --amend

    # Exibe informação de um commit específico
    $ git show 3e0c4a6

**Push** 

    # Empurra commits para servidor
    $ git push

    # Empurra commits para origin e branch específicos
    $ git push origin master

    # Empurra commits em uma nova branch e altera o track da branch atual
    $ git push origin newBranch
    $ git branch --set-upstream newBranch origin/newBranch

    # Empurra commits em uma nova branch e altera o track da branch atual
    $ git push -u origin newBranch

**Push forçado**

    # Reseta para commit  específico e faz push forçado (não recomendado)
    $ git reset --hard 8a01849306c655ab418b7999b18d6ff5f43928b2
    $ git push -f origin v1.1.2

**Diff**

    # Verifica diferenças com o difftool configurado
    $ vim MyServlet.java
    $ git difftool

    # Exibe diferenças (somente o nome do arquivo) entre a branch remota v1.1 e a branch remota master
    $ git diff --name-only origin/v1.1 origin/master 

    # Exibe diferenças (nome e status) entre a branch remota v1.1 e a branch remota master
    $ git diff --name-status origin/v1.1 origin/master 

    # Exibe diferenças (nome e estatus) entre a branch remota v1.1 e a branch remota master
    $ git diff --name-status --diff-filter=DA origin/v1.1 origin/master 

    # Exibe diferenças entre a branch local master e a branch remota master
    $ git diff master origin/master

    # Exibe arquivos modificados entre o commit atual e determinado commit (2cb4c91)
    $ git diff --name-only 2cb4c91..HEAD

    # Exibe somente os arquivos deletados entre o commit atual e determinado commit (2cb4c91)
    $ git diff --name-only --diff-filter=D 2cb4c91..HEAD

    # Abre o difftool configurado para realizar diff entre a branch remota v1.1 e a branch remota master
    $ git difftool origin/v1.1 origin/master

    # Abre o difftool configurado para realizar diff entre a branch local master e a branch remota master
    $ git difftool master origin/master

**Atualizando repositório local**

    # Atualiza repositório
    $ git fetch
    $ git merge origin/master
    $ git mergetool

    # Atualiza e faz merge automaticamente
    $ git pull
    $ git mergetool

    # Atualiza repositório e remove referências que não existem no remoto
    $ git fetch --prune
    
    # Atualiza repositório e remove referências que não existem no remoto
    $ git pull --prune

**Branch**

    # Exibe branches
    $ git branch
    
    # Exibe branches remotas
    $ git branch -r
    
    # Exibe todas as branches
    $ git branch -a
    
    # Cria branch e faz o checkout
    $ git branch issue11
    $ git checkout issue11
    
    # Cria branch e faz o checkout
    $ git checkout -b issue11
    
    # Cria branch a partir de commit
    $ git branch foo 691679d8b0c1c7b5a1528ffc94be5d15bbd5e420
    $ git checkout foo

    # Cria branch a partir de tag
    $ git checkout -b newBranch myTag
    
    # Remove branch local
    $ git branch -d issue11
    
    # Exibe origem da branch no reflog
    $ git reflog show v1.1.2

    # Cria branch e seta o remote upstream
    $ git checkout -b remoteBugFix --track origin/stable-3.2

    # Seta remote upstream da branch atual
    $ git branch --set-upstream-to origin/stable-3.2

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
