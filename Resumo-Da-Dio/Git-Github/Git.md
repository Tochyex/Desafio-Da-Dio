## Git e GitHub

Apesar de os dois terem o nome bem parecido os dois são bem diferentes um do outro, o **GIT** em resumo é um sistema que vai listar, criar, apagar diretórios enquanto o **GITHUB** é um modo de guardamos o nossos códigos privadamente ou então publicamente, quando o mesmo for guardado publicamente outras pessoas podem ver os códigos e ajudar você a deixar ele ainda melhor, seja deixando mais limpo, usando outra função, ou de outra forma.

## Git

Quando usamos o git temos alguns comando diferente quando usamos ele no windows ou então no Linux que são os sistemas operacionais mais usados, vou listar alguns comandos e suas funções.

**Windows**

Cd, dir, mkdir, del/rmdir

**Linux**

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

O git lida 





