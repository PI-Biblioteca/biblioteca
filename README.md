# Sistema de Gestão de Biblioteca

Projeto Integrado 2026/2 — Sistema de Gestão de Biblioteca.

## Contexto

Projeto acadêmico desenvolvido para o Projeto Integrado da Faculdade Anhanguera, com foco em uma biblioteca de faculdade e em sua operação pelos funcionários responsáveis pelo atendimento e pelo acervo.

O repositório principal do Projeto Integrado é destinado à documentação, modelagem e evidências da entrega. A implementação executável está mantida em repositórios separados e integrados:
- Backend: [JoaoPauloOlt/library-api](https://github.com/JoaoPauloOlt/library-api)
- Frontend: [JoaoPauloOlt/library-web](https://github.com/JoaoPauloOlt/library-web)

A validação da Entrega 2 deve considerar o estado integrado dos dois repositórios, e não apenas os artefatos de documentação.

## Equipe

- João Paulo
- Caike Assis
- Khaled Fatah
- Murillo Santos
- Gustavo Dourado

Turma: 2º semestre — 2026/2.

## Estrutura documental

- `docs/` — requisitos, modelagem, algoritmos, matemática e matriz de integração.
- `entrega 1/` — apresentação, trabalho escrito e anexos da Entrega 01.
- `CONTRIBUTING.md` — orientações de contribuição.
- `README.md` — visão geral e organização do projeto.

## Linha de base e incremento

A linha de base acadêmica corresponde aos requisitos, modelagem, protótipos e DDL produzidos anteriormente pela equipe.

O incremento de 2026/2 concentra-se na revisão da modelagem, integração das disciplinas, modelagem algorítmica e matemática, unidade funcional de devolução e organização documental. A separação está registrada em [Linha de Base e Organização](./docs/linha-de-base.md).

## Implementação prevista

### Backend

O backend executável está no repositório [JoaoPauloOlt/library-api](https://github.com/JoaoPauloOlt/library-api), com Java 17, Spring Boot, Spring Security, JWT/RBAC, JPA/Hibernate e PostgreSQL.

Tecnologias previstas:
- Java 17
- Spring Boot 3
- Spring Security, JWT e RBAC
- PostgreSQL
- JPA / Hibernate
- Maven e testes automatizados com JaCoCo

A base será simplificada e ajustada ao escopo e às limitações acadêmicas do Projeto Integrado antes de ser considerada a implementação oficial.

### Frontend

O frontend executável está no repositório [JoaoPauloOlt/library-web](https://github.com/JoaoPauloOlt/library-web), desenvolvido com React, Vite, React Router e Axios. Ele consome a API por meio de `VITE_API_URL` e aplica as permissões RBAC na navegação e nas operações.

## Escopo acadêmico inicial

- Cadastro de livros e autores
- Cadastro de usuários
- Registro de empréstimos
- Registro de devoluções
- Consulta de disponibilidade
- Histórico de empréstimos
- Cálculo dos dias de atraso
- Geração e consulta de multas decorrentes da devolução em atraso

O escopo poderá ser refinado durante as etapas de desenvolvimento, sem ampliar desnecessariamente a primeira versão.
