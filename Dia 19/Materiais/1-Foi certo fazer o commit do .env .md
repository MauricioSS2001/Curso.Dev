# Foi certo fazer o commit do .env?

Como eu antecipei na última Pista Lenta do Dia 18, algumas lapidações **importantes** precisam ser feitas, incluindo em **conhecimento**, e eu acho melhor a gente não deixar isso para depois e fazer agora. Então eu gostaria de começar tocando no ponto de que se foi certo ou não fazer o `commit` do arquivo `.env` 🤝

## Artigo sobre remover dados sensíveis

Este é o artigo que eu comentei sobre remover dados sensíveis do histórico do seu repositório: [Remover dados confidenciais de um repositório](https://docs.github.com/pt/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository)

## Comentário em destaque

Sugiro ler [esse comentário](https://curso.dev/alunos/maion/b0dbda29-d784-4dd2-8ae5-e59eac4cc992) do aluno `maion` explicando como ele usou o `BFG` para remover dados sensíveis de dois arquivos do seu repositório 💪

### Link para o commit feito na aula

-   [move `.env` file to `.env.development`](https://github.com/filipedeschamps/clone-tabnews/commit/a7e5bb9bca6290c81adfd5068ad197f6737aa2bd)
<br>

---
<br>

# Comentário em destaque

Para quem quiser saber como eu usei o BFG para corrigir meu repositório que havia vazado dados em dois arquivos: .env e cred.json

1 - Baixei o arquivo .jar do BFG Repo-Cleaner do [repositório](https://rtyley.github.io/bfg-repo-cleaner/) e coloquei na mesma pasta que clonarei o projeto.

2 - Clonei meu repositório com o --mirror:  
`git clone --mirror git://example.com/repo_problematico.git`

3 - Apaguei os arquivos com os comandos:  
`java -jar bfg-1.14.0.jar --delete-files cred.json repo_problematico.git`  
e  
`java -jar bfg-1.14.0.jar --delete-files .env repo_problematico.git`

4 - entrar na pasta do repositório problemático:  
`cd repo_problematico.git`

5 - Rodar os comandos conforme a documentação do BFG:  
`git reflog expire --expire=now --all && git gc --prune=now --aggressive`

6 - `git push`

E tudo pronto.  
EDIT: Acabei escrevendo no [TabNews](https://www.tabnews.com.br/maion/vazei-meus-dados-e-agora-veja-como-remover-dados-confidenciais-commitados) sobre isso. Gastem seus TabCoins comigo lá!! hahaha