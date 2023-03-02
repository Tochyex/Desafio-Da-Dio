## Git e GitHub

Apesar de os dois terem o nome bem parecido os dois são bem diferentes um do outro, o **GIT** em resumo é um sistema que vai listar, criar, apagar diretórios enquanto o **GITHUB** é um modo de guardamos o nossos códigos privadamente ou então publicamente, quando o mesmo for guardado publicamente outras pessoas podem ver os códigos e ajudar você a deixar ele ainda melhor, seja deixando mais limpo, usando outra função, ou de outra forma.

## Git

Quando usamos o git temos alguns comando diferente quando usamos ele no windows ou então no Linux que são os sistemas operacionais mais usados, vou listar alguns comandos e suas funções.

**Windows**

Cd, dir, mkdir, del/rmdir

Iunix

cd, ls, mkdir, rm -rf

#### Funções dos comandos 

**Cd=** faz entrar no diretório, e usando cd .. você volta um diretório.

**Dir** = vai listar o que tem dentro do diretório mostrando na tela.

**Mkdir** = cria um diretório novo. 

**del** = deleta os arquivos que estão dentro do diretório. 

**rmdir** = vai apagar o nosso diretório mas se esse diretório tiver algum arquivo ele não consegue apagar, então usamos uma flag para que mesmo se esse diretório tiver arquivos ele apaga mesmo assim, que é o rmdir (nome da pasta) /S /Q chamando essa flag apagamos tudo.

**cls**= esse comando limpa a tela, sempre tente deixar a tela limpa pra ter mais noção do que se esta fazendo.

#### Sha1

Vamos falar um pouco sobre o sha1 que é um sigla que significa "Secure hash algorithm"(Algoritmo de hash seguro), o sha1 é um algoritmo de encriptação  que gera um conjunto de caractere de identificação de 40 dígitos, caso eu crie algum arquivo ele vai me gerar um conjunto de 40 caractere, caso aja alguma modificação ele vai nos gerar mais um conjunto de caractere, caso nós mudemos o arquivo para o que era antes ele vai gerar o primeiro conjunto de caractere, então o sha1 é uma forma rápida e segura identificar arquivo. Podemos criar esse conjunto da seguinte forma.



**echo "olá mundo" | openssl sha1 

| >(stdin): f9fc856e55969501........ ate os 40 caracteres.

#### Objetos internos do Git 

O git lida com objetos ele manipula através de objetos então os arquivos são armazenado em um objeto chamado **Blob**. ele guarda meta dados ele consegue guardar o tipo de objeto, o tamanho da string ou do arquivo entre outros.

Temos que ter cuidado na hora de gerar o sha1 porque como o arquivo vai estar dentro do blob ele pode gerar outro sha1 vou dar exemplos.

> echo 'conteúdo' | git hash-object --stdin
>
> | > 40 caracteres

fazendo essa função irá mostrar o sha1, usamos a flag stdin porque o git hash espera receber um arquivo e a flag esta avisando que vai apenas inserir uma mensagem e caso usarmos o **openssl** ele vai nos gera outro tipo de sha como no exemplo abaixo

> echo -e 'conteúdo' | openssl sha1
>
> | > 40 caracteres diferente do primeiro

Basicamente a gente pediu pra encriptar o conteúdo fora da blob então ele nos mostra outro tipo de sha.

Para ele encripte dentro da blob usamos a seguinte função

> echo -e 'blob 9/0conteudo' | openssl sha1
>
> | > 40 caractere

 como eu citei ali em cima a nossa função tem o tipo de objeto, o tamanho da string e o conteúdo.

#### Trees = arvores 

As trees também guardam meta dados mas diferente das blobs ela guarda o nome e o sha1 dos arquivos enquanto as blobs apenas o sha1 , uma trees pode apontar para outras blobs ou então outras trees.



Tree  - lib :arrow_right: tree - simplegit.rb :arrow_right:  blob	

:arrow_down:

blob 



**Commit**

Commit = esse objeto é o que vai ligar todos outros

tree = pode apontar outra tree ou uma blob

parente = é o ultimo commit que foi dado antes dele

autor = é o dono do arquivou ou código, o criador

mensagem = aponta uma mensagem

timestamp = o commit guarda também a hora e a data de quando foi criado

E isso é o que o commit guarda como metadados



O legal é que como o commit também possui um sha1 se eu alterar alguma coisa que ele esta ligado ele vai mudar todo o sha1 de todos, então não vai ter como mudar nada no arquivo sem que você saiba.



#### Chave SSH

A chave ssh é um processo que cria uma conexão encriptada entre 2 maquinas de forma segura, sendo assim teremos 2 chaves 1 publica e 1 privada. E iremos usar a chave publica para se conectar ao servidor do github



#### Criando a chve SSH

ssh- keygen -t ed25519 -C kaiquedeveza@hotmail.com



Logo depois o git criar essa chave na pasta .ssh mais pra frente podemos mudar. Logo depois dando enter ele vai pedir uma senha e ai vai dizer onde a chave foi salva criando também a chave publica com o nome  .pub no final e cria uma **finger print(um tipo de identidade para a chave)**, o ed25519 é o tipo de criptografia que você ai usar ali no código.

Depois disso podemos ir até a pasta onde foi criada a .ssh e abrindo com o git bash listamos os arquivos usando o comando **ls** e vai ter dois arquivos **id_ed25519(nossa chave privada)** e outro chamado **id_ed25519.pub(nossa chave publica)**.

Usando o comando **cat id_ed25519.pub** ele vai nos mostrar o conteúdo da chave, depois usamos o conteúdo mostrado no github na parte de chaves ssh.

Depois usamos o comando **eval $(ssh-agent -s)** que um inicializador que lida com as chaves.

Logo depois usamos o **ssh-add id_ed25519** após fazermos isso entregamos a chave pro agente e através disso toda mensagem criptografada que chegar com essa chave ele vai usar essa chave pra descriptografar a mensagem, logo após todo esse processo ele vai perguntar a senha que você criou lá no começo.



#### Clonando um repositório do github 

Podemos clonar repositórios usando o comando **git clone (e o link copiado em ssh ou https la no github).**

**Token de acesso pessoal**

A segunda forma de autenticação é indo no github e ir na parte de settigs/developers settings/personal acces tokens e se voce for usar as config padrão do git apenas a caixa marcada com o nome de repo basta depois disso é só copiar o link https do github e usar o comando **git clone(Link https) logo depois disso o github vai pedir o token criado pra logar e clonar o arquivo.

Podemos usar o comando **git init** no repositório para o git começar a gerenciar e versionar o código(novas versões e alterações).Precisamos também configurar algumas coisas já que mais pra frente iremos gerar um comit e ele sempre pede um autor



> git config --global user.email 'de preferencia use seu email cadastrado no github'
>
> git config -- global user.name 'também o nome criado no github'

   

#### Gerando um commit 

Usamos o codigo git commit -m 'commit inicial' e assim trazendo algumas info sendo uma delas o sh1 criado antes



#### Ciclo de vida no git 

No git assim que você cria um repositório ou um arquivo o git ainda não sabe que ele existe até você dizer pra ele que ele existe e esses tipos de arquivo nós chamamos ele de Untracked, e no git temos alguns "ciclo" que cada arquivo precisa passar sendo eles o Untracked que acabamos de citar, Unmodified, Modified e staged .



Unmodified: É o arquivo que não sofreu nenhuma modificação



Modified: É o arquivo que já sofreu alguma modificação



Staged: Nessa parte os arquivos já estão prontos para fazer suas determinada função eles ficam ali só esperando você dar os comando para eles 



Quando o arquivo está untracked e usando o comando **add** ele passa direto pro staged logo depois disso quando damos o **commit** ele fica unmodified e após mexer em alguma coisa no arquivo ele passa pra uodified e ai usamos o mesmo comando **add** e ele volta a ficar staged e o ciclo se repete. 



Usando o comando **git status** ele vai nos dizer se precisamos dar algum commit se tem algum arquivo modificado e etc, temos também o comando **mv** que move arquivos e usando ./nomearquivo/ ele busca outro repositório. 



#### Repositório no github 

Conseguimos linkar o git e o github, no github criando um novo repositório usamos um comando no git que é **git remote add origin(link que foi dado no github)**,e usando o git remote -v ele vai listar os repositórios cadastrados.

E usando o **git push origin main** ele manda o repositório para o github 



#### Resolvendo conflitos

Caso o nosso repositório for editado e tentarmos dar um push vai gerar um conflito por que o nosso repositório esta desatualizado , após abrir o arquivo e fazer as modi devidas vamos dar um commit, e usando o comando git pull origin master puxamos os arquivos do github que foi editado para nossa maquina para resolvermos o problema 

