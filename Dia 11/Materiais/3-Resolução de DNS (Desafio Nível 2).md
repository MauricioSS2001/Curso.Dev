# Resolução de DNS (Desafio Nível 2)

Nesta aula iremos passar por toda cadeia de resolução de um `DNS` e entender de fato como que através de um `domínio` é possível descobrir o `IP` do servidor 💪

## Perguntas frequentes

**Como funciona o cache/TTL no DNS, onde é armazenado e qual o impacto no SEO?**

O cache das resoluções de DNS é armazenado apenas na máquina local e no `Recursive Resolver`. Pense o seguinte: o cache é um meio de armazenar a resposta de uma "pergunta", para não ser necessário perguntar novamente. E na cadeia de resolução de DNS, os únicos "membros" que "perguntam" são o computador local e o `Recursive Resolver`. O `Root Server`, `TLD`, e `Authoritative Server` apenas respondem, e por isso não precisam "memorizar" nenhuma resposta.

O TTL (Time To Live) define por quanto tempo uma informação de cache pode ser considerada válida. Enquanto esse tempo não expira, os dispositivos que armazenaram o cache continuarão utilizando os dados antigos, já que não é possível invalidá-lo forçadamente.

Como o cache reduz o tempo de resolução, a página pode ficar mais fácil de ser acessada, o que pode [de forma indireta afetar positivamente o SEO](https://www.cloudns.net/blog/dns-and-seo-how-does-dns-service-affect-seo/#:~:text=Having%20a%20domain%20that%20resolves%20faster%20will%20be%20translated%20to%20a%20superior%20user%20experience%20for%20your%20visitors%2C%20which%20will%20be%20seen%20as%20a%20great%20SEO%20sign.). Porém, um TTL alto pode afetar negativamente durante trocas de hospedagem, pois levaria mais tempo para a informação em cache ser invalidada. Por isso, de acordo com [essa fonte](https://blog.nameshield.com/blog/2019/02/21/can-the-dns-have-an-impact-on-the-seo/#:~:text=A%20low%20TTL%20allows%20to%20limit%20the%20impact%20during%20these%20modifications.), seria recomendado reduzir o TTL para limitar o direcionamento para um endereço IP que não está sendo mais utilizado. 🤝

Caso queira se aprofundar mais: [Cloudflare - O que é DNS](https://www.cloudflare.com/pt-br/learning/dns/what-is-dns/#:~:text=O%20que%20%C3%A9%20o%20armazenamento%20em%20cache%20de%20DNS%3F%20Onde%20o%20armazenamento%20em%20cache%20de%20DNS%20ocorre%3F)

* * *

**Como funciona a estrutura de domínios com múltiplos níveis (ex: `.com.br`)? Nesse caso são dois TLDs?**

Na verdade é apenas um TLD. O `.com` é uma subcategoria dentro do `.br`.

No caso de um domínio como o `tabnews.com.br`, o `Top-Level Domain` é apenas o `.br`, e o `.com` é chamado de `Second-Level Domain`, [e é controlado pelo mesmo administrador do TLD](https://www.icann.org/en/icann-acronyms-and-terms?nav-letter=t&page=1#:~:text=The%20administrators%20of%20a%20TLD%20control%20which%20second%2Dlevel%20domains%20are%20recognized%20within%20the%20TLD.).

Então, a consulta ao servidor TLD já retorna o `Authoritative Server` para o domínio em questão. Mesmo que o `.com.br` exigisse uma subconsulta interna no servidor TLD do `.br`, ela não seria no nível da cadeia de DNS, e um hipotético acréscimo de velocidade seria desprezível.

A escolha entre `.com` e `.com.br` vai depender do seu público alvo. Domínios com ccTLDs (como o `.br`) [tendem a ranquear melhor em buscas locais do Google](https://backlinko.com/google-ranking-factors#domain-factors:~:text=9.%20Country%20TLD%20extension%3A%20Having%20a%20Country%20Code%20Top%20Level%20Domain%20(.cn%2C%20.pt%2C%20.ca)%20can%20sometimes%20help%20the%20site%20rank%20for%20that%20particular%20country%E2%80%A6%20but%20it%20can%20limit%20the%20site%E2%80%99s%20ability%20to%20rank%20globally.).

* * *

**Como o servidor TLD sabe qual `Authoritative Server` referenciar?**

O servidor TLD sabe qual Nameserver (ou Authoritative Nameserver) referenciar, porque nós cadastramos o endereço desse servidor lá quando registramos o nosso domínio.

Isso vai ficar mais claro na aula [Configurar o Servidor de DNS](https://curso.dev/web/configurar-servidor-dns) do próximo dia.

* * *

**Por que não consultamos diretamente o `Authoritative Server`?**

Na prática, nós até poderíamos consultar diretamente os servidores autoritativos de um domínio, mas não é assim que funciona no dia a dia porque o sistema de DNS foi projetado para ser escalável e eficiente.

Se cada navegador ou aplicação fosse direto nos servidores autoritativos a cada requisição, eles ficariam sobrecarregados rapidamente.

Por isso existem os `Recursive Resolvers` (como os do seu provedor ou do Google/Cloudflare), que fazem esse papel de buscar a resposta nos servidores autoritativos e depois armazenam em cache por um tempo definido pelo TTL. Assim, quando você faz uma nova consulta para o mesmo domínio, a resposta vem muito mais rápido do cache, sem precisar repetir todo o caminho até os servidores autoritativos.

* * *

**O que acontece com a parte depois da barra (`/`) na URL?**

O que vem depois da `/` já não faz parte da resolução do domínio. O que vem ali se trata de uma página ou recurso a ser acessado dentro do servidor.

Então, quando o domínio `amazon.com` é resolvido, o seu navegador manda uma requisição para acessar a página `orders` daquele site.

* * *
