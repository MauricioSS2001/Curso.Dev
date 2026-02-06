# Sincronização das configurações do Editor

Esta é uma aula mais específica ao `Codespaces` ou até `VS Code` e que serve como referência para outros editores sobre uma feature para sincronização na nuvem de configurações.

Mas independente disto, a parte mais importante é que nesta aula iremos aprender a dividir uma `Issue` em `Tarefas` e concluir a primeira `Tarefa` da Milestone 🎉

## Perguntas frequentes

**O indicador de progresso das tasks mudou no GitHub. Como funciona agora com `sub-issues`?**

O GitHub passou por algumas mudanças de layout, e a sintaxe `- [ ]` sozinha não faz mais aparecer o contador "1 of 3 tasks" como mostrado na aula.

Agora, para ter a mesma visualização que é mostrada no vídeo, é preciso converter as tarefas em sub-issues. Para isso, clique nos 3 pontinhos (`...`) ao lado da task e escolha a opção "Convert to sub-issue".

Porém, uma desvantagem das sub-issues é que elas ficam listadas na página de Issues junto com as issues principais, o que pode poluir a visualização. Uma alternativa para contornar isso é filtrar apenas as issues principais, colocando na barra de pesquisa:

    is:issue state:open no:parent-issue
    

Também dá pra continuar usando as caixinhas (`- [ ]`) como o Filipe mostra no vídeo. Você perde a visualização do gráfico na página principal das issues, mas o repositório não fica lotado de sub-issues.

De qualquer forma, isso não vai interferir em nada no seu acompanhamento das aulas.

* * *

**Já tenho configurações no VSCode e quero separar do curso. Como criar perfis diferentes?**

A gerência de perfis é feita no próprio VSCode (não pelo GitHub). Você pode criar perfis diferentes para diferentes ambientes de desenvolvimento. Por exemplo, um perfil para seu desenvolvimento local, outro para o trabalho, e um novo perfil limpo para acompanhar o `curso.dev`.

**Como criar um novo perfil:**

1.  Clique na engrenagem (⚙️) no canto inferior esquerdo do VSCode
2.  Passe o mouse na opção "Perfis" (abaixo de "Paleta de comandos")
3.  Clique em "Novo perfil"
4.  Escolha se quer um perfil com as configurações padrão do VSCode (Perfil vazio) ou copiando sua configuração atual
5.  Insira um nome e pressione Enter

Com a sincronização ativada, dá pra usar as mesmas configurações em qualquer máquina com o VS Code.