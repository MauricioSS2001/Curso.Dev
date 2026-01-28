# Fazendo commits de forma mais rápida

Neste vídeo vamos fazer várias coisas, inclusive nos colocar numa posição **problemática** porém **vida real** 🤝

De qualquer forma, o destaque da aula é um atalho para fazer novos `commit`, um atalho que possivelmente vai se tornar a forma padrão de você fazer eles 💪

### Links para os commits feitos na aula

-   [adiciona arquivo .nvmrc](https://github.com/filipedeschamps/clone-tabnews/commit/47ee07d14072f53a0be56e1a8e5be32a67c40f3b)
-   [adiciona os arquivos de manifesto](https://github.com/filipedeschamps/clone-tabnews/commit/3eddad8563eb2574a068179460b3a417bd99a7de)
-   [adiciona pagina inicial](https://github.com/filipedeschamps/clone-tabnews/commit/89ff7120bd42d4e2925eeb8e7b85410de4eb52a0)

## Perguntas frequentes

**Devo usar aspas duplas ou aspas simples ao passar a mensagem de commit no terminal?**

As duas opções terão o mesmo efeito, exceto se quisermos destacar alguma palavra especial (como o nome de uma função ou arquivo) na mensagem de commit lá no GitHub. Nesse caso, o destaque só funcionará se forem utilizadas aspas simples (`'`). Para esse destaque, nós podemos escrever a palavra entre acentos graves (`` ` ``). Por exemplo:

    git commit -m 'adiciona arquivo `.editorconfig`'
    

Será renderizado no histórico de commits do GitHub assim:

![](https://i.imgur.com/5wphMbb.png)

Fazer isso utilizando aspas duplas acaba ativando um recurso do terminal chamado [`command substitution`](https://curso.dev/alunos/Andrei/0a619c57-56da-4bda-ad7a-69a3cbc912a1), que interpreta o que é passado entre os acentos grave como um comando a ser executado, passando o que é retornado da sua execução como um argumento para um outro comando.

* * *

**Erro `rejected` ao fazer `git push` após usar `git commit --amend`**

Esse é o comportamento esperado após realizar um `amend`. E isso acontece porque no Git, um commit faz referência a outro commit em uma cadeia muito amarrada. É um histórico imutável, por isso ele tem a segurança total de onde os dados estão vindo e indo. Quando você faz o `amend`, você reescreve o histórico do repositório local e isso quebra esta cadeia, ao menos quando comparado entre o repositório local e o remoto. Nesta situação, o repositório remoto não sabe mais como encaixar em sua cadeia o commit que está vindo do repositório local.

Nesse caso simples, a melhor opção é usar o `git push --force`. Na próxima aula o Filipe explica como proceder nessa situação em detalhes. 🤝

* * *

**Terminal "travado" após executar `git log` ou `git log --stat`**

Alguns comandos do Git abrem um modo de visualização paginada. Isso acontece quando a lista de commits é muito longa e maior que a própria janela do terminal.

Nesse modo, você pode usar as setas do teclado para navegar para cima e para baixo. E para sair, basta apertar a tecla `q` (de "quit", que significa "sair").

* * *

**Como adicionar múltiplos arquivos de uma vez com `git add`**

É possível fazer isso pela linha de comando de algumas formas:

-   `git add -A` - adiciona todos os arquivos modificados, novos e deletados
-   `git add .` - adiciona todos os arquivos do diretório atual
-   `git add package*` - adiciona todos os arquivos que começam com "package" (usando padrão de nome)
-   `git add pages/*` - adiciona todos os arquivos dentro de uma pasta específica

O Filipe vai mostrar isso mais pra frente também.

* * *

**Como remover um arquivo do stage após `git add` (antes do commit)**

Se você adicionou arquivos ao stage por engano, não tem problema, você pode tirar o que quiser do palco antes de fazer o commit, executando o comando:

    git restore --staged nome-do-arquivo.js
    

Isso remove o arquivo do stage (palco), mas mantém as alterações no seu arquivo local.

Quando você digita `git status`, o próprio Git mostra o comando para realizar esta ação.

* * *

**Por que precisamos commitar o `package-lock.json` se ele é gerado automaticamente?**

Para entender a importância de enviar o `package-lock.json` para o repositório remoto, é preciso esclarecer qual é o seu papel e qual é a diferença dele para o `package.json`.

A pista está na palavra "lock", que significa "trava". O `package-lock.json` é uma versão "travada" do seu irmão, no que diz respeito à lista de dependências.

Mesmo instalando versões específicas de pacotes, o `package.json` ainda permite uma certa flexibilidade quando o comando `npm install` for executado para instalar as mesmas dependências do zero. Isso será explicado em detalhes quando o Filipe abordar o conceito de Versionamento Semântico.

Enquanto o ambiente de desenvolvimento permite essa flexibilidade, o mesmo não pode ser dito para outros ambientes como o de produção. Nesses ambientes, a flexibilidade para instalação de pacotes com pequenas atualizações pode levar a comportamentos inesperados e bugs.

O `package-lock.json` fornece uma versão fixa de todas as dependências e sub-dependências, para que em ambientes onde erros não podem ser tolerados, não tenhamos surpresas. Por isso também é importante mantê-lo no repositório remoto.

Se isso ainda não ficou 100% claro, não se preocupe. À medida que você progredir no curso, isso vai melhorar, e o Filipe mais para frente vai se aprofundar nesse assunto.