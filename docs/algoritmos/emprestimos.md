# Algoritmos de Empréstimo

## 1. Registro de Empréstimo

**Responsável inicial:** Khaled Fatah

### Entrada
- CPF do usuário
- ISBN do livro
- Data do empréstimo

### Processamento
1. Localizar usuário e livro.
2. Verificar existência de ambos.
3. Verificar disponibilidade do livro.
4. Registrar o empréstimo.

### Saída
- Empréstimo registrado; ou
- mensagem indicando o motivo da rejeição.

### Pseudocódigo
```text
INÍCIO
    receber CPF
    receber ISBN
    receber data_emprestimo

    usuário ← buscar usuário pelo CPF
    livro ← buscar livro pelo ISBN

    SE usuário não existir ENTÃO
        exibir "Usuário não encontrado"
        encerrar
    FIM_SE

    SE livro não existir ENTÃO
        exibir "Livro não encontrado"
        encerrar
    FIM_SE

    SE livro possuir empréstimo ativo ENTÃO
        exibir "Livro indisponível"
        encerrar
    FIM_SE

    criar empréstimo
    registrar data do empréstimo
    associar usuário e livro

    exibir "Empréstimo registrado com sucesso"
FIM
```

## 2. Registro de Devolução

**Responsável inicial:** Khaled Fatah

### Entrada
- Identificador do empréstimo
- Data da devolução

### Processamento
1. Localizar o empréstimo.
2. Verificar se existe e está ativo.
3. Comparar a data de devolução com a data prevista.
4. Identificar se houve atraso.
5. Calcular a multa quando houver atraso.
6. Registrar a data da devolução e finalizar o empréstimo.
7. Retornar o resultado da operação.

### Saída
- Devolução registrada com a quantidade de dias de atraso e multa; ou
- mensagem de erro.

### Pseudocódigo
```text
INÍCIO
    receber id_emprestimo
    receber data_devolucao

    empréstimo ← buscar empréstimo pelo ID

    SE empréstimo não existir ENTÃO
        exibir "Empréstimo não encontrado"
        encerrar
    FIM_SE

    SE empréstimo já possuir data de devolução ENTÃO
        exibir "Empréstimo já finalizado"
        encerrar
    FIM_SE

    dias_atraso ← calcular diferença entre data_devolucao e data_prevista

    SE dias_atraso > 0 ENTÃO
        multa ← calcularMulta(dias_atraso)
    SENÃO
        dias_atraso ← 0
        multa ← 0
    FIM_SE

    registrar data_devolucao
    registrar dias_atraso
    registrar multa
    atualizar empréstimo

    exibir "Devolução registrada com sucesso"
    exibir dias_atraso
    exibir multa
FIM
```

### Modularização

A devolução utiliza funções de apoio para separar responsabilidades:

- `buscarEmprestimo(id)` — localiza o empréstimo.
- `calcularDiasAtraso(data_devolucao, data_prevista)` — determina o atraso.
- `calcularMulta(dias_atraso)` — calcula a multa quando houver atraso.
- `registrarDevolucao(id, data)` — finaliza o empréstimo.

O valor da multa e a fórmula matemática utilizada são definidos na documentação de [Matemática](../matematica/README.md), mantendo a modelagem algorítmica separada da modelagem matemática.

**Estruturas:** sequência, seleção e modularização por busca, cálculo e atualização do empréstimo.
