# `GIT comandos básicos`

### ___inicializando repositório___

criate folder on terminal

  | comando | comportamento |         
  --- | ---
  `mkdirin <nome_da_pasta>` | cria diretório|
	`cd <nome_da_pasta>/` | abre o diretório
  git init | inicializar e enchergar mudanças dentro do project
	ls -la | mostra diretórios ``.git``
	cd .git | abre o diretório oculto ``.git``
	ls | mostra pastas


###  ___config___

  > `git status` - reporta status atual
  >
  > `git config user.name` - mostra nome de usuário
  >
  > `git config user.email` - mostra email
  >
  > `git config core.editor` - mostra o editor usado
  >
  > `git config --list` - info gerais
  >
  > `git config --global <user.name ou user.amail ou core.editor>`
  >	configura um esses parâmetros


  ### ___alias___
  ```
  git config --global alias.<apelido-do-comando> <comando-a-ser-substituído>
  ```

  - função presente no **GIT** e **unix**, permite criação de
    atalhos para os comandos


  ### ___ligando repositório local ao remoto___

  ```
  git remote add origin <https://github.com/your_user/your_repository.git>
  git branch -M main
  git push -u origin main
  ```
  Notes:
  - [ ] O `-u` "trackea" o path do upload, vai de branch main local,
   para o main do repositório remoto origin.
  - [ ] `-u` É usado somente essa vez. Para realizar push de
  commit use `git push origin main`.


  ### ___checando reposotório remoto___

  >`git remote` - retorna o nome do repositório remoto "origin".
  >
  >`git remote -v` - info de _'fetch'_ e _'push'_.


  ### ___clonando repositório___

  ```
  git clone <link_repositório_pra_clonar> <novo_nome_para_repositorio_clonado>
  ```

  * link SSH é mais rápido.
  * Executar em uma pasta fora do seu repositório.
  * Pode clonar outro reporitório mas, enviar as mudanças
    somente funciona no reporitório próprio.


  ### ___fork de repositório___

  * É uma cópia de um projeto alheio.
  * Podendo realizar contribuições (alterações).
  * Informando as alterações feitas ao dono do projeto por Pull Request,
    que irá decidir aceitar ou não.  
  * click botão de fork no reporitório desejado no GitHub - escolhe o local
    para fork do reposotório.



  ###  ___ciclo entre os status dos arquivos___

  - **UNTRACKED**. Para o GIT esse arquivo ainda não existe.
  	até que seja adicionado à área de stage usando `git add <file>`

  - **UNMODIFIED**. Depois de adicionado o arquivo ao GIT mas
  	ainda sem alteração.
    <!--Nesse momento está pronto para ser comitado
  	*POR SE TRATAR DA CRIAÇÃO DO ARQUIVO*.-->
  O arquivo pode ser removido de `UNMODIFIED`
  	e voltar ao estado de `untracked`.


  - **MODIFIED**. sai de unmodified depois de qualquer alteração,
  	não pode ser comitado nesse estado. Deve ser adicionado antes ->
  	`git add <file>`

  - **STAGED**. depois de modificado e feito esse hash (versão) ele fica na
    área de stage. será enviado para o controle de versão se commitado.

  - **COMEBACK to UNMODIFIED**.
  	depois de 'commitada' a versão. Esse arquivo é
  	classificado como unmodified novamente nesse ponto não pode ser commitado
  	enquanto não for aterado novamente e added.


### ___git log___


> `git log` - Mostra para cada commit
> - [ ] commit: hash
> - [ ] author:
> - [ ] Date:
>
> `git show <numero hash do commit obtido no git log>` -
>			mostra all mudanças feitas pelo commite.
>
> `git diff` -
>			mostra mudanças antigas e as ainda não commitadas.
>
> `git diff --name-only`
>				show somente <nome> dos arquivos modificados - there is many files.
>
> `git log --decorate` -
>		branch to branch,
>		 se houve Merge.
>
> `git log --author="partes do nome"`
>
> `git log --graph` -
>		mostra timeline das branch e commit graficamente.
>
> `git shortlog` -
>		nome autor <qtd de commit>
>		 msg dos commit.
>
> `git shortlog -sn` -
>		<qtd de commit> nome author.


### ___desfazendo mudanças no modified___

(MODIFIED _**não added**_, desfaz modificação)
`git checkout <nome_do_arquivo>` ou

`git restore <nome_do_arquivo>` retorna ao estado anterior à modificação.

(MODIFIED _**added**_, _**staged**_) `git reset HEAD <name_do_arquivo>`
retira o arquivo do staged (to unstage)


### ___stash___

> `git stash` - guarda _{indexa}_ mudanças ainda não commitadas em um  arquivo,
>  _work in progress - **WIP**_, podendo ser
>	 acessado quando se desejar.
>
> `git stash apply` - aplica as mudanças que foram salvas no stash.
>
> `git stash list` - mostra uma lista dos stash salvos.
>
> `git stash clear` - limpa todos os stash salvos.


### ___commit___

> `git commit -am "aqui msg sobre alteração"`
>  - faz commit de file MODIFIED sem usar antes _**git add <file>**_
>
> `git commit -m "aqui a msg informando do que se trata a alteralção"`
>  - commita um arquivo já staged
>


### ___desfazendo commits___

```
git reset --soft <numero_hash_commit_anterior_ao_commit_q_será_desfeito>
```

- **remove o commit**, e retorna "1 nível abaixo", ou seja, **para a area de
staged, com** as **modificações comitadas ateriormente**, pronto pra ser
commitado again.


```
git reset --mixed <numero_hash_commit_anterior_ao_commit_q_será_desfeito>
```

- **remove o commit** e retorna "2 níveis abaixo", ou seja,
o arquivo **retorna** para **unstage**, **com** as **alterações anteriores**,
prontas para serem add novamente para área staged .
 - [ ] Importante: altera o hitórico de commites <!--evitar usar se já tiver
 sido commitado no repositório remoto-->

```   
git reset --hard <numero_hash_commit_anterior_ao_commit_q_será_desfeito>
```

- **"mata" o commit**, volta "3 níveis abaixo" ou seja, **apaga** junto
  com as **alterações** **feitas** no commit e retorna ao estado antes
  dessa modificação.


  ### ___branch , merge, rebase___
   `git checkout -b <nome_branch>` - create a new branch

  * `Branch` é um **ponteiro móvel** que leva a um commit  **[main] -> [commit]**


  | COMANDOS | COMPORTAMENTO |
  --- | ---
  `git branch` | lista e informa o branch em uso
  `git checkout <nome_branch_existente>` | alterna branch, para o branch nomeado
  `git branch -D <branch_to_DELETE>` | DELETA um branch

  ### ___merge___
  Uni as alterações dos branch

  `git merge <nome-branch-para-merge>`
  - uso em caso de pull request, onde é necessãrio olhar junção de recursos.


  * **cria** um **novo commit** com alterações do novo branch e **uni** com
    a última válida
    do **main**.


  ### ___rebase___
  Move o commit para a frente da fila e apaga o commit (ramificado) do hisórico.

  `git rebase <nome-branch-para-merge>`

  Caso seja necessário alterar e ir comitando, sem precisar juntar com outros.

  * tanto o main qnt a branch rebesed apaontam agora para esse commit.


  ### ___reverte___

  `git reverte <hash do commite a ser revertido>`

  Caso ocorra um bug após um commit usa-se `git reverte`, pra reverter o commit
  ao estado anterior às modificações em um novo sem descartar o bugado.
  O novo fica na frente do bugado, podendo dar **checkout** no bugado pra voltar
  a esse estado e
  fazer o Debug


  ### ___.gitignore___

  Funciona como arquivo de texto (o "ponto" significa arquivo oculto)

  Cotêm padrões para **não trackear** arquivos, **impedindo o compartilhamento**
  por extensão ou arquivos específicos, para tal, o arquivo `.gitignore` deve
  conter as extensões `*.<extensão>` ou `<nomes>.<extensão-do-arquivo>`

  - **Por extensão:**
    Ex: _`*.json` (todos os json não aparecerão no git status)_

  - **Por arquivo específico:**
  	EX.: `db.xls` somente o arquivo `db.xls` não aparecerá


  A collection of useful .gitignore templates
  https://github.com/github/gitignore


  ### ___Versionamento através de TAGs___

Usado para criar um número de versão e
anotaçães sobre release no repositório remoto

`git tag -a <n°release> -m <"message">`

`git tag` mostra as ___tags___ existentes (n° das versões)

_para **subir** ao GitHub_
  `git push origin main --tags`


### ___Apagando tags e branches___

apagando no reporitório local:

___tag___ -  `git tag -d <tag> `

___branche___ - `git branch -D <branch>`

apagando no reporitório remoto:

___tag___ - `git push origin :<tag>`

___branche___	- `git push origin :<branch-name>`
