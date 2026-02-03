# Client e Server

Existe uma relação **extremamente importante** em qualquer camada da tecnologia, que é a relação entre `cliente` e `servidor` (ou `client` e `server`). Algumas pessoas começam a se confundir sobre quem é o `client` e quem é o `server`, pois eles não são papeis fixos e dependem do que exatamente estes componentes estão fazendo. Ter a modelagem correta na mente sobre isso é algo valioso, pois ela destrava **novas percepções** sobre a arquitetura de todos os softwares envolvidos em um sistema.

## Perguntas frequentes

**Quem é `client` e quem é `server` quando um sistema envia dados para outro via API?**  

O sistema que **faz a requisição** é o `client`, mesmo que ele esteja enviando dados. O sistema que **recebe e processa** essa requisição é o `server`.

Por exemplo, se o sistema A envia um cadastro via API para o sistema B:

-   **Sistema A** = `client` (porque faz a requisição, enviando o cadastro)
-   **Sistema B** = `server` (porque recebe e processa essa requisição)

O que define o papel não é "quem envia dados", mas sim **quem inicia a comunicação**.

* * *

**O `client` é sempre quem inicia a interação/comunicação em um modelo client–server?**

Sim! Independente da função, aquele que inicia a interação é sempre considerado `client`.

Pense em um app de mensagens como o WhatsApp, por exemplo. Quando você abre o app, seu celular (client) inicia uma conexão com os servidores do WhatsApp (server) para verificar se há novas mensagens. Quem "bateu na porta" primeiro foi o seu celular, então ele é o client.

O [cliente sempre precisa abrir um canal de comunicação](https://pt.wikipedia.org/wiki/Modelo_cliente%E2%80%93servidor#:~:text=O%20componente%20de%20servidor%20fornece%20uma%20fun%C3%A7%C3%A3o%20ou%20servi%C3%A7o%20a%20um%20ou%20mais%20clientes%2C%20que%20iniciam%20os%20pedidos%20de%20servi%C3%A7o.). Mesmo que o servidor envie dados "sem ser solicitado" diretamente, isso só é possível porque já houve um "acordo" (estabelecimento de conexão inicial) por parte do cliente. O servidor não pode enviar dados arbitrariamente para "qualquer um".

* * *

**O `server` pode iniciar uma comunicação com o `client`?**

Não diretamente. Nesse caso, a diferença seria uma **conexão do tipo persistente**, mas ainda assim o cliente precisaria iniciar ela.

Tomando como exemplo o WhatsApp, quando você recebe uma notificação de mensagem nova "do nada", pode parecer que o servidor iniciou a comunicação. Mas o que acontece é que seu celular (client) já havia aberto uma conexão persistente com o servidor anteriormente. Com essa conexão aberta, sempre que houver uma atualização no servidor para o cliente, ela é enviada por esse canal já estabelecido.

Ou seja, o cliente abre o canal primeiro, e depois o servidor pode enviar atualizações por esse canal.

* * *

**O que é um `proxy` na relação client-server?**

Um `proxy` é um **servidor intermediário** entre o client e o server.

Usando a analogia da aula: é como ter mais de um garçom. Um garçom passaria o pedido para outro garçom, e assim sucessivamente até chegar na cozinha.

Na explicação do Filipe sobre o filho pedindo um copo de água para o pai, e o pai pedindo para a mãe, o pai atua como um `proxy` entre as duas pontas. Isso é justamente o que acontece quando um client pede algo para um server e o server faz uma requisição para outro server, atuando como client.

* * *

**O live reload não está funcionando no meu projeto (Windows + WSL)**

Isso pode estar acontecendo se o seu projeto estiver salvo no **sistema de arquivos do Windows**, ao invés de estar dentro do Ubuntu no WSL.

Fazer esse trabalho "cruzado" entre os sistemas afeta o desempenho e pode causar problemas como o live reload não funcionar.

Para solucionar, mova seu projeto para dentro do sistema de arquivos do Ubuntu no WSL.

Você pode conferir mais detalhes sobre isso na documentação da Microsoft: [https://learn.microsoft.com/pt-br/windows/wsl/filesystems#file-storage-and-performance-across-file-systems](https://learn.microsoft.com/pt-br/windows/wsl/filesystems#file-storage-and-performance-across-file-systems)