# dioGitBootcampInter

  Esse repositorio foi criado para acomanhar as aulas do curso de git.

### GIT e sua importancia

 * o controle de versionamento do projeto é importante, o GIT é uma ferramenta que fornece meios para controlar de forma melhor o versionamento de arquivos.
 * Linus Torvalds, 1995, criado para monitoramento e versionamento de codigo.
 * GIT <> GIT HUB <> GITLAB <> GITBUCKET
 
* Vantagens levantadas:
 * 1 - Controle de Versão
 * 2 - Armazenamento em nuvem
 * 3 - Trabalho em Equipe
 * 4 - Melhorar seu código
 * 5 - Reconhecimento


### Comandos de Terminal

Diferenças e semelhanças entre os terminais dos sistemas operacionais.
* caso os comandos executem com sucesso, muitos não vão retornar nada.

| windows -cmd  |  linux - tty  |   descricao       |
| ------------- | ------------- | ----------------- |
| dir           | ls            | lista arquivos    |
| cd <pasta>    | cd <pasta>    | navegacao pastas  |
| cls           | clear         | limpa tela        |
| tab           | tab           | autocompleta      |
| mkdir         | mkdir         | cria pasta        |
| echo > arq.js | toutch arq.js | cria arquivo      |
| del           |               | remove arquivo    |
| rmdir /S/Q    |               | remove diretorio  |
|               | rm -rf        | remove tudo       |

### Links
`<GITHUB>` : <https://github.com>
`<GIT   >` : <https://git-scm.com>

### Conceitos Fundamentais do GIT

#### SHA1

Sigla SHA significa Secure Hash Algorithm desenvolvido pela NSA (Agência de 
segurança nacional dos EUA), é um conjunto de funções criptográficas.
* Geram um conjunto de caracteres de 40 dígitos único.
* Forma curta de representar um arquivo 

```elm
    echo "ola mundo" | openssl sha1
    > (stdin)= f9fc856e559b950175f2b7cd7dad61facbe58e7b
```

#### Objetos fundamentais

* BLOBS - bolhas
Armazena: o tipo, o tamanho do arquivo \0 conteudo do arquivo : metadados do arquivo no GIT

```elm
    echo 'conteudo' | git hash-object --stdin
    fc31e91b26cf85a55e072476de7f263c89260eb1
    
    echo -e 'blob 9\0conteudo' | openssl sha1
    fc31e91b26cf85a55e072476de7f263c89260eb1
```

* TREES - arvores
Armazena: Blobs, \0, nome do arquivo : responsavel por montar a estrutura de onde esta localizado o arquivo : metadados da estrutura de diretorios e arquivos criptografados em Sha1 ex.: `\src\lib\simplegit.rb`

```flow
st=>operation: TREE:src
op3=>operation: TREE:lib
op4=>start: BLOB:simplegit.rb

st->op3->op4
```

* COMMITS
Armazena: Trees, parente, autor, mensagem e timestamp, tamanho e criptografado os metadados em SHA1
 * dessa forma é montado a linha do tempo do código.

#### Sistema Distribuido e com Segurança

Distribuido: pode ter o repositorio na nuvem com o codigo mais recente (master|main) e pode estar na máquina de 'n' colaboradores com versões confiaveis da aplicação.
 

#### FLUXO DE OPERAÇÃO*
 Workspace - Arquivos na area de trabalho
 Index - Area temporaria
 Head - Repositorio Local
 REMOTO - Repositorio Remoto

|comando       | base | Caminho percorrido pelo arquivo   |
| ------------ | ---- | --------------------------------  |
|commit -a     | >->- | workspace transfere para o Head   |
|add           | >>-- | workspace transfere para o Index  |
|commit        | ->>- | Index transfere para o Head       |
|checkout HEAD | <-<- | Head transfere para workspace     |
|checkout      | <<-- | Index transfere para workspace    |
|diff          | //-- | COMPARA o Index com o workspace   |
|diff HEAD     | /-/- | COMPARA o Head com o workspace    |
|push          | -->> | Head transfere para REMOTO        |
|pull          | <--< | REMOTO transfere para workspace   |
|fetch         | --<< | REMOTO transfere para Head        |

### Comandos GIT

`git --version` -> exibe a versão
`git init` -> inicializa o versionamento
`git add *` -> transfere para Index todos os arquivos
`git add -A` -> transfere para Index todos os arquivos modificados
`git add *.js`-> transfere para Index todos os arquivos de determinada extensão
`git commit` -> transfere para o HEAD
`git commit -m "comenta"` -> transfere para o HEAD sem abrir o editor para comentar
`git commit --amend -m "comentario novo"` -> altera o comentario do ultimo commit
`git status` -> verifica se existe algo não comitado na area temporaria
`gitk` -> ferramenta grafica para visualizar o projeto
`git branch` -> visualiza os branchs disponiveis no repo
`git checkout g` -> cria um branch para não cagar o projeto
`git checkout <master>` -> retorna para o "branch" mestre do projeto
`git merge <branch>`-> faz um merge do branch qual está situado (geralmente master) com a versao do branch que deseja adicionar, geralmente quando tudo deu certo e vamos colocar o codigo desenvolvido em produção
`git branch -d <branch>`-> remove o branch 
`git log` -> visualiza o log de commit do git

`git remote add origin <endereço do repositorio remoto>` -> adicionar o remoto no projeto
`git push -u origin master` -> push no remoto
`git pull` -> tras do remoto direto para o workspace
`git fetch --all` -> tras os branchs do remoto ??? (não deu pra perceber utilidade)

`git log --oneline`
`git log -p`
`git log --pretty="parametros de formatação"`
