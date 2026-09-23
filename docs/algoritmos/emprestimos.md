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
3. Registrar a data da devolução.
4. Atualizar o empréstimo.

### Saída
- Devolução registrada; ou
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

    registrar data_devolucao
    atualizar empréstimo

    exibir "Devolução registrada com sucesso"
FIM
```

**Estruturas:** sequência, seleção e modularização por busca e atualização do empréstimo.
