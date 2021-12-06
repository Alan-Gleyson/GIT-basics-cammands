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
   para o main do repositório remoto origin, é usado somente essa vez.
  - [ ] `git push origin main` - Para realizar push de commit.


  ### ___checando reposotório remoto___

  >``git remote`` - retorna o nome do repositório remoto "origin".
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
