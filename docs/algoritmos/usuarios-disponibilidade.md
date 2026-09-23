# Algoritmos de Usuário e Disponibilidade

## 1. Cadastro de Usuário

**Responsável inicial:** Caique Assis

### Entrada
- CPF
- Nome
- E-mail

### Processamento
1. Receber os dados.
2. Validar os campos obrigatórios.
3. Verificar CPF e e-mail já cadastrados.
4. Registrar o usuário.

### Saída
- Usuário cadastrado; ou
- mensagem de rejeição.

### Pseudocódigo
```text
INÍCIO
    receber CPF
    receber nome
    receber email

    SE algum campo obrigatório estiver vazio ENTÃO
        exibir "Preencha todos os campos obrigatórios"
        encerrar
    FIM_SE

    SE CPF já estiver cadastrado ENTÃO
        exibir "Usuário já cadastrado"
        encerrar
    FIM_SE

    SE email já estiver cadastrado ENTÃO
        exibir "E-mail já cadastrado"
        encerrar
    FIM_SE

    cadastrar usuário
    exibir "Usuário cadastrado com sucesso"
FIM
```

## 2. Consulta de Livros Disponíveis

**Responsável inicial:** Caique Assis

### Entrada
- Lista de livros
- Registros de empréstimos

### Processamento
1. Percorrer os livros cadastrados.
2. Verificar se cada livro possui empréstimo ativo.
3. Adicionar à lista de disponíveis quando não houver empréstimo ativo.

### Saída
- Lista de livros disponíveis.

### Pseudocódigo
```text
INÍCIO
    listaDisponiveis ← vazia

    PARA cada livro cadastrado FAÇA
        verificar se existe empréstimo ativo

        SE não existir empréstimo ativo ENTÃO
            adicionar livro à listaDisponiveis
        FIM_SE
    FIM_PARA

    exibir listaDisponiveis
FIM
```

**Estruturas:** sequência, seleção, repetição e modularização pela verificação de disponibilidade.
