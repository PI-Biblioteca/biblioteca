# Modelagem de Algoritmos — Sistema de Gestão de Biblioteca

> Documento referente à modelagem algorítmica da versão inicial do Projeto Integrado 2026/2.
>
> Baseado nos requisitos e na modelagem apresentados no documento do projeto da Biblioteca e nas exigências da Entrega 1 para **Algoritmos e Programação Estruturada**.

## 1. Objetivo

Este documento define os principais algoritmos necessários para a primeira versão funcional do Sistema de Gestão de Biblioteca.

A modelagem considera as funcionalidades previstas no projeto:

- cadastro de livros;
- cadastro de autores;
- cadastro de usuários;
- registro de empréstimos;
- registro de devoluções;
- consulta de livros disponíveis;
- consulta do histórico de empréstimos.

A modelagem algorítmica apresenta **entradas, processamento, saídas, decisões, repetições e modularização**, utilizando pseudocódigo para representar o fluxo das operações.

A organização dos algoritmos também permite que os integrantes tenham participação direta na implementação inicial.

---

## 2. Organização da contribuição da equipe

| Integrante | Contribuição algorítmica inicial |
|---|---|
| **João Paulo** | Cadastro e validação de livros/autores |
| **Caique Assis** | Cadastro e validação de usuários + consulta de disponibilidade |
| **Khaled Fatah** | Empréstimo, devolução e histórico de empréstimos |

> A divisão acima representa a contribuição inicial de cada integrante. Os algoritmos serão posteriormente integrados no sistema, portanto não representam módulos completamente isolados.

---

# 3. Algoritmos de Cadastro

## 3.1 Cadastro de Autor

**Responsável inicial:** João Paulo

### Entrada

- Nome do autor;
- Nacionalidade.

### Processamento

1. Receber os dados informados.
2. Verificar se os campos obrigatórios foram preenchidos.
3. Verificar se o autor já existe, quando aplicável.
4. Criar o registro do autor.
5. Armazenar o registro.

### Saída

- Autor cadastrado com sucesso; ou
- mensagem informando que os dados são inválidos ou que o cadastro não pode ser realizado.

### Pseudocódigo

```text
INÍCIO

    receber nome
    receber nacionalidade

    SE nome estiver vazio OU nacionalidade estiver vazia ENTÃO
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

**Estruturas utilizadas:**

- Sequência: recebimento e processamento dos dados.
- Seleção: validação dos campos e verificação de duplicidade.

---

## 3.2 Cadastro de Livro

**Responsável inicial:** João Paulo

### Entrada

- ISBN;
- título;
- gênero;
- autor.

### Processamento

1. Receber os dados do livro.
2. Validar os campos obrigatórios.
3. Verificar se o ISBN já está cadastrado.
4. Verificar se o autor informado existe.
5. Cadastrar o livro.

### Saída

- Livro cadastrado; ou
- mensagem de erro indicando o problema encontrado.

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

**Estruturas utilizadas:**

- Sequência;
- seleção;
- modularização por meio de validações e operação de cadastro.

---

# 4. Algoritmos de Usuário e Disponibilidade

## 4.1 Cadastro de Usuário

**Responsável inicial:** Caique Assis

### Entrada

- CPF;
- nome;
- e-mail.

### Processamento

1. Receber os dados.
2. Validar os campos obrigatórios.
3. Verificar se o CPF já está cadastrado.
4. Verificar se o e-mail já está cadastrado.
5. Registrar o usuário.

### Saída

- Usuário cadastrado com sucesso; ou
- mensagem informando o motivo da rejeição.

### Pseudocódigo

```text
INÍCIO

    receber CPF
    receber nome
    receber email

    SE CPF estiver vazio OU nome estiver vazio OU email estiver vazio ENTÃO
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

**Estruturas utilizadas:**

- Sequência;
- seleção;
- modularização das validações.

---

## 4.2 Consulta de Livros Disponíveis

**Responsável inicial:** Caique Assis

O algoritmo identifica os livros que não possuem empréstimo ativo.

### Entrada

- Lista de livros;
- registros de empréstimos.

### Processamento

1. Percorrer os livros cadastrados.
2. Verificar se cada livro possui empréstimo ativo.
3. Se não possuir, adicionar o livro à lista de disponíveis.
4. Continuar até verificar todos os livros.

### Saída

- Lista de livros disponíveis.

### Pseudocódigo

```text
INÍCIO

    listaDisponiveis ← vazia

    PARA cada livro cadastrado FAÇA

        verificar se existe empréstimo ativo para o livro

        SE não existir empréstimo ativo ENTÃO
            adicionar livro à listaDisponiveis
        FIM_SE

    FIM_PARA

    exibir listaDisponiveis

FIM
```

**Estruturas utilizadas:**

- Repetição: percorre todos os livros.
- Seleção: verifica a situação de cada livro.
- Modularização: a verificação de disponibilidade pode ser implementada como uma função própria.

---

# 5. Algoritmos de Empréstimo

## 5.1 Registro de Empréstimo

**Responsável inicial:** Khaled Fatah

### Entrada

- CPF do usuário;
- ISBN do livro;
- data do empréstimo.

### Processamento

1. Localizar o usuário.
2. Localizar o livro.
3. Verificar se o usuário existe.
4. Verificar se o livro existe.
5. Verificar se o livro está disponível.
6. Registrar o empréstimo.
7. Informar o resultado.

### Saída

- Empréstimo registrado; ou
- mensagem indicando por que o empréstimo não pode ser realizado.

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
    associar usuário ao empréstimo
    associar livro ao empréstimo

    exibir "Empréstimo registrado com sucesso"

FIM
```

**Estruturas utilizadas:**

- Sequência;
- seleção;
- modularização através das operações de busca e verificação de disponibilidade.

---

## 5.2 Registro de Devolução

**Responsável inicial:** Khaled Fatah

### Entrada

- Identificador do empréstimo;
- data da devolução.

### Processamento

1. Localizar o empréstimo.
2. Verificar se o empréstimo existe.
3. Verificar se ainda está ativo.
4. Registrar a data da devolução.
5. Atualizar a situação do empréstimo.

### Saída

- Devolução registrada com sucesso; ou
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

**Estruturas utilizadas:**

- Sequência;
- seleção;
- modularização pela busca e atualização do empréstimo.

---

# 6. Algoritmo de Histórico de Empréstimos

## 6.1 Consulta do Histórico

**Responsável inicial:** Khaled Fatah

O histórico deve permitir consultar os empréstimos registrados, incluindo aqueles já devolvidos.

### Entrada

- CPF do usuário, quando a consulta for específica;
- ou solicitação de histórico geral.

### Processamento

1. Receber o identificador da consulta.
2. Localizar os empréstimos correspondentes.
3. Percorrer os registros encontrados.
4. Apresentar os dados de cada empréstimo.
5. Informar quando não houver registros.

### Saída

- Lista dos empréstimos encontrados.

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
        exibir identificação do livro
        exibir identificação do usuário
        exibir data do empréstimo
        exibir data da devolução
    FIM_PARA

FIM
```

**Estruturas utilizadas:**

- Sequência;
- seleção;
- repetição para percorrer os registros;
- modularização pela consulta dos empréstimos.

---

# 7. Funções e Procedimentos de Apoio

Para evitar repetição de código, os algoritmos principais podem ser decompostos em funções ou procedimentos menores.

Exemplos:

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

Essa decomposição atende ao princípio de **modularização**, permitindo que cada operação tenha uma responsabilidade específica e possa ser utilizada por diferentes partes do sistema.

---

# 8. Fluxo Geral da Biblioteca

A integração dos algoritmos pode ser representada pelo seguinte fluxo:

```text
                 INÍCIO
                    |
                    v
             Escolher operação
                    |
        +-----------+-----------+
        |           |           |
        v           v           v
     Cadastro    Consulta    Empréstimo
        |           |           |
        |           |      Verificar usuário
        |           |           |
        |           |      Verificar livro
        |           |           |
        |           |      Verificar disponibilidade
        |           |           |
        |           |      Registrar empréstimo
        |           |           |
        +-----------+-----------+
                    |
                    v
              Devolução
                    |
                    v
          Atualizar empréstimo
                    |
                    v
               Histórico
                    |
                    v
                   FIM
```

---

# 9. Estruturas de Programação Evidenciadas

| Conceito | Aplicação na Biblioteca |
|---|---|
| **Sequência** | Receber dados → validar → processar → retornar resultado |
| **Seleção** | Verificar existência, disponibilidade e validade dos dados |
| **Repetição** | Percorrer livros e registros de empréstimos |
| **Modularização** | Separar buscas, validações, consultas e operações de empréstimo |
| **Entrada** | Dados de livros, autores, usuários e empréstimos |
| **Processamento** | Validações, buscas, verificações e registros |
| **Saída** | Mensagens, confirmações e listas de dados |

---

# 10. Relação com os Requisitos Funcionais

| Requisito | Algoritmo relacionado |
|---|---|
| **RF01 — Cadastro de livros** | Cadastro de Livro |
| **RF02 — Cadastro de autores** | Cadastro de Autor |
| **RF03 — Cadastro de usuários** | Cadastro de Usuário |
| **RF04 — Registrar empréstimos** | Registro de Empréstimo |
| **RF05 — Registrar devolução** | Registro de Devolução |
| **RF06 — Consultar livros disponíveis** | Consulta de Livros Disponíveis |
| **RF07 — Listar histórico de empréstimos** | Consulta do Histórico |

---

## 11. Escopo da primeira versão

Os algoritmos deste documento estão limitados às funcionalidades definidas para a primeira versão do projeto.

**Não fazem parte dos algoritmos iniciais:**

- cálculo de multas;
- relatórios avançados;
- autenticação e autorização avançadas;
- notificações;
- recomendações de livros;
- outras funcionalidades futuras.

Essas funcionalidades poderão ser adicionadas posteriormente caso façam parte do escopo de uma próxima etapa.

## 12. Critérios para implementação

Cada algoritmo deverá ser convertido em uma unidade funcional do sistema, mantendo a separação entre:

```text
Entrada
   ↓
Validação
   ↓
Processamento
   ↓
Persistência/Consulta
   ↓
Saída
```

A implementação deve preservar a lógica apresentada neste documento, permitindo que os algoritmos sejam posteriormente relacionados ao código-fonte, testes e evidências da Entrega 1.
