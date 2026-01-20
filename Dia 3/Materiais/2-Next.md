# A primeira parede

Com a base feita na aula passada, a gente vai agora começar a levantar as **paredes** (o que de fato vai dar pra começar a “tocar” do nosso sistema), e o primeiro módulo/framework que a gente vai utilizar pra fazer isso é o **Next.js**.

-   Site do framework: [https://nextjs.org/](https://nextjs.org/)
-   Site da empresa por trás: [https://vercel.com/](https://vercel.com/)

## Atenção 🔴

Você não precisa se preocupar agora com o aviso de vulnerabilidades existentes ao instalar o Next. Mais para frente no projeto nós iremos lidar com isso ao atualizar todas as dependências, contando com a cobertura e a proteção dos testes automatizados, e esse processo vai render muitos conhecimentos valiosos.

## Perguntas frequentes

**Apareceram vulnerabilidades após instalar as dependências. Devo me preocupar ou rodar `npm audit fix --force`?**  

Você **não precisa se preocupar** com essas vulnerabilidades agora, e **não deve** rodar o comando `npm audit fix --force`.

O recomendado é que você utilize as mesmas versões que o Filipe mostra no vídeo, para que não haja nenhum atrito durante as aulas. Mais para frente, vamos atualizar todas as dependências do nosso projeto e resolver essas vulnerabilidades juntos, e esse processo vai render vários aprendizados valiosos.

Se você já rodou o `npm audit fix --force` e as versões foram alteradas, volte para as versões da aula com o comando:

    npm install next@13.1.6 react@18.2.0 react-dom@18.2.0
    

* * *
**Apareceu a mensagem `npm warn ERESOLVE overriding peer dependency` ou `Could not resolve dependency`. O que fazer?**

Se você instalou as **exatas mesmas versões** que o Filipe indica, não deveria ter ocorrido nenhum conflito. Esse erro geralmente acontece quando você instalou uma versão diferente dos pacotes antes.

Para resolver, remova todos os pacotes e instale novamente executando os comandos abaixo:

1º Remover os arquivos:

    rm -rf node_modules package-lock.json
    

2º Reinstalar as dependências nas versões corretas:

    npm install next@13.1.6 react@18.2.0 react-dom@18.2.0
    

* * *
Além do `package.json`, também foi criado o `package-lock.json`. É normal? Devo manter?  

Sim, é **100% normal** e você deve **manter os dois arquivos**. O `package-lock.json` é criado automaticamente pelo `npm` quando você instala dependências no seu projeto. A diferença entre eles é que:

-   O **package.json** tem uma visão mais macro do projeto, salvando informações gerais e as dependências principais (com possibilidade de aceitar versões compatíveis);
    
-   Já o **package-lock.json** congela a versão **exata** de cada dependência e subdependência, garantindo que todos que clonarem o projeto terão exatamente o mesmo ambiente.
    

Nas próximas aulas, o Filipe vai explicar mais sobre o propósito desse arquivo, e se quiser mais detalhes você pode conferir esse comentário aqui: [https://curso.dev/alunos/Andrei/f8bd216a-a8bb-4276-90fa-3b578abdefaa](https://curso.dev/alunos/Andrei/f8bd216a-a8bb-4276-90fa-3b578abdefaa)

* * *

**Qual a diferença entre o arquivo `.nvmrc` e o `package.json`? Ambos não controlam versões?**  

Eles têm propósitos diferentes:

-   **`.nvmrc`:** É usado exclusivamente pelo **NVM** para definir a versão do **Node.js** do projeto. Quando você roda `nvm install`, o NVM lê esse arquivo e instala a versão especificada.
    
-   **`package.json`:** É usado pelo **NPM** e lista informações importantes sobre o projeto, sendo a mais importante as **dependências** (módulos como React, Next, etc.) e suas versões.
    

Embora o `package.json` também permita especificar a versão do Node (na propriedade `engines`), nós não temos a conveniência do NVM conseguir ler esse arquivo automaticamente. Por isso usamos os dois.

* * *

**Digitei o comando de instalação e deu erro `404` ou `"package name is not valid"`. O que houve?**  

Provavelmente você digitou o nome do pacote com **letra maiúscula** (ex: `React` ou `React-dom` em vez de `react` e `react-dom`).

Os nomes de pacotes npm são **case-sensitive** e devem ser escritos exatamente como aparecem no registro. **Sempre** utilize os nomes idênticos aos que o Filipe mostra no vídeo, todos em letras minúsculas:

    npm install next@13.1.6
    npm install react@18.2.0
    npm install react-dom@18.2.0
    

Ou instale todos de uma vez:

    npm install next@13.1.6 react@18.2.0 react-dom@18.2.0
    

* * *
**O que são Next.js e React na prática?**  

Se esse é o seu primeiro contato com desenvolvimento web, é natural que isso pareça confuso agora. Ao longo das aulas, o propósito e a função dessas tecnologias vai ficar mais claro.

**Por hora, pense assim:**

-   O nosso objetivo é construir um site feito de várias partes ou componentes (botões, cabeçalhos, tabelas, etc.)
-   O **React** nos permite programar esses componentes usando uma sintaxe especial (HTML + JavaScript), com a vantagem de poder reutilizá-los em várias partes do site
-   O **Next.js** fornece a infraestrutura e a "cola" para juntar e organizar todos esses componentes React nas páginas do site

* * *

**Por que não usamos o comando `npx create-next-app`?**  

Porque queremos mostrar com calma o que cada "pecinha" faz. Além disso, se usássemos esse comando, os alunos ficariam com versões diferentes das que o Filipe usa na aula, o que poderia gerar conflitos mais para frente.