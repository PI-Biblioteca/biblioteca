# Modelagem de Algoritmos

Documento índice da modelagem algorítmica do Projeto Integrado 2026/2.

A modelagem utiliza uma unidade funcional de devolução e apresenta decomposição em funções/procedimentos, além de sequência, seleção e operações de processamento.

## Documentos

- [Algoritmos de Cadastro](./cadastros.md)
- [Usuário e Disponibilidade](./usuarios-disponibilidade.md)
- [Empréstimos](./emprestimos.md)
- [Histórico de Empréstimos](./historico.md)
- [Modularização e Fluxo](./apoio-e-fluxo.md)

## Unidade funcional principal

`processarDevolucao()` coordena a operação de devolução e delega responsabilidades para:

1. `localizarEmprestimo(idEmprestimo)`;
2. `validarDevolucao(emprestimo)`;
3. `calcularAtraso(dataPrevista, dataDevolucao)`;
4. `registrarDevolucao(emprestimo, dataDevolucao)`;
5. `atualizarDisponibilidade(exemplar)`.

Essa decomposição será utilizada como referência para a futura implementação do backend.

## Escopo

A modelagem contempla cadastro, usuários, disponibilidade, empréstimos, devoluções e histórico. O cálculo quantitativo dos dias de atraso é tratado na documentação de Matemática.
