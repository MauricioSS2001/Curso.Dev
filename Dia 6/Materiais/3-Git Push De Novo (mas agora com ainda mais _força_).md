# Git Push De Novo (mas agora com ainda mais "força")

Nesta Pista Lenta será ensinado um dos recursos mais **perigosos** do Git, que é fazer o `push`, porém usando a opção `force`. Fora isso, é uma ótima aula para revisar outros comandos como o `amend` e os efeitos colaterais que ele causa no `commit` anterior, na linha do tempo da sua `branch` `local` e a relação disto tudo com a mesma `branch` lá no `origin`.

## Perguntas frequentes

**Por que o `git push` foi rejeitado após usar `git commit --amend`?**

O push foi rejeitado porque o comando `git commit --amend` reescreve o último commit. Quando você faz isso, o Git percebe que a "história" ou "linha do tempo" do seu repositório local ficou diferente da do repositório remoto, pois agora existem dois commits diferentes apontando para o mesmo lugar na linha do tempo. Com isso, por segurança, o Git bloqueia o envio para evitar que você sobrescreva algo sem querer.

Nós usamos o comando `git push` com a opção `--force` para contorna esse bloqueio, e forçar o envio das suas alterações locais para o remoto.

* * *

**O `git push --force` em uma branch individual afeta outras branches ou pessoas?**  

Se apenas você estiver trabalhando nela, e nenhuma outra branch foi criada com base nela, não vai gerar impacto algum.

Porém, quando trabalhamos em equipe, o uso do `--force` precisa ser combinado com os colegas, pois pode sobrescrever o trabalho de outras pessoas.

* * *

**Existe uma alternativa mais segura ao `--force`?**

Sim! Uma opção seria usar o `git push --force-with-lease`, que é a forma "segura" de forçar o push, pois só sobrescreve o remoto se a sua cópia local estiver atualizada. Ou seja, ele evita apagar commits que outros possam ter enviado para o remoto.

Outra alternativa é resolver o conflito localmente usando `git pull` e depois enviar normalmente para o GitHub. Apesar de "poluir" um pouco o histórico com um commit de resolução de conflito, é uma opção válida. 🤝

* * *

**O commit "apagado" com `amend` + `--force` ainda é acessível? E se eu vazar credenciais?**

Mesmo com um `--amend` e `push --force`, o commit anterior não é apagado imediatamente, e você pode acessá-lo se tiver o `hash` dele. Ele fica disponível temporariamente até que o garbage collector do Git o limpe.

Por isso, no caso do vazamento de credenciais, o `amend` não é suficiente. Seria necessário recorrer a ferramentas externas para fazer a remoção completa.

O Filipe vai abordar essa questão mais na frente no Dia 19. 🤝

* * *

**Quando usar `amend` vs criar um novo commit para corrigir erros?**

Depende do cenário. Criar um novo commit corrigindo seria menos "destrutivo". A vantagem do `amend` é que o histórico dos commits fica mais limpo, mas ele deve ser aplicado com cautela.

Quando é uma alteração muito simples e você está trabalhando sozinho (como no caso desta aula), vale a pena usar o `amend`. Num contexto colaborativo, principalmente se tratando da branch `main`, e dependendo da complexidade da alteração, um novo commit pode ser mais adequado.