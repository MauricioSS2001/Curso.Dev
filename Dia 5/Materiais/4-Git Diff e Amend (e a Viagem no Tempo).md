# Git Diff e Amend (e a Viagem no Tempo)

Eu gostaria de começar a aula de hoje falando sobre um poder que você tem, que é de **viajar no tempo**. Sim, você tem em mãos uma máquina do tempo, que não é tão massa quanto um **Delorean**, mas que é o `git` e com ele você consegue sim viajar no tempo e mudar as coisas que aconteceram... pelo menos dentro do seu **repositório**. Então para isto, nós iremos aprender a usar o comando `git commit --amend`.

## Perguntas frequentes

**O que acontece com o commit antigo após usar `--amend`? É possível recuperá-lo?**  

O comando `git commit --amend` não altera diretamente um commit existente, pois commits são imutáveis. O que ele faz é criar um novo commit com o conteúdo atualizado e substituir a referência do commit anterior.

O commit antigo é substituído e continua existindo temporariamente no histórico como um commit "órfão", até que o garbage collector do Git faça a remoção automática após um tempo. O garbage collector é um coletor de lixo que faz uma limpeza periódica no repositório para remover objetos que não possuem nenhuma referência apontando para eles, ou seja, que não pertencem a nenhuma branch.

E existe sim uma maneira de recuperar o commit que foi sobrescrito enquanto ele não foi deletado permanentemente pelo garbage collector. Isso pode ser feito através do comando especial `reflog`, que o Filipe vai mostrar como usar mais para frente no curso. 🤝

* * *

**Como alterar um commit que não é o último (mais antigo)?**

É possível sim, mas não apenas com o `--amend` sozinho. Seria preciso utilizá-lo em conjunto com outro comando, que é o `git rebase`. O `git rebase` é uma espécie de `amend` turbinado.

Mais para frente o Filipe vai ensinar como fazer ele em detalhes, mas resumidamente o processo seria:

1.  Iniciar o rebase interativo: `git rebase -i HEAD~N` (onde N é o número de commits que você quer visualizar)
2.  No editor, marcar o commit desejado como `edit`
3.  Fazer as alterações necessárias
4.  Executar `git commit --amend`
5.  Finalizar com `git rebase --continue`

* * *

**O `--amend` serve para corrigir vazamento de dados sensíveis (senhas, tokens)?**  

Depende se o commit já foi enviado para o repositório remoto ou não.

**Se o commit ainda está apenas local (não fez `git push`):** Nesse caso, o `--amend` resolve sim. Você pode remover os dados sensíveis, fazer o amend e seguir normalmente.

**Se o commit já foi enviado para o repositório remoto:** O `--amend` não será suficiente, infelizmente. Quando o commit chega no remoto, já era. Nem `git push --force` resolve completamente, porque pode haver caches, reflogs, clones e forks feitos do repositório. O melhor cenário seria invalidar as chaves de acesso (tokens, etc.) e fazer renovações desses segredos o quanto antes.

Mais para frente o Filipe vai explicar o que fazer nessas situações com mais detalhes. 🤝