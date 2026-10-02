# Matriz de Integração das Disciplinas — Sistema Biblioteca

## Objetivo

Documentar a matriz de integração entre **Linguagem de Programação**, **Algoritmos e Programação Estruturada** e **Matemática Computacional**, relacionando os conteúdos acadêmicos do semestre com sua aplicação prática na funcionalidade de **Devolução de Livros** do Sistema Biblioteca.

## Escopo

Relacionar, para cada disciplina: os conceitos aplicados, a aplicação na unidade funcional de devolução e as evidências previstas para a Entrega 1.

## Matriz de Integração

| Disciplina / Área | Conceitos Aplicados | Aplicação na Unidade Funcional de Devolução | Evidências Previstas (Entrega 1) |
|---|---|---|---|
| **Linguagem de Programação** | Estruturas condicionais (if/else), métodos, funções e manipulação de objetos e datas. | Implementação da lógica de devolução na API (library-api), recebendo as datas do empréstimo e processando os dados. | Código-fonte e documentação de chamadas aos endpoints (Swagger/Postman) — previstos para as próximas entregas. |
| **Algoritmos e Programação Estruturada** | Pseudocódigo, fluxogramas, variáveis de entrada, sequência lógica, tomada de decisão e saída. | Mapeamento do fluxo lógico de devolução: recebimento da data efetiva R, comparação com o prazo D e definição do status. | Pseudocódigo e Fluxograma no trabalho escrito e nos Anexos 03 e 04. |
| **Matemática Computacional** | Funções matemáticas, variáveis discretas e cálculo de limite inferior via função `max`. | Aplicação da fórmula `A = max(0, R − D)`, em que R e D representam datas e a diferença (R − D) é calculada em dias, para determinar a quantidade A de dias em atraso sem gerar valores negativos. | Formulação matemática no trabalho escrito, Anexo 05 e Tabela de Casos de Teste (Anexo 06). |

## Complemento (fora do escopo original da Issue #8)

A regra de devolução também depende da tabela `emprestimo` (id_emprestimo, ISBN, CPF, data_emprestimo, data_devolucao) e da integridade referencial garantida pelas chaves estrangeiras ISBN → `livro` e CPF → `usuario`. Esse ponto de **Banco de Dados / Modelagem de Dados** é relevante para o projeto, mas ainda não possui um script DDL disponível na branch `develop` — a evidência correspondente será adicionada quando o script existir no repositório.

## Critérios de Conclusão

- [x] Conceitos de cada disciplina identificados.
- [x] Aplicação na unidade funcional documentada.
- [x] Evidências previstas alinhadas à Entrega 1.
