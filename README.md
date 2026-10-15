<div align="center">

# 📦 SESI Lab — Sistema de Gestão de Estoque

### 🚀 SouJava Junior · Fábrica de Software | SouJava Brasília

**Um projeto real, construído em comunidade, para aprender, colaborar e entregar software com propósito.**

[![Java](https://img.shields.io/badge/Backend-Java-ED8B00?logo=openjdk&logoColor=white)](https://www.java.com/)
[![Angular](https://img.shields.io/badge/Frontend-Angular-DD0031?logo=angular&logoColor=white)](https://angular.dev/)
[![GitHub Issues](https://img.shields.io/badge/Planejamento-GitHub_Issues-181717?logo=github)](https://github.com/SouJavaBrasilia/SesiLab/issues)
[![GitHub Projects](https://img.shields.io/badge/Quadro-Kanban-0969DA?logo=github)](https://github.com/orgs/SouJavaBrasilia/projects/1)

[**📋 Kanban**](https://github.com/orgs/SouJavaBrasilia/projects/1) · [**🎯 Issues**](https://github.com/SouJavaBrasilia/SesiLab/issues) · [**☕ SouJava Brasília**](https://soujava.org.br/brasilia)

</div>

---

## 👋 Boas-vindas

Este repositório reúne o desenvolvimento do **Sistema de Gestão de Estoque do SESI Lab**, primeiro desafio da iniciativa **SouJava Junior / Fábrica de Software do SouJava Brasília**.

A iniciativa aproxima pessoas com diferentes níveis de experiência de um ciclo real de desenvolvimento: entendimento do problema, definição de requisitos, prototipação, implementação, testes, revisão e entrega. A participação é colaborativa e voluntária; **não é necessário dominar toda a stack para começar**.

> **Estado atual:** organização do MVP, prototipação das telas e preparação para validação com o SESI Lab. Funcionalidades e decisões técnicas descritas como *propostas* ainda estão sujeitas a refinamento e aprovação.

## 🧭 O problema que queremos resolver

O sistema busca apoiar o controle do estoque do SESI Lab, tornando mais claras as quantidades disponíveis, o registro de entradas e retiradas e o histórico das movimentações.

**Resultados esperados:**

- Centralizar a consulta e o cadastro dos itens de estoque.
- Registrar entradas e retiradas com rastreabilidade.
- Apoiar o acompanhamento de quantidades e alertas.
- Organizar o acesso conforme as responsabilidades dos usuários.
- Reduzir controles manuais e facilitar a consulta ao histórico.

## 🎯 Escopo funcional inicial (MVP)

As funcionalidades abaixo representam o **levantamento inicial** e devem ser refinadas nas issues e validadas com o SESI Lab.

| Área | Funcionalidades previstas |
| --- | --- |
| Acesso | Login e navegação conforme o perfil do usuário |
| Dashboard | Visão geral do estoque e indicadores a definir |
| Itens | Listagem, consulta e cadastro de itens |
| Movimentações | Registro de entradas e retiradas |
| Histórico | Consulta das movimentações realizadas |
| Alertas | Identificação de itens com estoque baixo, conforme regras a definir |
| Administração | Gestão de usuários, permissões e dados de referência |

### 👥 Perfis inicialmente considerados

| Perfil | Responsabilidades previstas |
| --- | --- |
| **Usuário** | Consultar itens e solicitar/registrar retiradas, conforme fluxo aprovado |
| **Controlador de estoque** | Gerenciar itens, quantidades e movimentações |
| **Administrador** | Administrar usuários, permissões e dados de referência |

Os limites de permissão e os fluxos de aprovação ainda precisam ser especificados. A tabela acima **não substitui uma matriz formal de autorização**.

### 📏 Regras de negócio a detalhar

- Validação de campos obrigatórios e consistência dos dados.
- Regras para quantidades disponíveis e prevenção de retiradas inválidas.
- Registro de movimentações para consulta e auditoria.
- Critérios e limites para alertas de estoque.
- Permissões por perfil e comportamento esperado em operações não autorizadas.

> Não considere essas regras como especificação fechada: cada comportamento deve ter critérios de aceite e ser validado com os responsáveis pelo produto.

## 🧰 Tecnologias e ferramentas

| Frente | Definição atual |
| --- | --- |
| **Backend** | Java |
| **Frontend** | Angular |
| **Design / UX** | **Ferramenta livre:** Penpot, Figma ou outra escolhida pelos participantes |
| **Versionamento** | Git e GitHub |
| **Gestão de tarefas** | GitHub Issues + GitHub Projects |
| **Colaboração** | Issues, discussões técnicas e pull requests |

**Importante sobre prototipação:** não há obrigação de usar Penpot. **Figma também é bem-vindo.** O essencial é que o resultado seja compartilhável, revisável pela equipe e adequado para apresentação ao SESI Lab. Caso existam protótipos em ferramentas diferentes, a equipe deverá combinar como consolidar a versão a ser validada.

**Ainda não definidos formalmente:** versão do Java e do Angular, framework específico do backend, banco de dados, estratégia de autenticação, hospedagem, pipelines, testes automatizados e arquitetura detalhada. Essas escolhas devem ser discutidas e registradas antes de serem tratadas como padrão do projeto.

## 🗂️ Organização do trabalho

Acompanhamos as entregas no [**GitHub Project — SESI Lab**](https://github.com/orgs/SouJavaBrasilia/projects/1).

```text
Backlog → Ready → In Progress → Review → Done
```

| Etapa | Significado |
| --- | --- |
| **Backlog** | Demanda identificada, ainda não preparada para execução |
| **Ready** | Atividade entendida, com escopo e critérios de aceite suficientes |
| **In Progress** | Alguém está trabalhando na atividade |
| **Review** | Entrega pronta para revisão técnica, funcional ou de design |
| **Done** | Entrega revisada e aceita segundo os critérios combinados |

### 📌 Primeiras atividades

| Issue | Entrega |
| --- | --- |
| [#1](https://github.com/SouJavaBrasilia/SesiLab/issues/1) | Consolidar escopo e fluxos do MVP |
| [#2](https://github.com/SouJavaBrasilia/SesiLab/issues/2) | Disponibilizar ambiente colaborativo de prototipação *(reavaliar à luz da liberdade de ferramentas)* |
| [#3](https://github.com/SouJavaBrasilia/SesiLab/issues/3) | Prototipar login e navegação por perfil |
| [#4](https://github.com/SouJavaBrasilia/SesiLab/issues/4) | Prototipar dashboard e listagem de estoque |
| [#5](https://github.com/SouJavaBrasilia/SesiLab/issues/5) | Prototipar cadastro e movimentações |
| [#6](https://github.com/SouJavaBrasilia/SesiLab/issues/6) | Revisar protótipo e apresentar ao SESI Lab |
| [#7](https://github.com/SouJavaBrasilia/SesiLab/issues/7) | Organizar backlog e orientações de contribuição |

As issues podem ser refinadas, divididas ou complementadas conforme a evolução do projeto. **Não há responsáveis ou prazos presumidos:** eles serão combinados com os voluntários.

## 🤝 Como contribuir

1. **Conheça o contexto:** leia este README e as [issues abertas](https://github.com/SouJavaBrasilia/SesiLab/issues).
2. **Escolha uma frente:** requisitos, UX/UI, frontend, backend, testes, documentação ou revisão.
3. **Converse na issue:** manifeste interesse e alinhe escopo, dependências e disponibilidade antes de começar.
4. **Registre o andamento:** mantenha a issue e seu status no Kanban atualizados; documente decisões e evidências da entrega.
5. **Compartilhe para revisão:** código por pull request; protótipos por link e registro na issue; documentação por proposta de alteração.
6. **Conclua com critérios claros:** a entrega deve atender aos critérios de aceite acordados e passar pela revisão aplicável.

### Boas práticas recomendadas

- Preferir mudanças pequenas e fáceis de revisar.
- Vincular pull requests à issue correspondente (ex.: `Closes #12`, quando apropriado).
- Descrever **o que mudou**, **por que mudou** e **como verificar**.
- Evitar incluir senhas, tokens, dados pessoais ou dados reais sensíveis no repositório.
- Não implementar regras de negócio presumidas sem discutir com a equipe.
- Registrar contribuições nas issues, inclusive para apoiar o acompanhamento das horas de participação e eventual certificação, conforme critérios definidos pela organização.
- Tratar sugestões e revisões com respeito: o projeto é também um espaço de aprendizagem.

### Modelo simples para comentários de andamento

```md
**Atualização:**
- O que foi feito:
- O que falta:
- Dúvidas ou bloqueios:
- Links/evidências (PR, protótipo, testes):
```

## 🎨 Fluxo de design e validação

A equipe pode trabalhar com **Penpot, Figma ou outra ferramenta**, desde que os artefatos possam ser compartilhados e revisados.

Fluxo sugerido:

1. Identificar usuários, objetivos e jornadas principais.
2. Desenhar os fluxos e protótipos das telas previstas para o MVP.
3. Revisar internamente navegação, campos, estados e permissões.
4. Consolidar a proposta a ser apresentada ao SESI Lab.
5. Registrar feedback e decisões nas issues.
6. Refinar os protótipos antes de implementar as telas correspondentes.

**Para uma entrega de protótipo**, inclua na issue: link de acesso, telas contempladas, fluxos principais, dúvidas pendentes e observações para revisão. O objetivo não é exigir uma ferramenta específica, mas garantir clareza e continuidade.

## 🏗️ Arquitetura e implementação

O produto prevê **frontend Angular** e **backend Java**. O desenho da solução, as responsabilidades dos componentes e os contratos de integração ainda devem ser detalhados em conjunto.

Antes de avançar em funcionalidades de implementação, a equipe deverá alinhar, conforme necessário:

- Modelo de dados e entidades de negócio.
- Contratos e convenções da API.
- Estratégia de autenticação e autorização.
- Validação, tratamento de erros e rastreabilidade.
- Estratégia de testes, ambiente local e processo de entrega.
- Padrões de código e organização dos módulos.

As decisões relevantes devem ser documentadas no repositório ou nas issues, com contexto e justificativa. **Evite presumir tecnologias não aprovadas.**

## 🔗 Links úteis

| Recurso | Link |
| --- | --- |
| **Repositório principal** | [SouJavaBrasilia/SesiLab](https://github.com/SouJavaBrasilia/SesiLab) |
| **Issues** | [Backlog de atividades](https://github.com/SouJavaBrasilia/SesiLab/issues) |
| **Kanban** | [GitHub Project #1](https://github.com/orgs/SouJavaBrasilia/projects/1) |
| **Referência inicial Angular** | [lsegala/front-angular](https://github.com/lsegala/front-angular) |
| **Skills de IA da comunidade** | [SouJavaBrasilia/skills-ia](https://github.com/SouJavaBrasilia/skills-ia) |
| **SouJava Brasília** | [soujava.org.br/brasilia](https://soujava.org.br/brasilia) |

> O repositório `front-angular` é uma referência inicial compartilhada com a equipe; a estrutura definitiva da aplicação deverá ser confirmada no projeto principal.

## 🗺️ Próximos marcos

- [ ] Consolidar o escopo e os fluxos do MVP.
- [ ] Organizar e compartilhar os protótipos, independentemente da ferramenta escolhida.
- [ ] Revisar internamente as jornadas e telas.
- [ ] Validar a proposta com o SESI Lab.
- [ ] Registrar decisões de arquitetura e contratos de integração.
- [ ] Detalhar e distribuir as primeiras tarefas de implementação.
- [ ] Definir critérios de teste, revisão e entrega.

## ❓ Perguntas frequentes

**Preciso saber Java e Angular para participar?**  
Não. Há espaço para contribuições em diferentes áreas e níveis de experiência.

**Penpot é obrigatório?**  
Não. A equipe pode usar Penpot, Figma ou outra ferramenta adequada. O importante é compartilhar o trabalho e possibilitar revisão.

**Posso começar a desenvolver qualquer funcionalidade?**  
Prefira alinhar antes na issue. Isso evita retrabalho e decisões conflitantes, especialmente enquanto o MVP está sendo validado.

**Como registro minha contribuição?**  
Use a issue correspondente para registrar atividades, links, evidências e eventuais bloqueios. O acompanhamento de horas e a certificação dependem dos critérios definidos pela organização.

**O escopo e a stack estão fechados?**  
Não completamente. Java e Angular são as tecnologias-base indicadas; os demais detalhes técnicos e funcionais precisam de alinhamento.

---

<div align="center">

### ☕ Aprender juntos. Construir juntos. Entregar juntos.

**SouJava Junior · SouJava Brasília**

*Código, colaboração e comunidade.*

</div>

---

## 🌱 Crescimento dos juniores: nosso propósito

O **SouJava Junior existe para que os juniores cresçam técnica e profissionalmente**. O desenvolvimento do sistema de estoque do SESI Lab é um meio para aprender fazendo, assumir pequenas entregas, receber mentoria, participar de revisões e desenvolver autonomia. A iniciativa é **voluntária e não remunerada**.

## 🧱 Diretrizes técnicas da reunião de 13/10/2026

- **Arquitetura inicial:** monólito modular, com limites dos módulos ainda a definir.
- **Backend:** Java; **frontend:** Angular.
- **DDD:** não será imposto como requisito inicial, evitando complexidade excessiva para iniciantes.
- **BFF:** termo mencionado na reunião; a responsabilidade dessa possível camada ainda precisa ser esclarecida.
- **Prototipação:** livre escolha entre **Figma, Penpot ou outra ferramenta**, desde que o trabalho possa ser compartilhado e revisado.
- **Design System e Storybook:** propostas para avaliação, **não decisões obrigatórias**.
- **Backlog técnico:** detalhamento colaborativo com Leonardo Segala e demais participantes, sem presumir responsáveis ou prazos não combinados.

📚 **Documentação complementar:** [Arquitetura](docs/ARQUITETURA.md) · [Reunião de 13/10](docs/REUNIAO-2026-10-13.md) · [Design System e Storybook](docs/DESIGN-SYSTEM.md)

---

## 🌱 Crescimento dos juniores: nosso propósito

O **SouJava Junior existe para que os juniores cresçam técnica e profissionalmente**. O desenvolvimento do sistema de estoque do SESI Lab é um meio para aprender fazendo, assumir pequenas entregas, receber mentoria, participar de revisões e desenvolver autonomia. A iniciativa é **voluntária e não remunerada**.

## 🧱 Diretrizes técnicas da reunião de 13/10/2026

- **Arquitetura inicial:** monólito modular, com limites dos módulos ainda a definir.
- **Backend:** Java; **frontend:** Angular.
- **DDD:** não será imposto como requisito inicial, evitando complexidade excessiva para iniciantes.
- **BFF:** termo mencionado na reunião; a responsabilidade dessa possível camada ainda precisa ser esclarecida.
- **Prototipação:** livre escolha entre **Figma, Penpot ou outra ferramenta**, desde que o trabalho possa ser compartilhado e revisado.
- **Design System e Storybook:** propostas para avaliação, **não decisões obrigatórias**.
- **Backlog técnico:** detalhamento colaborativo com Leonardo Segala e demais participantes, sem presumir responsáveis ou prazos não combinados.

📚 **Documentação complementar:** [Arquitetura](docs/ARQUITETURA.md) · [Reunião de 13/10](docs/REUNIAO-2026-10-13.md) · [Design System e Storybook](docs/DESIGN-SYSTEM.md)
