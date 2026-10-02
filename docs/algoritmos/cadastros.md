# Algoritmos de Cadastro

## 1. Cadastro de Autor

**Responsável inicial:** João Paulo

### Entrada
- Nome do autor
- Nacionalidade

### Processamento
1. Receber os dados.
2. Validar os campos obrigatórios.
3. Verificar se o autor já existe.
4. Criar e armazenar o registro.

### Saída
- Autor cadastrado; ou
- mensagem de erro.

### Pseudocódigo
```text
INÍCIO
    receber nome
    receber nacionalidade

    SE algum campo obrigatório estiver vazio ENTÃO
        exibir "Preencha todos os campos obrigatórios"
        encerrar
    FIM_SE

    SE autor já estiver cadastrado ENTÃO
        exibir "Autor já cadastrado"
        encerrar
    FIM_SE

    cadastrar autor
    exibir "Autor cadastrado com sucesso"
FIM
```

## 2. Cadastro de Livro

**Responsável inicial:** João Paulo

### Entrada
- ISBN
- Título
- Gênero
- Autor

### Processamento
1. Receber os dados.
2. Validar os campos obrigatórios.
3. Verificar se o ISBN já está cadastrado.
4. Verificar se o autor existe.
5. Cadastrar o livro.

### Saída
- Livro cadastrado; ou
- mensagem de erro.

### Pseudocódigo
```text
INÍCIO
    receber ISBN
    receber título
    receber gênero
    receber id_autor

    SE algum campo obrigatório estiver vazio ENTÃO
        exibir "Dados obrigatórios não preenchidos"
        encerrar
    FIM_SE

    SE ISBN já estiver cadastrado ENTÃO
        exibir "Livro já cadastrado"
        encerrar
    FIM_SE

    SE autor não existir ENTÃO
        exibir "Autor não encontrado"
        encerrar
    FIM_SE

    cadastrar livro
    exibir "Livro cadastrado com sucesso"
FIM
```

**Estruturas:** sequência, seleção e modularização por validações e operações de cadastro.
