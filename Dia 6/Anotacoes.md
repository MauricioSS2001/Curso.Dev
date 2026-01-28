# Git Push

## Linha do tempo
A linha do tempo marca quais `commits` estão a frente ou atras da versão do repositório remoto do `git`.

**Ahead:** A `branch` local está **à frente do repositório**.
**Behind:** A `branch` local está **atrás do repositório**.
<br>

**Branch main:** é a branch **principal** do repositório
<br>

## Branches
Uma `branch` é uma ramificação do repositório.

### Listando branches
~~~ git
git branch
~~~
<br>

## Comparando branches em relação a linha do tempo
Considere os seguintes itens:
- **origin/main**
- **local/main**

Estamos trabalhando na mesma `branch` (`main`), porém em locais distintos, onde `local`, é a `branch` que está localmente no computador e a `origin` é a origem que ela veio (No caso, odo `git`).
<br>

## Git Push
`Push` significa **empurrar**. Um processo `push` envia o commit local para o diretório remoto do `git`.
~~~ git
git push
~~~
Processo de **Upload**.
<br>

## Git Pull
`Pull` significa **puxar**. Um processo `pull` traz as alterações da `branch` do repositório remoto para a `branch` local.
~~~ git
git pull
~~~
Processo de **Download**.
<br>

---
---
---

<br>

# Package.json VS Package-lock.json
Embora ambos arquivos sejam **manifestos**, possuem algumas diferenças.
- **`package.json`**
    - **Metadados -** (Autor, descrição, etc...)
    - **Scripts -** (Utilizados com `npm run`)
    - **Dependências do projeto -** (Dependências do projeto {`npm install`})
    <br>

- **`package-lock.json`**
    - **Depêndencias principais e "sub"dependências** (Principais como `React`, `Next` e as depências necessárias para cada uma dessas)
<br>

## Criando um commit com mensagem (Simplificando os comandos)
Para simplificar o processo de <i>commit</i>, podemos utilizar o comando abaixo.
<br>

**Após adicionar os arquivos**
~~~
git commit -m "Mensagem do commit"
~~~
**Nota:** `-m` é utilizado para indicar que o commit terá uma mensagem.
<br>

## Vários commits em um push
Um processo de `push` no `git` pode conter vários `commits`.
<br>

## Consertando um erro em um commit
Para consertar um erro em um <i>commit</i>, é possível utilizar a linha do tempo do `git` com alguns passos.
<br>

**1.** Voltar para o repositório local.
**2.** Alterar o código necessário.
**3.** Adicionar os arquivos com `git add`.
**4.** <i>Emendar</i> o <i>commit</i> com `git commit --amend`.
**5.** "Empurrar" para `origin (origem)` com `git push`.
<br>

---
---
---
<br>

# Por que o `push` pode falhar?
O `push` pode falhar no processo de `ammend` quando o hash do commit da **<i>branch local</i>** é diferente da **<i>branch remota</i>**.

- **Hash da branch remota (`origin`):** `d87e431`
- **Hash da branch local (com `ammend`):** `17ce278`
<br>

## Empurrando um commit a força (sobreescrevendo de maneira forçada)
Para sobreescrever a `branch` ignorando a linha do tempo do `git`, é possível realizar o `push` de maneira "forçada".

**Push forçado**
~~~ git
git push --force
~~~
**Comando abreviado**
~~~
git push -f
~~~
<br>

**Notas:** 
- O **<i>hash</i> do <i>commit</i>** passará a ser o do **<i>commit</i> forçado** (o que veio do `local`).
- O <i>commit</i> pré existente pode ser acessado **temporariamente** até que o **garbage collector** do `git` limpe-o permanentemente.
<br>

**NOTA IMPORTANTE:** O uso equivocado do `git push` de maneira forçada pode gerar danos irreversíveis ao código presente no repositório.