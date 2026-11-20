# Validação da Aplicação — Entrega 2

## Objetivo

Comprovar que a aplicação de gestão de biblioteca funciona de ponta a ponta, com backend, frontend e banco de dados integrados. Este documento separa implementação existente, testes automatizados e evidências que ainda precisam ser coletadas em execução.

## Repositórios executáveis

- Backend: https://github.com/JoaoPauloOlt/library-api
- Frontend: https://github.com/JoaoPauloOlt/library-web

## Matriz de validação funcional

| Cenário | Resultado esperado | Evidência a coletar |
|---|---|---|
| Autenticação | Login e emissão de JWT conforme perfil | Captura do login e dashboard |
| Catálogo | Listagem de livros e disponibilidade | Captura do catálogo |
| Solicitação | USER solicita exemplar disponível | Tela e registro criado |
| Atendimento | LIBRARIAN registra empréstimo para usuário ativo | Tela e registro criado |
| Aprovação | REQUESTED → ACTIVE; exemplar → LOANED | Tela e consulta do banco/API |
| Atraso | ACTIVE → LATE após vencimento | Registro com status e dueDate vencida |
| Devolução | LATE → RETURNED; exemplar → AVAILABLE | Tela e consulta do banco/API |
| Multa | Multa OPEN persistida, com dias e valor corretos | Tela de multas e registro persistido |
| Consulta própria | USER consulta somente suas multas | Captura autenticada como USER |
| Consulta global | LIBRARIAN/ADMIN consultam multas globais | Captura autenticada como funcionário |
| Isenção | ADMIN isenta multa OPEN com justificativa e auditoria | Status WAIVED, responsável, data e motivo |

## Regras de negócio de multas

- Tarifa diária: R$ 2,00.
- Tolerância: nenhuma.
- Contagem: dias corridos (calendário).
- Fuso de negócio: America/Sao_Paulo.
- Limite máximo: inexistente.
- Devolução na data de vencimento ou antes: sem multa.
- Pagamento: fora do escopo atual.
- Isenção: somente ADMIN, com justificativa obrigatória e trilha de auditoria.

Fórmula:

`multa = dias_de_atraso × 2,00`

## Testes automatizados

Backend — executar na raiz de `library-api`:

```bash
./mvnw verify
```

A suíte utiliza PostgreSQL e aplica o gate de cobertura JaCoCo definido no projeto. O módulo de multas possui testes unitários e testes de integração que verificam a devolução atrasada, a persistência da multa, a atualização do exemplar, os eventos da Outbox, a devolução no prazo, a prevenção de duplicidade e a isenção administrativa.

Frontend — executar na raiz de `library-web`:

```bash
npm ci
npm test
npm run lint
npm run build
```

## Execução reproduzível

Backend com Docker Compose:

```bash
cp .env.example .env
docker compose up --build
```

A API fica disponível em `http://localhost:8080`. O Compose inicia PostgreSQL, RabbitMQ e API no perfil `dev`. O seed de desenvolvimento fornece contas e cenários de demonstração. Para restaurar os dados locais, seguir o procedimento seguro de reset documentado no README da API.

Frontend:

```bash
cp .env.example .env
npm ci
npm run dev
```

Configurar `VITE_API_URL=http://localhost:8080` no ambiente local. A aplicação fica disponível em `http://localhost:5173`.

## Roteiro de demonstração para a banca

1. Entrar como USER e solicitar um livro disponível.
2. Entrar como LIBRARIAN e aprovar a solicitação.
3. Demonstrar que o exemplar deixa de estar disponível.
4. Utilizar o cenário de empréstimo atrasado do seed de desenvolvimento.
5. Registrar a devolução pela interface de circulação.
6. Demonstrar o status RETURNED, a disponibilidade restaurada e a multa criada.
7. Entrar como USER e consultar a multa própria.
8. Entrar como ADMIN, isentar a multa com justificativa e demonstrar os dados de auditoria.
9. Apresentar o CI e os testes de integração do backend e frontend.

## CI automatizado verificado em 20/11/2026

Os seguintes pipelines foram consultados no GitHub Actions e concluíram com sucesso:

- Backend — cenário de seed e empréstimo atrasado, PR [#92](https://github.com/JoaoPauloOlt/library-api/pull/92), [execução CI #849](https://github.com/JoaoPauloOlt/library-api/actions/runs/44738655566). Executou Maven verify, PostgreSQL, JaCoCo e SonarCloud.
- Backend — integração de multas com PostgreSQL, PR [#90](https://github.com/JoaoPauloOlt/library-api/pull/90), [execução CI #823](https://github.com/JoaoPauloOlt/library-api/actions/runs/44374906878). Verificou devolução atrasada, persistência da multa, disponibilidade do exemplar, eventos da Outbox, devolução no prazo, prevenção de duplicidade e isenção administrativa.
- Frontend — integração da tela de multas, PR [#24](https://github.com/JoaoPauloOlt/library-web/pull/24), [execução Frontend CI #157](https://github.com/JoaoPauloOlt/library-web/actions/runs/44739019374). Lint, testes e build concluídos com sucesso.
- Frontend — fluxo de circulação de funcionários, PR [#23](https://github.com/JoaoPauloOlt/library-web/pull/23), [execução Frontend CI #153](https://github.com/JoaoPauloOlt/library-web/actions/runs/43443254099). Lint, testes e build concluídos com sucesso.

Esses resultados comprovam a execução automatizada dos respectivos repositórios e cenários. Eles não substituem a demonstração manual da aplicação integrada com os três perfis e a coleta de capturas de tela.

## Registro de evidências

| Evidência | Status |
|---|---|
| Backend e banco iniciados do zero | Pendente de captura |
| Frontend conectado à API | Pendente de captura |
| Login dos três perfis | Pendente de captura |
| Solicitação e aprovação | Pendente de captura |
| Empréstimo atrasado | Pendente de captura |
| Devolução e disponibilidade | Pendente de captura |
| Multa persistida | Pendente de captura |
| Consulta e isenção administrativa | Pendente de captura |
| CI backend e frontend aprovado | Comprovado por execuções GitHub Actions #849, #823 e #157; anexar capturas dos resultados à apresentação |

Não declarar a validação completa apenas com base na existência de endpoints ou testes. A pontuação deve ser sustentada por execução integrada observável e evidências anexadas à entrega.
