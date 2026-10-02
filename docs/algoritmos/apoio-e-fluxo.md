# Modularização e Fluxo dos Algoritmos

## Funções e procedimentos de apoio

Para evitar repetição de código, os algoritmos podem utilizar funções ou procedimentos menores:

```text
buscarAutor(id)
buscarLivro(isbn)
buscarUsuario(cpf)
buscarEmprestimo(id)
verificarDisponibilidade(isbn)
validarDadosLivro(dados)
validarDadosUsuario(dados)
registrarEmprestimo(dados)
registrarDevolucao(id, data)
listarHistorico(cpf)
```

Essa decomposição representa a **modularização**, permitindo separar buscas, validações, consultas e operações de empréstimo.

## Fluxo geral

```text
INÍCIO
   |
   v
Escolher operação
   |
   +--> Cadastro
   |
   +--> Consulta de disponibilidade
   |
   +--> Empréstimo
   |       |
   |       +--> verificar usuário
   |       +--> verificar livro
   |       +--> verificar disponibilidade
   |       +--> registrar empréstimo
   |
   +--> Devolução
   |       |
   |       +--> localizar empréstimo
   |       +--> atualizar empréstimo
   |
   +--> Histórico
           |
           +--> consultar registros
           +--> exibir resultados
   |
   v
 FIM
```

## Estruturas de programação

| Conceito | Aplicação |
|---|---|
| Sequência | Receber → validar → processar → retornar |
| Seleção | Verificar existência, disponibilidade e validade |
| Repetição | Percorrer livros e registros |
| Modularização | Separar buscas, validações e operações |
| Entrada | Dados de livros, autores, usuários e empréstimos |
| Processamento | Validações, buscas e registros |
| Saída | Mensagens, confirmações e listas |

## Relação com os requisitos funcionais

| Requisito | Algoritmo |
|---|---|
| RF01 — Cadastro de livros | Cadastro de Livro |
| RF02 — Cadastro de autores | Cadastro de Autor |
| RF03 — Cadastro de usuários | Cadastro de Usuário |
| RF04 — Registrar empréstimos | Registro de Empréstimo |
| RF05 — Registrar devolução | Registro de Devolução |
| RF06 — Consultar livros disponíveis | Consulta de Livros Disponíveis |
| RF07 — Listar histórico de empréstimos | Consulta do Histórico |
