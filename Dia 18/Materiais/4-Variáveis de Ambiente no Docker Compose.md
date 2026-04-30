# Variáveis de Ambiente no Docker Compose

Como fazer para evitar de ter Variáveis de Ambiente duplicadas no arquivo `compose.yaml`, no arquivo `databse.js` e fazer tudo puxar do `.env`? É isso o que iremos ver nesta aula, fora se deparar com um **mistério**... vamos ver se você sabe a resposta 🤝

## Mistério: Por quê o Banco de Dados rodou?

Por que no minuto `02:22` da aula, ao trocar a Variável de Ambiente de `POSTGRES_DATABASE` para `POSTGRES_DB` no arquivo `.env`, a conexão com o Banco de Dados continuou funcionando, se o `database.js` estava pedindo ainda pela antiga Variável de Ambiente `POSTGRES_DATABASE`? Você vai precisar investigar para encontrar esta resposta 💪

## Comentário em destaque

Caso queira saber qual a resposta, sugiro ler [esse comentário](https://curso.dev/alunos/HenriqueNas/b907f191-6823-495b-84b3-bb9494c525c4) que está bastante completo 🤝

### Link para o commit feito na aula

-   [add `database.js` and `.env` files](https://github.com/filipedeschamps/clone-tabnews/commit/23969ab8f64e40a210d80847d3ca9bee9c1f3b2e)
<br>

---
<br>

# Comentário

essa aula me deu orgulho de mim mesmo hahaha  
antes mesmo de colocar o `chapéu de investigador` eu estava com o `chapéu de curioso` !!

* * *

na aula passada, quando instaciamos o `const client = new Client()` eu fui correndo atrás da doc do `pg`, e bom, lendo um pouco achei massa uma coisa:

`new Client(config: Config)`

> Every field of the config object is entirely optional. A Client instance will use environment variables for all missing values.

ou seja, quando vc instancia um novo `Client`, paro todo valor não passado como argumento no obj `config: Config` ele vai buscar das variáveis de ambiente !!

agora olhem a doc da tipagem `Config`:

```ts
type Config = {
  user?: string, // default process.env.PGUSER || process.env.USER
  password?: string or function, //default process.env.PGPASSWORD
  host?: string, // default process.env.PGHOST
  database?: string, // default process.env.PGDATABASE || user
  port?: number, // default process.env.PGPORT
  connectionString?: string, // e.g. postgres://user:password@host:5432/database
  ssl?: any, // passed directly to node.TLSSocket, supports all tls.connect options
  types?: any, // custom type parsers
  statement_timeout?: number, // number of milliseconds before a statement in query will time out, default is no timeout
  query_timeout?: number, // number of milliseconds before a query call will timeout, default is no timeout
  application_name?: string, // The name of the application that created this Client instance
  connectionTimeoutMillis?: number, // number of milliseconds to wait for connection, default is no timeout
  idle_in_transaction_session_timeout?: number // number of milliseconds before terminating any session with an open idle transaction, default is no timeout
}
```

* * *

pra quem ainda não sacou, olhem a prop `database`, ela diz que é opcional, mas que quando não é passada o `pg` busca pela variável `PGDATABASE` e caso não encontre nada vai usar o mesmo valor defino para a prop `user`... e funcionou pq o `user` e o `database`tem o mesmo valor: `postgres`

[link da doc do pg.Client](https://node-postgres.com/apis/client)