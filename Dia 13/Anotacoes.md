# Página "Em Construção" e Encerramento da Milestone 0

## Ideia/Teoria McDonald's
Desenvolvida em 2013 por **Jon Bell** e consiste na escolha de caminhos para avanço nas etapas.
> Considere um escritório em uma segunda-feira onde os funcionários querem almoçar juntos. Como niinguém sugere nenhum restaurante, o primeiro cita o MacDonald's, fazendo com que os demais discordem e exponham outras alternativas que tem mais interesse.

- **Sugira algo bizarro ou sem compromisso algum para fazer os demais começarem a sugerir.**
- A **ideia ruim** levará a **ideias melhores**.
<br>

---
---
---
<br>

# Não confie em nenhum serviço

## 100% Uptime
**Nenhum serviço** consegue manter `100% Uptime` ou seja, nenhum deles é capaz de estar ativo sem nenhuma queda durante os 365 dias do ano (Mais de 31.000.000 de segundos).

A maior parte dos serviços promete entrega de `99% Uptime` ao ano.
- 9 horas ao ano ou 44 minutos ao mês de quedas, manutenções, <i>bug's</i>m etc...
<br>

## SLA (Service Level Agreement) / (Acordo de Nível de Serviço)
Acordo que estabele o percentual `Uptime` do serviço.
<br>

## Status Pages
Páginas especializadas em mostrar a "saúde" do serviços contratados (se o serviço está funcionando ou não).
Para realizar uma pesquisa, basta utilizar o modelo abaixo em qualquer navegador:
~~~ Browser
<serviço> status
~~~
Por exemplo, "**Vercel status**".
- <a href="https://www.vercel-status.com/">Vercel status</a>
- <a href="https://health.aws.amazon.com/health/status">AWS status</a>

**Nota:** Cadeias de serviços podem desestabilizar aplicações, por exemplo como a `Vercel` mantém servidores na `AWS`, ela depende da saúde da `AWS` para manter alguns serviços rodando.