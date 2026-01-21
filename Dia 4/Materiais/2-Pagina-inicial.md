# Página inicial

Depois de uma rápida dica sobre como limpar o seu terminal usando `clear` ou `CTRL` + `L`, chegou a hora de subir de verdade o nosso **Servidor Web**, mas para isso, precisamos de uma **página** de verdade e não poderia ser diferente, a não ser começar com a `index`.

Além disso, eu mostro um recurso interessante no **Codespaces** sobre como deixar as suas rotas de forma **pública** e ainda com **live-reload**.

## Perguntas frequentes

Estou recebendo o erro `'import' and 'export' may appear only with 'sourceType: module'`. Como resolver?  

Isso acontece porque em versões mais modernas do npm, ao executar o `npm init`, ele inclui a propriedade `"type": "commonjs"` no `package.json`.

Quando o `type` está como `"commonjs"`, o Node entende que os arquivos do projeto usam o padrão CommonJS, que trabalha com `require` e `module.exports`. Nesse modo, se você usar `import` e `export`, o parser acusa exatamente essa mensagem de erro.

A solução mais simples é remover a linha `"type": "commonjs"` do arquivo `package.json`.

* * *

Como deixar a porta pública no VSCode local (fora do Codespaces)?  

Esse recurso de encaminhamento de portas só é nativo no Codespaces. No VSCode local há um recurso similar que utiliza o Dev Tunnels da Microsoft.

**Para quem usa WSL, o passo a passo é o seguinte:**

1.  Com o servidor do Next do seu projeto já rodando lá dentro do WSL, na porta 3000, abra uma nova janela do VSCode no Windows (não pelo terminal do WSL, mas pelo Windows mesmo). E em seguida, abra o terminal:

![](https://i.imgur.com/xT7vTc1.png)

2.  Clique na aba `Ports`, e depois no botão `Forward a port`:

![](https://i.imgur.com/p98horv.png)

3.  Digite 3000 no campo Port, e aperte Enter. Você será solicitado para conectar o seu VSCode à sua conta do GitHub. Em seguida, você será encaminhado novamente para o seu VSCode local, e o endereço da sua porta encaminhada já deve estar aparecendo.

![](https://i.imgur.com/9PrHVzs.png)

* * *

Estou recebendo o erro `Missing script: "dev"`. O que fazer?  

A mensagem de erro indica que o script `dev` não está presente no `package.json`. Confira se não há algum erro de digitação ou de formatação.

O seu arquivo deve estar semelhante a este:

    {
      "name": "clone-tabnews",
      "version": "1.0.0",
      "description": "",
      "main": "index.js",
      "scripts": {
        "dev": "next dev"
      },
      "author": "",
      "license": "MIT",
      "dependencies": {
        "next": "^13.1.6",
        "react": "^18.2.0",
        "react-dom": "^18.2.0"
      }
    }
    

Verifique especialmente se dentro de `"scripts"` você tem `"dev": "next dev"` (e não algo como `"next": "next dev"`, que é um erro comum).

* * *

Estou recebendo o erro `Project directory could not be found`. Como resolver?  

Esse erro geralmente acontece porque o Next.js não consegue encontrar a pasta `pages` do projeto. As causas mais comuns são:

1.  **Nome da pasta incorreto:** O Next.js procura obrigatoriamente uma pasta chamada `pages` (com "s" no final e letra minúscula). Se a sua pasta estiver como `page`, `Pages` ou qualquer outra variação, ele não consegue achar os arquivos do projeto e por isso não inicia.
    
2.  **Pasta no local errado:** A pasta `pages` deve estar na raiz do projeto, no mesmo nível do `package.json`.
    

Verifique se a pasta está nomeada corretamente como `pages` (minúsculo, com "s") e se está na raiz do projeto.

* * *

O hot reload (atualização automática) não funciona no WSL. O que pode ser?  

Não é recomendado trabalhar cruzando os sistemas de arquivos do WSL e do Windows, por conta de problemas de performance. Quando você está usando o WSL (Ubuntu) e seu projeto está em uma pasta do Windows (como `/mnt/c/Projetos/seu_projeto`), o desempenho de acesso a arquivos pode ser muito lento, o que afeta o funcionamento do hot reload. Você pode conferir mais detalhes sobre isso [aqui](https://learn.microsoft.com/pt-br/windows/wsl/filesystems#file-storage-and-performance-across-file-systems).

Se você usa o WSL como ambiente de desenvolvimento, o melhor a se fazer é salvar o seu projeto dentro do WSL, usando o diretório raiz do sistema de arquivos do Linux: `/home/<username>/meu-projeto`.

Certifique-se também de abrir o VSCode a partir do WSL usando o comando `code .` no terminal Ubuntu.

* * *

A pasta `.next` não aparece no meu projeto. Fiz algo errado?  

Não se preocupe, pois a pasta `.next` é gerada automaticamente pelo Next quando executamos o `npm run dev`. Ela contém os arquivos de build do nosso projeto, que são uma versão empacotada dele para ser entregue pelo servidor. Você não precisa criar essa pasta manualmente e não precisa se preocupar com ela.

Se ela ainda não apareceu, provavelmente é porque você ainda não executou o comando `npm run dev` com sucesso, ou o Codespaces/VSCode ainda não atualizou a visualização da árvore de arquivos.