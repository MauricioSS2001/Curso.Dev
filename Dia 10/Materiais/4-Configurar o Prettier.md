# Configurar o Prettier

Nesta aula iremos passar um pente fino no assunto `Prettier` que é um dos **formatadores de código** mais famosos do mundo 💪

A princípio, o assunto `Prettier` é simples, e de fato é, mas esta simplicidade abre espaço para brechas numa estratégia mais madura sobre a **garantia** da estilização do código. Então como aqui no `curso.dev` minha missão é não deixar buracos no seu conhecimento, chegou a hora de estudar este assunto de forma **séria**, incluindo, preparar o projeto para que ele também seja um projeto **sério** 🤝

### Link para o commit feito na aula

-   [adiciona scripts `lint:check` e `lint:fix`](https://github.com/filipedeschamps/clone-tabnews/commit/0f6d6381cfddc536b2d3f5ed9758f9b026941a27)

## Perguntas frequentes

**Por que as caixinhas (`- [ ]`) não funcionam mais para mostrar o progresso da issue?**

Houve uma mudança na interface do GitHub após a gravação dessa aula. Agora, para ter essa indicação de progresso externa à issue, você precisa criar _sub-issues_, que vão funcionar como as tarefas a serem cumprindas. Nessa página [aqui](https://docs.github.com/pt/issues/tracking-your-work-with-issues/using-issues/adding-sub-issues) você encontra os detalhes de como trabalhar com elas.

Uma desvantagem desse novo recurso é que ele acaba "lotando" o repositório com muitas issues. Por isso, se você preferir usar as caixinhas (`- [ ]`) que o Filipe mostra no vídeo, você pode continuar fazendo o controle das tarefas dentro da issue "pai" mesmo, e para ver o progresso dela, é só entrar na página da issue e ver quantas caixinhas já foram marcadas.

Qual a diferença entre os comandos `git add .` e `git add -A`?  

A diferença é que o `git add -A` adiciona todos os arquivos do projeto inteiro ao stage, independentemente de qual subdiretório você esteja. Já o `git add .` considera apenas os arquivos do diretório atual e seus subdiretórios. Na prática, se você estiver na raiz do repositório, ambos os comandos terão o mesmo efeito.

Num cenário como o abaixo:

    /meu-projeto
      /img
        imagem.png
      index.html
    

Caso você altere o arquivo `index.html`, mas dê uma `cd img`, se você executar o `git add .` o arquivo `index.html` não irá para o `stage`. O que aconteceria se você usasse o `git add -A`.

Mensagem do commit com crases (`` ` ``) não aparece corretamente no GitHub  

Isso acontece por conta de um recurso do terminal chamado `command substitution`. Quando você usa aspas duplas, o terminal interpreta o conteúdo entre crases como um comando a ser executado, e não como texto literal.

Por isso, você deve utilizar aspas simples ao invés de aspas duplas na mensagem do commit:

    git commit -m 'adiciona scripts `lint:check` e `lint:fix`'
    

Se você já fez o commit com a mensagem errada, pode corrigir usando o comando `git commit --amend`. E se o commit com a mensagem errada já foi enviado para o GitHub, você vai precisar realizar o `push --force` demois do `amend`:

    git commit --amend -m 'adiciona scripts `lint:check` e `lint:fix`'
    git push --force
    

**Anteção:** Houve uma mudança na interface do GitHub que deixou de exibir o sombreado cinza para o destaque na mensagem do commit. O destaque agora fica apenas na alteração da fonte.

* * *

**Prettier não formata automaticamente ao salvar o arquivo**

Existem algumas causas comuns para esse problema:

**1\. Verifique as configurações do VSCode:**

-   O `Prettier` deve estar configurado como formatador padrão (`Default Formatter`)
-   A opção `Format On Save` deve estar habilitada
-   A opção `Auto Save` deve estar desligada (`off`)

**2\. Configurações conflitantes:**  
Verifique se não há configurações específicas por linguagem sobrescrevendo o formatador padrão. Acesse `Ctrl+Shift+P` > `Preferences: Open User Settings (JSON)` e verifique se há algo como:

    "[javascript]": {
        "editor.defaultFormatter": "vscode.typescript-language-features"
    }
    

Se houver, remova ou altere para `"esbenp.prettier-vscode"`.

**3\. Prettier esperando arquivo de configuração:**  
Nas configurações do VSCode, procure por `Prettier: Config Path`. Se estiver preenchido com `.prettierrc`, o VSCode esperará por esse arquivo. Deixe o campo vazio para usar as configurações padrão.

**4\. Reinicie o editor:**  
Caso você esteja usando o Codespaces, reinicie a sua instância. Se estiver no ambiente local, feche e abra o editor novamente.

**5\. Aba de configuração correta:**  
Se estiver usando Codespaces no VSCode local, certifique-se de alterar as configurações na aba `Remote [WSL: Ubuntu]` ou `Workspace`, e não apenas em `User`. 🤝

* * *

**Prettier formatou arquivos do `.next` e `node_modules`**

Isso pode ter acontecido porque você fez o commit das pastas `.next` e/ou `node_modules` antes de configurar o `.gitignore`. Mesmo que você tenha incluído elas no `.gitignore` depois, elas já estão sendo rastreadas pelo Git, então provavelmente isso fez o Prettier verificar elas também.

Para resolver isso, será preciso remover essas pastas do rastreamento do Git. Caso esse tenha sido o seu caso, pedimos que você envie suas alterações locais mais recentes para o GitHub e coloque aqui o link do seu repositório, que nós vamos te ajudar com isso. 🤝

* * *

**Qual a diferença entre o EditorConfig e o Prettier?**

Eles não fazem exatamente as mesmas coisas e se complementam para garantir a consistência da formatação no projeto:

**EditorConfig:**

-   Orienta o editor na formatação do código **à medida que você vai digitando**
-   Atua **antes de salvar** o arquivo
-   Funciona através da extensão do VSCode
-   Foca na ferramenta/IDE

**Prettier:**

-   Formata os arquivos **depois de salvá-los**
-   Realmente modifica o código, reformatando-o de acordo com as regras definidas
-   Pode ser executado via linha de comando (`npm run lint:fix`)
-   Foca em uma sintaxe definida

**Atenção:** Só faz sentido usar os dois se ambos estiverem seguindo os mesmos padrões. Configurações conflitantes entre eles podem causar comportamentos indesejados.

O Prettier também considera o arquivo `.editorconfig` em suas formatações, além de possuir diversas configurações por padrão. Você pode ver na [documentação](https://prettier.io/docs/en/options) quais são as opções e qual é o padrão de cada uma. 🤝