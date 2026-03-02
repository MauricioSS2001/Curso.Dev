# Inauguração Milestone 1: Fundação

## Comparações entre tecnologias
Mesmo que uma tecnologia se torne obsoleta, o conhecimento adquirido servirá para realizar comparações e entender `Trade-offs` entre elas.

**<i>Trade-off</i>:** Relação onde um ponto é mais positivo enquanto outro é menos gerando uma compensação.

**Exemplo:** O protocolo `TCP` é **mais lento**, porém **garante integridade de pacotes**. Já o protocolo `UDP` é **mais rápido**, porém **não garante integridade de pacotes.
<br>

## Planejamento de um projeto
- Começar pelo `Frontend` para definir como a **fundação** será construída.
    - Considerar que é a parte onde o usuário terá acesso a aplicação.
<br>

## Banco de Dados Local vs Remoto
- Iniciar o proejto sempre com um `Banco de Dados Local` para eviitar problemas posteriores.
<br>

- `Banco de Dados Remotos` geralmente são utilizados para **ambientes de produção**.
<br>

---
---
---
<br>

# Uma história macabra sobre "Overengineering"

## Overengineering
`Overengineering` pode ser traduzido como **"Excesso de Engenharia"** e significa **construir algo muito complexo** no lugar de algo que **deveria ser simples**.
<br>

## Underengineering
`Underengineering` pode ser traduzido como **"Falta de Engenharia"** e significa **construir algo abaixo do ideal**.
<br>

## O principal quesito da construção de um software
O principal quesito da construção de um software é o quão **"modificável"** ele é. Este quesito leva em consideração alguns outros, listados abaixo:
- Lingugagem de porgamação
- Arquitetura
- Modelagem
- Testes Automatizados

> Nada é tão perigoso quanto um software que não pode sofrer manutenção.

<br>

---
---
---
<br>

# Arquitetura e Organização de Pastas
`Arquitetura` e `Organização de Pastas` são coisas diferentes.
- **Arquitetura**
    - MVC (Model, View, Controller)
    - Clean Architecture

O que define a `arquitetura de software` é o **escopo** (que delimita início e término) de componentes e o **tipo de interação** entre eles.
<br>

> Arquitetura simples com ótima modelagem faz o projeto ir longe.

**Nota:** O projeto será construído utilizando a **arquitetura MVC**.
<br>

## Estrutura MVC do projeto
> 📦root/
├──📂pages/
│   └──📄index.js
├──📂models/
│   ├──📄users.js
│   ├──📄content.js
│   └──📄password.js
├──📂infra/
│   ├──📄database.js
│   ├──📂migrations/
│   └──📂provisioning/
│       ├──📂staging/
│       └──📂production/
└──📂tests/

<br>

---
---
---
<br>

# PoC e MVP ajudam mesmo?

## Poc VS MVP
- **Poc (Proof of Concept / Prova de Conceito)**
    - Construir ideias (<i>features</i>) menores e ir refinando para se tornar um projeto maior.
    - Pequenas **"provas"** para modelagem da cosntrução do projeto.
    - As "provas" **devem ser baratas**, ou seja, empregar um **esforço pequeno** para seus desenvolvimentos.
    > A PoC é mais voltada para a validação interna (para ver se a ideia é tecnicamente viável pelo ângulo daqueles que vão executar).

<br>

- **MVP (Minimum Viable Product / Produto Mínimo Viável)**
    - Solução mínima do sistema para validação.
    - Busca validação do cliente final, ou seja, "Este sistema faz sentido? Alguém pagará para usar isto?".
    > O MVP está mais relacionado à validação externa (para ver se há clientes que estão dispostos a usar/pagar pelo produto).