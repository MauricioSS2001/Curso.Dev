# Git Commit (e a Escada Infinita)

Agora que a gente já sabe usar o `git` para ver os `commits` (as fotos) que o nosso repositório possui, chegou a hora de entender quais são os **3 estágios** que um arquivo pode passar nessa história de controle de versão.

### Link para o commit feito na aula

-   [adiciona o arquivo .gitignore](https://github.com/filipedeschamps/clone-tabnews/commit/a788f47deec15c70886bca848815ccc96bf0055e)

## Perguntas frequentes

Como sair do VIM quando ele abre ao executar `git commit`?  

Quando você executa `git commit` sem o parâmetro `-m`, o Git abre um editor de texto para você escrever a mensagem. Por padrão, esse editor é o VIM.

Para salvar e sair do VIM:

1.  Pressione `ESC` (garante que você está no modo comando)
2.  Digite `:wq`
3.  Pressione `Enter`

O commit será salvo e você volta para o terminal normal.

**Para configurar o VSCode como editor padrão do Git:**

Execute uma vez no terminal:

    git config --global core.editor "code --wait"
    

Depois disso, ao executar `git commit`, vai abrir uma aba normal no VSCode para você escrever a mensagem.

* * *

O `git log` fica "preso" mostrando (END) e não consigo digitar novos comandos  

Esse é o comportamento normal. O `git log` deixa o terminal "preso" para que os comandos que você digita no teclado influenciem apenas ele mesmo (permitindo navegar pelo histórico).

Para sair dessa tela, basta pressionar a tecla `Q`.