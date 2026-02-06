# 🎁 Extra: Configurar o Prettier Ignore

Algo aconteceu no meu ambiente de desenvolvimento que foi diferente do que aconteceu no ambiente de alguns outros alunos quando executaram o script `npm run lint:check` ou `npm run lint:fix`. Nesta aula vamos investigar o que aconteceu e o que fazer para deixar tudo sincronizado 💪

### Link para o commit feito na aula

-   [adiciona `.prettierignore`](https://github.com/filipedeschamps/clone-tabnews/commit/662bf5936245f3af53f3e70436a43bb48c49f12f)

## 🛑 Breaking Change

O `prettier` a partir da versão `3.0.0` mudou o seu comportamento e por padrão está utilizando o conteúdo dentro `.gitignore` para também ignorar o linting de estilização 🎉 Isto foi anunciado [neste comunicado](https://prettier.io/blog/2023/07/05/3.0.0.html#ignore-gitignored-files-by-default-14731httpsgithubcomprettierprettierpull14731-by-fiskerhttpsgithubcomfisker).

Caso você queira simular o comportamento da aula, basta instalar o módulo na versão `2.8.8` da seguinte forma:

    npm install prettier@2.8.8
    

## Perguntas frequentes

**Por que o Prettier não passou pela pasta `.next` mesmo sem criar o `.prettierignore`?**

Isso aconteceu por conta da _Breaking Change_ mencionada acima.

A partir da versão `3.0.0`, o Prettier passou a utilizar o próprio arquivo `.gitignore` para decidir quais arquivos devem ser ignorados. Como a pasta `.next` já está listada no `.gitignore`, o Prettier automaticamente a ignora.

Se você quiser reproduzir o erro mostrado na aula, pode instalar a versão `2.8.8` do Prettier.

* * *

**Por que o texto entre crases some na mensagem de commit quando uso aspas duplas?**

Isso acontece porque quando colocamos algo entre crases dentro de aspas duplas, o terminal interpreta o que colocamos entre as crases como um comando a ser executado. Isso é um recurso do terminal chamado de `command substitution`.

Por isso, ao escrever:

    git commit -m "adiciona `.prettierignore`"
    

O terminal tenta executar `.prettierignore` como um comando (o que resulta em um erro, visto que esse não é um comando válido). Como nada é retornado, a mensagem fica apenas `adiciona`.

Para contornar isso, você deve usar aspas simples `''` no lugar de aspas duplas `""`:

    git commit -m 'adiciona `.prettierignore`'
    

Você pode ver mais detalhes [neste comentário](https://curso.dev/alunos/Andrei/0a619c57-56da-4bda-ad7a-69a3cbc912a1).

* * *

**Ainda preciso criar o `.prettierignore` se estou usando Prettier 3.0+?**

Fica a seu critério. Você pode continuar na versão mais atualizada sem criar o `.prettierignore`, já que o Prettier agora segue a lista de arquivos do `.gitignore` na hora de decidir o que vai ser ignorado.

Porém, o arquivo `.prettierignore` pode ser útil caso você queira ignorar algo que o `.gitignore` não está ignorando. Esse inclusive é o caso do repositório do [TabNews](https://github.com/filipedeschamps/tabnews.com.br/blob/main/.prettierignore) atualmente.

Recomendo dar uma olhada [nessa thread](https://curso.dev/alunos/imthiagomartins/d2f3fb18-9a26-4e5a-a388-d73e323ff8e1) para mais detalhes. 🤝

* * *

**Qual a diferença entre `git add .` e `git add -A`?**

A principal diferença é:

-   **`git add .`** só irá adicionar o conteúdo modificado da pasta em que você estiver no momento.
-   **`git add -A`** irá adicionar todo o conteúdo modificado do repositório, independentemente de qual pasta você esteja.

Então o ideal é usar o `git add -A`, pois você pode estar dentro de alguma subpasta sem perceber e acabar não adicionando tudo.

Se você executar na raiz do projeto, não terá diferença entre os dois comandos.

* * *

**Qual a diferença entre o Prettier instalado via npm e a extensão do VSCode?**

Cada um tem uma função diferente:

-   **Extensão do Prettier no VSCode:** É o que vai permitir a formatação automática ao salvar o arquivo. Ela te ajuda durante o desenvolvimento.
    
-   **Prettier instalado via npm:** Nos permite automatizar a formatação (ou checagem dela) através de um script, seja localmente ou no CI (Continuous Integration), como faremos mais para frente no curso.
    

Usando os dois, temos uma garantia dupla de que o código estará sempre formatado corretamente.

* * *

**Por que o destaque com crase não aparece mais com fundo cinza no GitHub?**

Houve uma mudança na interface do GitHub que deixou de exibir esse sombreado cinza na página principal do repositório. O destaque agora fica apenas na alteração da fonte.