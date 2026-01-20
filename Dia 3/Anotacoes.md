# Aula 3

## Carl Sagan
Um dos astrofísicos mais conhecidos do Mundo.

>"Para criar uma torta de maçã do zero,
>você deve primeiro criar o Universo."
><i>Carl Sagan</i>

**Mas o que isso quer dizer?**
Esta frase denota que nada é criado do absoluto zero.
Dentro da programação, nada é realmente criado do zero, mas sim criado a partir de ferramentas, códigos, <i>frameworks</i> e outros itens já existentes.

---

## Node.Js

**Recursos Necessários:**
- Terminal
- NVM (Node Version Manager)


### Verificando a versão do Node.Js
~~~ JS
node -v
~~~
**Nota:** O projeto utiliza `Node Hydrogen (Apelido da versão)`.
<br>

### Verificando versões atuais do Node.Js
~~~ JS
nvm -ls
~~~
**Nota:** `ls` significa **<i>list</i> (lista)**.
<br>

### LTS (Long Term Support / Suporte de Longo Prazo)
O termo **<i>LTS</i>** refere-se a um recurso que obterá suporte por um longo período de tempo. No caso do Node, uma verão <i>LTS</i> significa que receberá atualizações por um extenso período.
- Pequenas atualizações serão lançadas dentro da mesma versão porém **possuem compatibilidade garantida**.
<br>

### Instalando uma versão do Node
~~~ JS
nvm install lts/hydrogen
~~~
- O termo `lts/hydrogen` pode ser alterado por outra versão desejada.

---

## Trabalhando com NVM

### Documentação rápida
~~~ JS
nvm --help
~~~
<br>

### Versão padrão para a aplicação
O `Codespace` utiliza a versão mais recente do Node quando aberto. Porém podemos definir uma versão padrão para evitar erros de compatibilidade.

~~~
nvm alias default lts/hydrogen
~~~
- O termo `lts/hydrogen` pode ser alterado por outra versão desejada.
<br>

- **alias:** Apelido
- **default:** Padrão
<br>

### .NMVRC
O arquivo `.nvmrc` define a versão do `Node` que deve ser utilizada quando executar a aplicação.

- **RC (Run Comand):** É uma convenção criada para <i>scripts</i> que possuem instruções de inicialização.
<br>

**O que Adicionar no arquivo?**
~~~ JS
lts/hydrogen
~~~
<br>

**Instalando o Node**
~~~ JS
nvm install
~~~
<br>

---
---
---

<br>

# Next.js
`Next.js` é um framework que facilita o desenvolvimento <i>web</i> desde a parte do desenvolvimento da aplicação, até a fase de <i>deploy</i>.
<br>

## Ambientes
- **Desenvolvimento:** Ambiente onde a aplicação é desenvolvida.
- **Produção:** Ambiente onde o cliente acessa a aplicação (servidor).
<br>

## Analysis Paralysis (Paralisia Por Análise)
- Analisar ou pensar demais ao ponto de paralisar.
- Angústia por ter tomado a decisão "errada" no início.
<br>

## Next.js e React
- **Next.js:** É como a estrutura da casa (projeto), tem a função de definir os limites da aplicação.
- **React:** É como os móveis dos cômodos (telas/<i>UI</i>) da aplicação.
<br>

### Destaque do Next.js
- Destaque com a integração `Framework/Web Host`.
- Trabalha com `Frontend` e `Backend`.
- Desenvolvido pela [Vercel](https://vercel.com) (Empresa que fornece hospedagem de sites).
<br>

### Vercel
- Empresa focada em `Experiência do Desenvolvedor (DX)`.
<br>

---

## Manifesto
O arquivo `package.json` é responsável por listar as depências do projeto.
<br>

---

## Instalando
~~~ JS
npm init
~~~
Utilizado para iniciar um Projeto `Node`.
**Nota:** Licença utilizada na criação do projeto `MIT`.
<br>

~~~ JS
npm install next@13.1.6
~~~
Instalando `Next.js`
<br>

~~~ JS
npm install react@18.2.0
~~~
Instalando `React`.
<br>

## React (Renderizadores)
O `React` foi dividido em vários módulos, principalmente o responsável por `renderizar`. O <i>renderizador we</i> é o `react-dom`.
<br>

~~~ JS
npm install react-dom@18.2.0
~~~
Instalando `React Dom`.
<br>