# Não confie em nenhum serviço 🛑

Quando eu falo para não confiar nos serviços eu não estou falando no sentido **moral** em que eles "querem o seu mal" ou "querem fraudar você" de alguma forma. Até porque, todos os serviços que eu uso (seja em projetos pessoais ou projetos profissionais) eu confio bastante neste ponto... e é o **mínimo** na verdade.

Agora, uma coisa que você não pode confiar e que não existe, é `100% de Uptime`, ou seja, um serviço consiga dentro de um ano ficar online 100% do tempo nos mais de **31 milhões de segundos** que um ano tem.

### Status Pages

-   Vercel: [https://www.vercel-status.com/](https://www.vercel-status.com/)
-   AWS: [https://health.aws.amazon.com/health/status](https://health.aws.amazon.com/health/status)
-   GitHub: [https://www.githubstatus.com/](https://www.githubstatus.com/)

## Perguntas frequentes

**Como foi feita a migração de região do `curso.dev` quando a AWS caiu?**

Tecnicamente foi uma migração do _backend_, a camada da aplicação que faz o processamento dos dados. Por padrão, quando fazemos o deploy de uma aplicação na Vercel, as funções de computação/processamento de dados (as regras de negócio) são executadas na região de Washington, D.C., USA. E foi exatamente ela que teve a degradação.

O Filipe mudou manualmente para outra região por meio de um arquivo de configuração que é commitado no repositório. Na raiz do projeto, existe um arquivo chamado `vercel.json` onde é possível definir a região do deploy:

```json
{
  "regions": ["iad1"]
}
```

Para mudar de região, ele alterou para:

```json
{
  "regions": ["cle1"]
}
```

E o próximo deploy foi feito nesta outra região que estava sem problemas.

O Filipe explica esse processo nesse comentário aqui: [https://curso.dev/alunos/filipedeschamps/aaf70461-6616-4d43-9ea7-1fbdc7e0e594](https://curso.dev/alunos/filipedeschamps/aaf70461-6616-4d43-9ea7-1fbdc7e0e594) 🤝

* * *

**Onde o `curso.dev` está hospedado? Qual a relação entre Vercel e AWS?**

O `curso.dev` é hospedado na Vercel, que por baixo dos panos roda na AWS.

Isso significa que a Vercel usa, por baixo dos panos, as `Lambdas` da AWS. Então quando ocorreu o problema na região `us-east-1` da AWS, a API do `curso.dev` foi afetada porque as funções de processamento estavam nessa região.

A Vercel não hospeda nada desta parte, ela só administra. Por isso foi possível migrar facilmente para outra região através do arquivo de configuração `vercel.json`.

* * *

**O TabNews tem uma página de status?**

Sim! É essa aqui: [https://www.tabnews.com.br/status](https://www.tabnews.com.br/status) 🤝

* * *

**Vamos criar uma página de status no curso?**

Vamos sim! Inclusive será uma das primeiras! 🤝

* * *

**É possível configurar regiões de backup na Vercel?**

Segundo a [documentação da Vercel](https://vercel.com/docs/functions/configuring-functions/region), usuários dos planos Pro e Enterprise podem passar uma lista de regiões _padrão_:

-   Usuários **Pro** podem fazer deploy em até três regiões
-   Usuários **Enterprise** podem fazer deploy em regiões ilimitadas

Além disso, os usuários do plano Enterprise podem definir a propriedade [`functionFailoverRegions`](https://vercel.com/docs/project-configuration#functionfailoverregions) especificando regiões de backup para caso as regiões padrão estejam indisponíveis.