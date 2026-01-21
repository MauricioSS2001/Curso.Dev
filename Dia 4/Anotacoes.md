# Dia 4

## Protocolos
Protocolos são padrões entre duas partes. Dentro do desenvolvimento <i>web</i>, podemos considerar uma "conversa" entre cliente e servidor.

### Exemplos de Protocolos
- **HTTP (Hypertext Transfer Protocol):** Documentos que contém referências para outros documentos.
- **FTP (File Transfer Protocol):** Protocolo para transferência de arquivos.
- **SMTP (Simple Mail Transfer Protocol):** Protocolo utilizado para transferência de e-mails.
<br>

---

<br>

## Evitando ou ignorando perda de dados
Existem protcolos que podem tolerar ou ignorar erros entre os proxys("lados da conversa" (cliente/servidor)).
<br>

### TCP e UDP (User Datagram Protocol)
- **TCP:** Protocolo que realiza uma conferência dos `payloads` para verificar a integridade da informação. Caso haja perda de payload, o protocolo assegura o `error recovery`. Cada pacote é autossuficiente.
    <br>
    - Assegura integridade da informação.
    - Mais lento.
    <br>
- **UDP:** Protocolo que pode perder `payloads` pelo caminho. Os pacotes perdidos são ignorados em troca de uma maior velocidade e menor confiabilidade de integridade.
    <br>
    - Não assegura integridade das informações.
    - Mais rápido.
    - **Exemplo:** Ligações de vídeo em apps como <i>Zoom</i>, <i>Teams</i>, Jogos <i>multiplayer</i>, etc..
    <br>

[Video Demonstrativo](https://www.youtube.com/watch?v=ZEEBsq3eQmg)
<br>

### Hierarquia de Protocolos
Os protocolos podem e são unidos para a construção da Internet.
> 1. **HTTP:** Permite a referenciação de outros documentos na <i>WEB</i>.
> 2. **TCP:** Evita perda de `pacotes (payloads)` entre a comunicação.
> 3. **IP (Internet Protocol):** Trasmite dados através de "túneis" da Internet.

<br>

---

<br>

## Scripts
Scripts são "atalhos" para execução de comandos na aplicação.
<br>

### Onde criar um script?
para criar um script, basta inserir um nome para ele e o comando dentro do objeto `scripts` no arquivo `package.json`.

~~~ Node
dev: "next dev"
~~~
<br>

### Executando um Script
para executar um script, basta rodá-lo pelo `terminal` com o nome definido no `package.json`.
~~~ Node
npm run dev
~~~
<br>

### Depência local e global
A instalação de um módulo no `Node` pode ser **local** ou **global**.
- **Local:** Apenas no projeto atual em que se está trabalhando (Dentro da NodeModules).
- **Global:** Ná maquina em que esá instalado o `Node`. Não recomendado pois pode causar conflito de versões em diferentes projetos visto que todos utilizarão a mesma.
<br>

---
---
---

<br>

## Limpando o terminal
Para limpar o `terminal` basta utilizar o comando `CTRL + L` ou digitar o comando abaixo.
~~~ JS
clear
~~~
<br>

## Arquivos no Next.js
`Next.JS` utiliza o sistema <i>**File-Based Routing (Roteamento Baseado em Arquivos)**</i>. Este sistema é responsável pela busca de arquivos no projeto com base na rota acessada pelo cliente.
<br>

## Criando páginas no Next.js
Para criação de páginas, é necessário criar um diretório chamado `pages`. Cada arquivo dentro desta pasta que seja `JavaScript` ou `TypeScript`, se tornará uma página na aplicação. 
<br>

## O arquivo <i>index.js</i>
O termo **index (índice)** é utilizado de maneira padronizada devido ao fato de ser amplamente utilizado como página inicial no início da Internet. Devido a padronização, o termo é utilizado até hoje abrangendo a maior parte dos sites.