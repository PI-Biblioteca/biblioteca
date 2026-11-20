# Linha de Base e Organização

## Linha de base acadêmica

A linha de base deste Projeto Integrado corresponde aos artefatos acadêmicos produzidos anteriormente pela equipe para o sistema de biblioteca.

Ela serve como referência para o incremento desenvolvido no semestre 2026/2 e inclui:

- requisitos funcionais e não funcionais;
- modelo conceitual e DER;
- entidades e relacionamentos;
- protótipos de interface;
- definição inicial do banco de dados e DDL.

Esses artefatos representam a base anterior do projeto e não devem ser confundidos com as atividades de modelagem e implementação realizadas na Entrega 1 de 2026/2.

## Incremento 2026/2

O trabalho desenvolvido para a Entrega 1 concentra-se na revisão e integração dos conteúdos das disciplinas atuais.

O incremento inclui:

- organização do repositório documental e do fluxo de contribuição;
- revisão da modelagem;
- modelagem algorítmica;
- decomposição da unidade funcional de devolução em funções/procedimentos;
- modelagem matemática do cálculo dos dias de atraso;
- casos de teste e validação;
- documentação da integração entre as disciplinas.

## Arquitetura dos repositórios

O repositório `PI-Biblioteca/biblioteca` é dedicado à documentação, modelagem e evidências acadêmicas.

A implementação será separada em:

- **backend:** repositório próprio, derivado de um fork adaptado de `JoaoPauloOlt/library-api`;
- **frontend:** repositório próprio, separado do backend.

Os links definitivos dos repositórios de implementação serão adicionados quando forem criados.

## Histórico do repositório

A organização do repositório permite distinguir a evolução do projeto por meio do histórico de commits e Pull Requests.

A Entrega 1 foi organizada em `entrega 1/`, com espaços para apresentação, trabalho escrito e anexos. A documentação de algoritmos também foi separada em arquivos específicos para facilitar manutenção e contribuição.

## Estrutura documental

- `docs/` — requisitos, modelagem, algoritmos, matemática e integração.
- `entrega 1/` — apresentação, trabalho escrito e anexos.
- `CONTRIBUTING.md` — fluxo de contribuição e revisão.


## Implementação executável — Entrega 2

A implementação foi consolidada nos repositórios:

- Backend: [JoaoPauloOlt/library-api](https://github.com/JoaoPauloOlt/library-api)
- Frontend: [JoaoPauloOlt/library-web](https://github.com/JoaoPauloOlt/library-web)

O backend implementa autenticação JWT, autorização por permissões (RBAC), catálogo, exemplares físicos e circulação. O frontend consome os contratos REST do backend e apresenta catálogo, empréstimos, histórico e relatórios. O módulo de multas foi implementado no backend; a integração de consulta e isenção administrativa no frontend está em validação.

### Fluxo funcional a demonstrar

1. Usuário autenticado consulta o catálogo e solicita um exemplar disponível.
2. Funcionário localiza o usuário ativo e registra empréstimo em seu nome, quando aplicável.
3. Funcionário aprova a solicitação; o exemplar passa a `LOANED` e o empréstimo a `ACTIVE`.
4. O empréstimo vencido passa a `LATE` pelo processamento automático.
5. Funcionário registra a devolução; o empréstimo passa a `RETURNED` e o exemplar retorna a `AVAILABLE`.
6. Se a devolução ocorrer após o vencimento, a API calcula e persiste a multa na mesma transação da devolução.
7. Usuário consulta as próprias multas; funcionários consultam multas globais; administrador pode isentar multa em aberto com justificativa.

### Regras de multa implementadas

- R$ 2,00 por dia corrido de atraso;
- sem tolerância e sem limite máximo;
- datas de negócio calculadas no fuso `America/Sao_Paulo`;
- devolução no vencimento ou antes dele não gera multa;
- pagamento não faz parte do escopo desta versão.

### Reprodutibilidade

Consulte os READMEs dos repositórios executáveis para os requisitos completos e variáveis de ambiente.

Backend:
- `docker compose up --build` inicia PostgreSQL, RabbitMQ e API no perfil de desenvolvimento;
- `./mvnw verify` executa os testes e a verificação de cobertura;
- os testes de integração utilizam PostgreSQL e bancos isolados.

Frontend:
- `npm ci` instala as dependências;
- `npm test`, `npm run lint` e `npm run build` validam a aplicação;
- `VITE_API_URL` configura a URL da API.

### Evidências exigidas para a apresentação

Registrar evidências reais após executar a versão integrada:

- login com os perfis USER, LIBRARIAN e ADMIN;
- solicitação, aprovação e devolução de empréstimo;
- transição de empréstimo para atrasado;
- exemplar indisponível durante o empréstimo e disponível após a devolução;
- multa calculada e persistida após devolução atrasada;
- consulta de multas conforme as permissões;
- isenção administrativa com justificativa;
- execução bem-sucedida do CI e dos testes de integração;
- execução reproduzível a partir de um banco limpo.

**Atenção:** os itens acima são roteiro de validação. Só devem ser marcados como comprovados depois da execução e captura das respectivas evidências. Consulte também [Validação da Aplicação](./validacao-aplicacao.md).
