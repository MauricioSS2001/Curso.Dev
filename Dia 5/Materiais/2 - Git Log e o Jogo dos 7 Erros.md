# Git Log (e o Jogo dos 7 Erros)

Topa jogar o Jogo dos 7 erros comigo? Tudo em nome de aprender `git`, mas mais especificamente o mecanismo de `diff`, pois isto vai ser um _"plot twist"_ numa confusão que muita gente faz sobre os bastidores de como o `git` funciona e gerencia o seu histórico de arquivos. Fora que, entendendo isso, vai abrir sua mente sobre o que é retornado pelo comando `git log` (e como).

## Perguntas frequentes

Como o `Git` consegue ser eficiente em espaço se grava arquivos inteiros em vez de `diffs`?  

O Git consegue ser eficiente nesse aspecto, mesmo gravando arquivos inteiros, graças a três coisas:

-   **Compressão**: cada `blob` é compactado
-   **Deduplicação**: arquivos idênticos são armazenados apenas uma vez, pois geram o mesmo hash
-   **Packfiles**: periodicamente o Git agrupa os `blobs` e aplica _delta compression_ para armazenamento de longo prazo

* * *

O `Git` realmente não armazena as diferenças (`diffs`) permanentemente?  

O Git não armazena os `diffs` de forma permanente. Cada `commit` é como uma "foto" do repositório inteiro naquele momento. Os `diffs` que visualizamos são calculados sob demanda, comparando as "fotos" (snapshots) quando necessário.

Essa abordagem é mais performática porque o Git não precisa reconstruir o arquivo aplicando todas as alterações desde o início do projeto.

* * *

O `Git` duplica todos os arquivos a cada `commit`, mesmo os não modificados?  

Não! O Git vai armazenar apenas os arquivos que foram alterados. Ele não duplica os arquivos que estão iguais.

Os arquivos não modificados continuam sendo apenas apontamentos (referências) para os `blobs` já existentes. É por isso que, mesmo tendo muitos commits, o repositório não fica gigantesco.