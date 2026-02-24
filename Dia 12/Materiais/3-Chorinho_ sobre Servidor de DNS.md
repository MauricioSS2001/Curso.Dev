# "Chorinho" sobre Servidor de DNS 💪

Que massa que você decidiu assistir o chorinho de conteúdo sobre o **Servidor de DNS** porque com ele há uma alta probabilidade de isso te colocar na frente daquele seniorzão do trabalho ou estar melhor preparado pra uma discussão na internet quando o assunto é `DNS` 💪

E não perde a oportunidade de ficar até ao final para o desafio de `Capture The Flag` 🤝

## Perguntas frequentes

**Erro de timeout ao usar `dig +trace`**

Isso pode estar acontecendo por conta de alguma configuração do seu servidor de DNS, ou de alguma restrição do seu firewall ou do seu provedor de internet.

Você pode contornar isso especificando para o `dig` um servidor de DNS público como o do Google (`8.8.8.8`) ou da Cloudflare (`1.1.1.1`):

```sh
dig seudominio.com.br TXT +trace @1.1.1.1
```

* * *
**Comandos `sudo` e `dig` não funcionam no Windows**

Para trabalhar localmente no Windows, você precisa configurar o seu ambiente seguindo os passos da aula [Windows](https://curso.dev/web/ambiente-de-desenvolvimento-windows). Com o WSL configurado, você conseguirá executar os comandos conforme mostrado na aula.

Uma alternativa rápida, caso queira usar o terminal nativo do Windows sem WSL, o comando equivalente é:

```sh
nslookup -q=txt curso.dev
```

* * *
**Aparecem registros `ALIAS` ao invés de `A Record` na Vercel**

De forma simples, o registro `ALIAS` que está aparecendo para você é uma forma que a Vercel usa para definir o `A record` do seu domínio de forma dinâmica.

Ou seja, ao invés de deixar o endereço IP `76.76.21.21` _hardcoded_ no seu servidor DNS, eles usam um _placeholder_ (o `ALIAS`) no lugar, para que eles tenham mais flexibilidade no gerenciamento da infraestrutura deles.

Esse `ALIAS` no fim das contas acaba resolvendo para o IP de um outro _autoritative server_, que por sua vez possui o `A record` final do seu domínio, que você pode constatar ao executar o `dig`.

Alguns alunos já reportaram ter se deparado com a mesma situação, o que indica que a Vercel deve estar remanejando a infraestrutura dela internamente.

* * *

**Para que serve o registro `TXT`?**

O registro `TXT` é usado, em geral, para validar a posse de um domínio.

Por exemplo, se você quiser contratar o Google como o provedor de email para o seu domínio, ele vai pedir para você inserir um código específico no seu servidor DNS, para que ele possa verificar que você é de fato o dono dele.

Um outro caso de uso é para configurar mecanismos de segurança de email como `SPF` e `DKIM`, os quais iremos abordar em aulas mais avançadas.