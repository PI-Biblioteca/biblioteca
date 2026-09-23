# Algoritmo de Histórico de Empréstimos

**Responsável inicial:** Khaled Fatah

### Entrada
- CPF do usuário, para consulta específica; ou
- solicitação de histórico geral.

### Processamento
1. Receber o identificador da consulta.
2. Localizar os empréstimos correspondentes.
3. Verificar se existem registros.
4. Percorrer os empréstimos encontrados.
5. Apresentar os dados.

### Saída
- Lista dos empréstimos encontrados; ou
- mensagem informando que não existem registros.

### Pseudocódigo
```text
INÍCIO
    receber CPF ou solicitação de histórico geral

    listaEmprestimos ← buscar empréstimos correspondentes

    SE listaEmprestimos estiver vazia ENTÃO
        exibir "Nenhum empréstimo encontrado"
        encerrar
    FIM_SE

    PARA cada empréstimo da lista FAÇA
        exibir livro
        exibir usuário
        exibir data do empréstimo
        exibir data da devolução
    FIM_PARA
FIM
```

**Estruturas:** sequência, seleção, repetição e modularização pela consulta dos empréstimos.
