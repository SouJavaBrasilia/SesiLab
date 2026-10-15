# Arquitetura — SouJava Junior / SESI Lab

> **Status:** diretriz aprovada na reunião de 13/10/2026; detalhamento técnico pendente.

## Diretrizes

- **Arquitetura inicial:** monólito modular, priorizando uma solução compreensível para participantes juniores.
- **Stack-base:** backend Java e frontend Angular.
- **Abordagem pedagógica:** não impor DDD como requisito inicial, evitando complexidade desnecessária.
- **Modularização:** limites e responsabilidades dos módulos serão discutidos e documentados pelo time.

## Atenção ao termo BFF

As anotações da reunião também mencionam **BFF**, mas monólito modular e BFF não são sinônimos. A equipe ainda precisa definir se haverá uma camada BFF, quais responsabilidades ela terá e como se dará a integração entre Angular e Java.

## Decisões pendentes

- Versões de Java e Angular e framework backend.
- Modelo de dados, persistência e migrações.
- Contratos de API, autenticação e autorização.
- Estrutura de módulos, testes, CI/CD e implantação.

Documente decisões nas issues e submeta mudanças à revisão. O objetivo principal é que os juniores aprendam e evoluam construindo o produto.
