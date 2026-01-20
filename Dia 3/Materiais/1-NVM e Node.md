# A fundação

Nesta aula eu destaco uma frase do [Carl Sagan](https://en.wikipedia.org/wiki/Carl_Sagan) que se conecta perfeitamente com o que acontece no mundo da tecnologia e programação... inclusive com o que acontece dentro desta própria aula ao configurar o **Node.js**, a fundação do projeto, utilizando o utilitário `nvm`.

## Perguntas frequentes

**O que é Node.js e o que é `nvm`?**  

O Node.js é uma ferramenta que vai nos permitir trabalhar com a linguagem JavaScript diretamente na nossa máquina, sem depender do navegador, que é o ambiente para o qual ela foi feita para rodar originalmente. No nosso caso, o Node.js será o responsável por executar o código JavaScript no servidor do nosso projeto clone do TabNews.

Já o NVM é uma outra ferramenta que nos permite trabalhar com várias versões do Node em nossa máquina, facilitando a troca entre elas com um comando simples, sem precisar ficar desinstalando e instalando versões sempre que formos trabalhar em projetos que utilizam diferentes versões do Node.

Pense na seguinte analogia: o Node.js é como um forno elétrico que permite usar uma receita (JavaScript) fora da cozinha tradicional (o navegador). Assim, você pode "cozinhar" programas no servidor.

Já o NVM é como um painel que troca a voltagem do forno. Ele permite usar o forno em diferentes potências (versões do Node.js) conforme a receita pede, sem precisar comprar outro.

**A versão `lts/hydrogen` está fora do suporte extendido. Devo usar ela mesmo assim ou posso usar uma versão mais recente?**  

A recomendação é que você utilize as mesmas versões que o Filipe mostra no vídeo, para evitar qualquer tipo de atrito por conta de possíveis incompatibilidades com as versões dos outros pacotes que vamos utilizar ao longo do curso.

Então sim, use a `lts/hydrogen` (versão 18) mesmo que esteja fora de manutenção. Não se preocupe, que mais para frente nós vamos atualizar tanto o Node como as outras dependências do nosso projeto, e vai dar pra extrair aprendizados bem valiosos desse processo.

Agora, se por algum motivo técnico você não conseguir instalar a `lts/hydrogen`, aí sim pode usar a `lts/iron` (versão 20), que é a mais próxima. 🤝

**Estou com problemas com o `nvm` no Windows. Porque os comandos não funcionam da mesma maneira que o Filipe mostra na aula?**  

Se você optou por desenvolver localmente no Windows ao invés do Codespaces, certifique-se de seguiu os passos de configuração da aula [Windows](https://curso.dev/web/ambiente-de-desenvolvimento-windows). Alguns alunos acabam instalando o `nvm-windows` e trabalhando fora do WSL, o que leva à divergências na hora de reproduzir os passos mostrados pelo Filipe na aula.

Isso acontece porque o `nvm` e o `nvm-windows` são duas ferramentas diferentes, e elas não têm as exatas mesmas funcionalidades. O `nvm-windows` é uma outra ferramenta diferente da que estamos utilizando no curso, que não suporta os mesmos comandos.

Seguindo os passos da aula de configuração para o [Windows](https://curso.dev/web/ambiente-de-desenvolvimento-windows), o comportamento deve ser idêntico ao que é mostrado na aula.

Defini a versão padrão com `nvm alias default lts/hydrogen`, mas quando abro um novo terminal, volta para outra versão. O que pode ser?  

Primeiro, certifique-se de que você já fez o download da versão antes de colocar ela como default. É necessário instalar a versão primeiro com `nvm install lts/hydrogen`, e só depois definir o alias com `nvm alias default lts/hydrogen`.

Se mesmo assim o problema persistir, execute o comando `nvm ls` e verifique se os apontamentos do alias para a versão do Node correspondente estão corretos.

Caso não estejam, a solução é:

1.  Desinstalar todas as versões do Node
2.  Instalar novamente a versão desejada com `nvm install lts/hydrogen`
3.  Definir novamente o alias com `nvm alias default lts/hydrogen`
4.  Fechar e abrir a IDE/terminal

