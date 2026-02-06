# Configurar o EditorConfig

O [EditorConfig](https://editorconfig.org/) é um **Configurador de Editor** e por ele a gente vai definir regras **fundamentais** de como o seu **Editor** deve se comportar como, por exemplo, qual a largura da indentação do código, se será uma indentação mais curta ou mais comprida e se nela deve usar o caractere de `espaço` ou `tab`. Mas importante destacar que essas regras irão acontecer **antes** de você salvar um arquivo... guarde esta informação para a próxima aula 🤝

### Link para o commit feito na aula

-   [adiciona arquivo `.editorconfig`](https://github.com/filipedeschamps/clone-tabnews/commit/75832d3355c0632465a5509f3c08b00873bfb337)

## Perguntas frequentes

**Mensagem do commit com crases (`` ` ``) não aparece corretamente no GitHub**

Isso acontece por conta de um recurso do terminal chamado `command substitution`. Quando você usa aspas duplas, o terminal interpreta o conteúdo entre crases como um comando a ser executado, e não como texto literal.

Por isso, você deve utilizar aspas simples ao invés de aspas duplas na mensagem do commit:

    git commit -m 'adiciona arquivo `.editorconfig`'
    

Se você já fez o commit com a mensagem errada, pode corrigir usando o comando `git commit --amend`. E se o commit com a mensagem errada já foi enviado para o GitHub, você vai precisar realizar o `push --force` demois do `amend`:

    git commit --amend -m 'adiciona arquivo `.editorconfig`'
    git push --force
    

**Atenção:** Houve uma mudança na interface do GitHub que deixou de exibir o sombreado cinza para o destaque na mensagem do commit. O destaque agora fica apenas na alteração da fonte.

* * *

**Devo usar aspas duplas ou aspas simples ao passar a mensagem de commit no terminal?**

As duas opções terão o mesmo efeito, exceto se quisermos destacar alguma palavra especial (como o nome de uma função ou arquivo) na mensagem de commit lá no GitHub. Nesse caso, o destaque só funcionará se forem utilizadas aspas simples (`'`). Para esse destaque, nós podemos escrever a palavra entre acentos graves (`` ` ``). Por exemplo:

    git commit -m 'adiciona arquivo `.editorconfig`'
    

Será renderizado no histórico de commits do GitHub assim:

![](https://i.imgur.com/5wphMbb.png)

Fazer isso utilizando aspas duplas acaba ativando um recurso do terminal chamado [`command substitution`](https://curso.dev/alunos/Andrei/0a619c57-56da-4bda-ad7a-69a3cbc912a1), que interpreta o que é passado entre os acentos grave como um comando a ser executado, passando o que é retornado da sua execução como um argumento para um outro comando.

* * *

**Por que as caixinhas (`- [ ]`) não funcionam mais para mostrar o progresso da issue?**

Houve uma mudança na interface do GitHub após a gravação dessa aula. Agora, para ter essa indicação de progresso externa à issue, você precisa criar _sub-issues_, que vão funcionar como as tarefas a serem cumpridas. Nessa página [aqui](https://docs.github.com/pt/issues/tracking-your-work-with-issues/using-issues/adding-sub-issues) você encontra os detalhes de como trabalhar com elas.

Uma desvantagem desse novo recurso é que ele acaba "lotando" o repositório com muitas issues. Por isso, se você preferir usar as caixinhas (`- [ ]`) que o Filipe mostra no vídeo, você pode continuar fazendo o controle das tarefas dentro da issue "pai" mesmo, e para ver o progresso dela, é só entrar na página da issue e ver quantas caixinhas já foram marcadas.

* * *

**O `.editorconfig` não funciona e a indentação continua com 4 espaços**

Esse problema pode ter algumas causas. Experimente as soluções abaixo, começando pela mais simples:

**1º - Reiniciar o editor/ambiente**

-   **Codespaces:** Aperte as teclas Ctrl+Shift+P, busque por `"Stop Current Codespace"`, e aperte Enter. Depois é só abrir ele de novo pelo caminho que você já conhece.
-   **VSCode local:** Às vezes é necessário reiniciar o editor.
-   **WSL (Windows):** Se estiver usando ambiente local com WSL, pode ser necessário reiniciar o Ubuntu no WSL.

**2º - Desativar o Detect Indentation (aba Remoto)**

1.  `Ctrl+Shift+P` ou `F1`
2.  Busque por `Preferences: Open Settings (UI)`
3.  Vá na aba `Remoto [Codespaces: /nome_do_codespaces/]`
4.  Desative a opção `Detect Indentation`
5.  Faça o refresh da página

**Atenção:** É necessário desativar o `Detect Indentation` na aba **Remoto** em Configurações. Se você desativar apenas na aba **Usuário**, pode não funcionar.

**3º - Gerar o arquivo pela interface**

Apague o `.editorconfig` criado manualmente e gere um novo pela interface: clique com o botão direito na raiz dos arquivos e selecione `Generate .editorconfig`.

**Atenção:** Se você continuar a escrever no corpo de uma função que já está com indentação de 4 espaços, pode acontecer do editor dar continuidade a essa mesma indentação. Teste criando um arquivo novo ou uma nova função para verificar se está funcionando. 🤝

* * *

**O GitHub não mostra mais o fundo cinza no destaque da mensagem de commit**

Houve uma mudança na interface do GitHub que deixou de exibir esse sombreado cinza, infelizmente. Agora o destaque fica apenas na alteração da fonte, que ainda é válido realizar.

* * *

**Se eu usar o Prettier, o `EditorConfig` se torna desnecessário?**

Na verdade, não. Enquanto o `Prettier` vai nos ajudar na formatação do código _após nós escrevermos_, quando o arquivo estiver salvo, o `EditorConfig` vai nos ajudar a manter o padrão _enquanto_ nós escrevemos o código.