# Configurar scripts dos serviços

Essa aqui vai ser mais uma aula com **lapidações**, mas uma **super importante**, porque a gente vai deixar o projeto alinhado para quando a gente for trabalhar na issue de `Continuous Integration` 💪 Fora isso, a aula é repleta com dicas extras 😍

### Link para o commit feito na aula

-   [add services scripts](https://github.com/filipedeschamps/clone-tabnews/commit/dcda2172bec466cbd7efb972df710c6f85b3be73)

### Observação

O aluno `thiagosantana` fez uma observação importante sobre a remoção de volumes com o comando `docker compose down`, que foi respondida nesse comentário [aqui](https://curso.dev/alunos/Andrei/6413a0f0-ef53-45c9-a496-6a0f074789d1).

<br>

---
<br>

# Comentário

Respondendo a [**"Pessoal, por favor, me ignorem causa eu esteja falando alguma groselha, mas se eu entendi certo a informação mínuto 3:55 da aula está parcilamente certo pois o comando 'docker compose dow..."**](https://curso.dev/alunos/thiagosantana/f41a117c-58d2-448b-ab18-9eb1da47a79f) dentro da publicação [**Configurar scripts dos serviços**](https://curso.dev/web/configurar-scripts-servicos)
<br>

[Andrei](https://curso.dev/alunos/Andrei)


`thiagosantana`, você está corretíssimo acerca do comportamento do comando `docker compose down`! 💪

Ao executá-lo "puro", os volumes (nomeados ou anônimos) relacionados ao contêiner removido ainda permanecem. Para removê-los também é preciso passar a opção [`--volumes` ou `-v`](https://docs.docker.com/reference/cli/docker/compose/down/#:~:text=Remove%20named%20volumes%20declared%20in%20the%20%22volumes%22%20section%20of%20the%20Compose%20file%20and%20anonymous%20volumes%20attached%20to%20containers).

Mas, ainda assim, usar apenas o `docker compose down` acaba servindo para o nosso propósito de criar uma instância do banco "zerada", porque o volume que é criado a partir da imagem que estamos usado é do tipo _**anônimo**_. [E volumes anônimos não são compartilhados entre contêineres automaticamente](https://docs.docker.com/storage/#:~:text=If%20you%20create%20multiple%20containers%20after%20each%20other%20that%20use%20anonymous%20volumes%2C%20each%20container%20creates%20its%20own%20volume.%20Anonymous%20volumes%20aren%27t%20reused%20or%20shared%20between%20containers%20automatically.) (conforme também [aqui](https://docs.docker.com/reference/cli/docker/compose/down/#:~:text=Anonymous%20volumes%20are,or%20named%20volumes.)). Então, quando executamos o "down" e depois o "up", um novo contêiner é criado juntamente com um novo volume anônimo.

Muito obrigado por chamar a atenção para esse detalhe, meu caro! 🤝