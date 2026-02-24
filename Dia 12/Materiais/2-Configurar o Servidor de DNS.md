# Configurar o Servidor de DNS

Nesta Pista Lenta iremos configurar nosso próprio **Servidor Autoritativo** (Servidor de DNS), para que ele aponte lá para o Servidor da Vercel, que é onde ta o nosso site 💪

## Chorinho sobre Servidor de DNS

**[Clique aqui para acessar a aula](https://curso.dev/web/configurar-servidor-dns-chorinho)** 🤝

## Registro.br possui um "Modo Avançado"

Eu não sabia, mas o Rodrigo Kulb colocou [nesta resposta](https://curso.dev/alunos/rodrigoKulb/2c901041-9734-4705-822d-829d2550a316) que o Registro.br possui um **Modo Avançado** onde ele fornece para você um Servidor Autoritativo completo 😍

## Perguntas frequentes

**Por que usar o servidor DNS da `Vercel` em vez do `Registro.br`?**

A vantagem de utilizar o servidor DNS da Vercel é que, além de centralizar as configurações do nosso projeto em um lugar só, ela facilita algumas coisas para a gente, como a inserção automática de registros `DNS` para o domínio ou subdomínios criados.

Outros benefícios podem ser conferidos [aqui](https://vercel.com/docs/projects/domains/working-with-nameservers#benefits-of-using-vercel-nameservers).

De qualquer forma, você não é obrigado a usar o servidor DNS da Vercel. Pode ficar com o do Registro.br, caso prefira. 🤝

* * *

**Erro "Another Vercel account is using this domain" ou "Verification needed"**

Isso acontece quando alguém já tinha inserido esse mesmo domínio lá na Vercel. Então, mesmo que você seja o dono do domínio, para a Vercel a titularidade dele pertence a outra pessoa.

**Como resolver:**

Você vai precisar [comprovar a posse do domínio](https://vercel.com/docs/domains/working-with-domains/add-a-domain#verify-domain-access), inserindo o registro `TXT` indicado pela Vercel no servidor de DNS oferecido pelo Registro.br. Para fazer isso, você precisa habilitar o modo avançado no Registro.br que o Filipe colocou na descrição da aula.

**Atenção:** Na coluna `NOME` do registro `TXT`, você deve colocar apenas `_vercel`, e não o caminho completo como `_vercel.seudominio.com.br`.

Caso você ache muito complicado realizar esse processo, você pode permanecer com o servidor autoritativo que o `Registro.br` fornece sem problema algum. 🤝

* * *

**A interface da `Vercel` mudou e não encontro a opção `Nameservers`**

O layout da Vercel mudou, e a opção correspondente agora é a `Vercel DNS`.

Se você clicar nessa aba, verá que aparecem os mesmos endereços mostrados na aula:

-   `ns1.vercel-dns.com`
-   `ns2.vercel-dns.com`

Basta adicionar esses endereços como servidores DNS 1 e 2 no painel do domínio no `Registro.br`, como o Filipe ensina a partir do minuto `7:10` da aula.

* * *

**Por que demora cerca de 2 horas para a propagação do DNS?**

Isso é por conta da rede de `DNS` ser uma estrutura global e robusta, cujo funcionamento é crítico para a sustentação da internet, e leva tempo para essa mudança alcançar todos os servidores do mundo.

Outro fator que deve ser levado em consideração é que esses registros ficam armazenados na rede por um período na forma de `cache`, que também possui um tempo de validade.

Segundo a própria documentação do Registro.br, pode levar até [1 hora](https://registro.br/tecnologia/caracteristicas-tecnicas/#:~:text=Em%20ambos%20os%20modos%2C%20devido%20ao%20car%C3%A1ter%20distribu%C3%ADdo%20das%20informa%C3%A7%C3%B5es%20DNS%2C%20o%20tempo%20para%20que%20as%20altera%C3%A7%C3%B5es%20sejam%20vis%C3%ADveis%20em%20toda%20a%20Internet%20(TTL%20%2D%20Time%20To%20Live)%20%C3%A9%20de%20at%C3%A9%201%20hora.) para que a propagação seja completa. É preciso um pouquinho de paciência nessa etapa.

* * *

**Ainda não entendi muito bem o que são o `servidor autoritativo`, o `TLD` e como funciona o fluxo de resolução de DNS**

O **Servidor TLD (Top-Level Domain)** é simplesmente o responsável por cuidar dos domínios que estão registrados dentro daquele domínio de topo, no nosso caso o `.br`. Qualquer busca por um domínio que termine com `.br` vai ter que "bater" nesse servidor para saber o endereço do servidor autoritativo.

Já o **Servidor Autoritativo** é aquele que possui a resposta definitiva do endereço `IP` do servidor onde o site está hospedado. Na cadeia de resolução de `DNS`, ele é a última ponta (servidor) a ser contactada para poder traduzir o domínio num endereço IP.

**O fluxo resumido:**

1.  O `Root Server` direciona a busca para o servidor responsável pelo domínio de topo (`TLD`)
2.  O servidor `TLD` (responsável pelo `.br`) informa o endereço do servidor autoritativo
3.  O `Servidor Autoritativo` devolve o IP do servidor final onde o site está hospedado

Essas aulas sobre DNS são bem densas, e é natural que no primeiro contato as coisas fiquem um pouco nebulosas. Uma excelente estratégia para consolidar melhor essas informações é revisar essas aulas.

* * *

**Posso mudar o domínio para outro projeto na `Vercel` depois?**

Pode sim! Você pode configurar o seu domínio para apontar para onde você quiser.

**Como fazer:**

1.  No dashboard do seu projeto antigo lá na Vercel, clique em `Settings` no menu superior
2.  No menu lateral, clique em `Domains`, depois no botão `Edit` do seu domínio, e por fim em `Remove`
3.  Volte para o dashboard geral da Vercel (o que lista todos os projetos que você tem)
4.  Clique em `Domains` no menu superior, depois no botão `Add Existing`
5.  Selecione o novo projeto, depois o seu domínio, e clique em `Add`
