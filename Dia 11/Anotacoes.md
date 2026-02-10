# Resolução de DNS (Desafio Nível 1)

## Cloudflare
Sistema que evita `Ataques de Negação` que tem o objetivo de **derrubar o sistema**.
<br>

## Domínios
Endereços como `www.google.com.br`, `www.youtube.com`, etc... **são apenas apelidos**. O real endereço de uma aplicação (um site por exemplo) é o `IP (Internet Protocol)`.
<br>

- Cada dispositivo conectado à `Internet` possuí um `endereço IP`.
<br>

- Um computador pede arquivos a outro por meio do envio de um "pacotinho".
    - Cada "pacotinho" tem o registro do `Endereço IP` final.
    - Durante o trajeto, cada roteador utilzia este `Endereço IP` para enviar o "pacotinho" pelo melhor caminho possíve até ele chegar ao destino final.

<br>

## Exemplo de IP
`www.google.com.br` tem os seguintes `Endereços IP`:
- `IPv6` : `2800:3f0:4001:837::2003:`
- `IPv4` : `172.217.29.163`
<br>

## DNS (Domain Name System / Sistema de Nomes de Domínios)
O principal objetivo do `DNS` é converter um domínio como `www.google.com.br` no `endereço IP` dele (`172.217.29.163`).
<br>

## Conexão entre computador (cliente) e servidor pelo DNS

**1.** O computador (`Cliente`) envia o `link` (`google.com.br`) da aplicação desejada (considere um <i>site</i>) para o `servidor DNS`.

**2.** O `Servidor DNS` envia o `Endereço IP` (`172.217.29.163`) para o computador (`Cliente`).

**3.** O computador (`CLiente`) envia as reuqisições para o `Servidor` por meio de seu `Endereço IP`.
<br>

## Dica sobre alteração de hospedagem
O `Domínio` deve ser mantido preferencialmente enquanto o `Endereço IP` pode ser alterado sem problemas.
<br>

## Desafio 1
Acessar a segunda aula do dia que está "escondida". para acessar, é necessário achar o `Domínio` da segunda aula.

**Link da primeira aula:** https://curso.dev/web/resolucao-dns-nivel-1

**Solução:** Alterar o link trocando o `1` pelo `2`.
<br>

---
---
---
<br>

# User Experience (UX)
`User Experience` é otermo utilizado para descrever a `Experiência do Usuário`. Por exemplo, se toda vez que o usuário precisasse avençar uma página alterando o `link` manualmente pelo navegador, poderiam acontecer inúmeros problemas levando a uma **experiência negativa** para o usuário.
<br>

---
---
---
<br>

## A Internet é distribuída
A `Internet` ser distribuída, faz com que haja uma catástrofe em algum lugar do planeta, os demais países não percam o acesso a `Internet`.
<br>

## Explorando funcionamento do completo do servidor DNS

**1. Seu computador(`cliente`) faz uma requisição para o `Recursive Resolver` do seu provedor de Internet.**
    - O `Recursive Resolver` é responsável pela descoberta do `endereço IP` do <i>site</i>.
    - Cada `Recursive Resolver` possui acesso aos `Root Servers`. (Atualmente, existem mais de 1700 instâncias deles para garantir a redundância da Internet.)
<br>

**2. O `Root Server` lê o domínio "ao contrário", no caso, pelo `.br`.**
- Sempre há um ponto (`.`) no final de cada <i>link</i>.
    <br>

    **Exemplo:**
    > google.com.br. ===> Note o ponto `.` ao final do <i>link</i>.
    
    <br>

    Este recurso é chamado `Fully Qualified Domain Name (FQDN)` ou `Nome de Domínio Completamente Qualificado`.
    <br>
    - Este é o **endereço real completo**. 
    <br>
    - A busca começa pelo último ponto (`root domain`).
<br>

**3. O `Root Server` busca o `endereço IP` em outro servidor por meio do `TLD (Top Level Domain)`.**
<br>
    - O `TLD` é um parte que compõem o <link>, como `.br`, `.net`, `.org`, etc...
<br>

**4. A busca é feita dentro do `Root Server` para descobrir qual o endereço `IP` do `TLD Server`.**
    - Servidores `TLD` são divididos em duas categorias:
    <br>
- **ccTLDS (Country Code Top-Level Domains):** 
        São `TLDs` reservados para países, como `.br` para **Brasil** (Administrado pelo **Comitê Gestor da Internet no Brasil**), `.ca` para **Canada**, `.pt` para **Portugal**, etc...
        <br>

**5. O `Root Server` devolve ao `Recursive Server` o `IP` do `TLD Server`.**
    - **Nota:** cada `TLD Server` é responsável por uma `TLD` como `.br`, `.net`, `.etc`...

- **gTLDS (Generic Top Domains):**
São `TLDs` genéricos como `.com` que significa **<i>commercial</i> / Comercial (usado para sites comerciais)**, `.org`, `.net`, `.dev`, entre outros.
<br>

**6. O `Recursive Server` recebe o endereço `IP` do `Authoritative Server` e solicita as inforamções para este `servidor`.**
- Este `servidor` possui todos `DNS Records (Registros de domínios)` que possui o endereço final do `servidor da aplica aplicação` (<i>site</i>).
<br>

!["img1"](./Materiais/img/img1.png)

---

## ICANN (Internet Corporation for Assigned Names and Numbers)
Organização internacional responsável pelos `TLDS`

**Curiosidade:** Em 2015, o **Banco Bradesco** adquiriu o `TLD` `.bradesco`. Após a aquisição, todos os `Root Servers` receberam a adição deste `TLD`.

---

## TTL (Time To Live)
Para evitar o tempo do processo de busca de enderço `IP` a cada requisição do navegador, a tecnologia `TTL` defini o "tempo de vida" que este `cache` deve ser mantido.
- Requisições para um mesmo servidor*.
<br>

- O `cache` acelera muito pois sua camada pode participar ativamente de todos os processos de busca.
<br>

- Alterações de `DNS` fazem com que a atualização do `cache` possa demorar para ser efetivada.
<br>

!["img2"](./Materiais/img/img2.png)