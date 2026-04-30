# Criar módulo "database.js"

Nesta aula iremos criar o módulo `database.js` que é uma **abstração** da nossa infraestrutura e que vai ser responsável por **abrir conexão** com o **Banco de Dados** e enviar **queries** pra ele. Para isto, vamos instalar o módulo `pg` na versão `8.11.3` 🤝

## Comentário destaque ⭐️

Depois de ver a aula, sugiro ler [este comentário](https://curso.dev/alunos/filipedeschamps/ca07843d-c389-4722-83f7-55d8de12481b) que fiz sobre a dúvida de outro aluno, pois pode ajudar a clarear alguns pontos importantes sobre a utilidade do `database.js` 💪

---

# Comentário

Aula incrivel mais uma vez, Felipe! Mas sinto que não fixei nada, tenho muita dificuldade de entender o que o módulo database deveria ser, na minha mente ia ser um monte de dados guardados que iriam ser consultados kkkk. Ao mesmo tempo não entendo muito bem o que é o PG na pratica e o que acontece debaixo dos panos, o motivo por qual usamos, entendo a relação client-server mas não entendo por que precisamos usa-lo. Os modulos sobre git/gihub, testes automatizados, docker foram muito faceis e divertidos de fixar na mente já comecei até a treinar em outros projetos, mas nesse tenho que ser sincero que não fixei nada kkkkkk

Se alguem tiver recomendação onde eu possa estudar mais sobre, agradeço <3


## Resposta

Justíssimo `MarcosSantos`, muito obrigado por esse comentário e não se preocupe, de verdade, pois você irá conseguir ter uma compreensão maior quando as peças começarem a se encaixar ao avançarmos com o projeto 💪

E para revisar o que aconteceu, em aulas passadas decidimos utilizar o banco de dados `Postgres`, correto? Só que para conseguir se comunicar com ele, é preciso saber conversar no protocolo que ele conversa (e que é bem difícil de se implementar). Dado a isso, instalamos o módulo `pg`, pois ele sabe se comunicar nesse protocolo. Então nós utilizamos o `pg` para **abrir uma conexão** ao banco de dados e enviar uma `query` (um comando) contra ele e que por hora não possui nenhum dado dentro dele.

E para não precisar repetir o código responsável por abrir uma conexão, enviar uma query e fechar uma conexão em todos os locais na qual precisaremos trabalhar com o banco de dados, nós criamos uma abstração chamada `database.js`. Com ela, basta executar o médoto `database.query()` que toda gestão da conexão será feita por baixo dos panos e retornar o resultado pronto para ser usado.

Mas novamente, sugiro continuar assistindo as aulas e quando chegarmos na parte de programar as regras de negócio e consultas ao banco, tudo irá fazer mais sentido 🤝