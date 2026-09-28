# Modelagem

DER, entidades, relacionamentos e regras de negócio.

## DER - DIAGRAMA DE ENTIDADES E RELACIONAMENTOS

<img width="669" height="401" alt="Image" src="https://github.com/user-attachments/assets/8bf67322-ecc4-4d98-9c2f-256c55048e35" />

## TABELA DE ENTIDADES

| Entidade | Descrição |
|---|---|
| LIVRO | isbn, título, gênero, id autor |
| AUTOR | id autor, nome, nacionalidade |
| USUARIO | cpf, nome, email, telefone |
| EMPRESTIMO | id empréstimo, data empréstimo, data devolução, isbn, cpf |

## Relacionamentos

| Entidade A | Verbo/Ação | Entidade B | Cardinalidade |
|---|---|---|---|
| USUARIO | realiza | EMPRESTIMO | 1:N |
| EMPRESTIMO | refere-se | LIVRO | N:1 |
| LIVRO | possui | AUTOR | N:1 |

## REGRAS DE NEGÓCIO 

### RN01 — Empréstimos por usuário
Um usuário pode realizar vários empréstimos.

### RN02 — Usuário do empréstimo
Cada empréstimo deve estar associado a um único usuário.

### RN03 — Livro do empréstimo
Cada empréstimo deve estar associado a um único livro.

### RN04 — Empréstimos do livro
Um livro pode participar de vários empréstimos ao longo do tempo.

### RN05 — Autor dos livros
Um autor pode possuir vários livros cadastrados no sistema.

### RN06 — Autor do livro
Cada livro deve estar associado a um único autor.

### RN07 — Devolução
Para realizar uma devolução, o empréstimo correspondente deve existir no sistema.

### RN08 — Verificação de atraso
Ao registrar uma devolução, o sistema deve verificar se houve atraso.

### RN09 — Registro da devolução
Após a devolução, o sistema deve registrar a data correspondente no empréstimo.

### RN10 — Resultado da devolução
O sistema deve informar se a devolução ocorreu dentro do prazo ou se houve atraso, indicando a quantidade de dias de atraso quando aplicável.

# Unidade Funcional — Processamento de Devolução com Verificação de Atraso

## 1. Objetivo

Documentar a unidade funcional escolhida para a Entrega 1: **processamento de devolução com verificação de atraso**.

Essa unidade funcional tem como objetivo registrar a devolução de um livro emprestado, localizar o empréstimo correspondente, verificar se houve atraso e apresentar o resultado do processamento.

---

## 2. Escopo

A unidade funcional contempla:

- Localização do empréstimo;
- Validação do empréstimo;
- Cálculo dos dias de atraso;
- Registro da devolução;
- Apresentação do resultado ao usuário.

---

## 3. Entradas

| Entrada | Descrição |
|---|---|
| `id_emprestimo` | Identificador do empréstimo que será devolvido |
| `data_devolucao` | Data em que o livro está sendo devolvido |

---

## 4. Processamento

### 4.1 Localização do empréstimo

O sistema utiliza o `id_emprestimo` informado para localizar o registro correspondente na entidade **EMPRESTIMO**.

O empréstimo deve existir no sistema para que a devolução possa ser processada.

### 4.2 Validação do empréstimo

Após localizar o empréstimo, o sistema verifica se ele pode ser devolvido.

As seguintes validações são realizadas:

- O `id_emprestimo` deve existir;
- O empréstimo deve estar registrado no sistema;
- O empréstimo não pode possuir uma devolução já registrada.

Caso alguma validação não seja atendida, a devolução não é registrada e o sistema apresenta uma mensagem informando o problema.

### 4.3 Cálculo dos dias de atraso

Após validar o empréstimo, o sistema compara a data prevista para devolução com a data em que o livro foi efetivamente devolvido.

O cálculo é realizado da seguinte forma:

```text
dias de atraso = data de devolução - data prevista de devolução

quando resultado for:
- **Menor ou igual a 0:** não houve atraso.
- **Maior que 0:** houve atraso e o resultado representa a quantidade de dias de atraso.
```
### 4.4 Registro da devolução

Após o processamento, o sistema registra a data efetiva da devolução no empréstimo correspondente.

Dessa forma, o histórico do empréstimo passa a indicar que o livro foi devolvido.

### 4.5 Resultado apresentado

Em caso de devolução sem atraso:

> Devolução registrada com sucesso.  
> Não houve atraso.

Em caso de devolução com atraso:

> Devolução registrada com sucesso.  
> Atraso de X dias.

Caso o empréstimo não seja encontrado ou não possa ser devolvido:

> Não foi possível processar a devolução.

---

## 5. Saídas

| Saída | Descrição |
|---|---|
| Confirmação da devolução | Informa que a devolução foi registrada |
| Situação do atraso | Informa se houve ou não atraso |
| Quantidade de dias de atraso | Apresentada quando a devolução ocorre após a data prevista |
| Mensagem de erro | Apresentada quando o empréstimo não é encontrado ou não pode ser devolvido |

---

## 6. Fluxo da Unidade Funcional

1. Informar o ID do empréstimo.
2. Localizar o empréstimo no sistema.
3. Verificar se o empréstimo existe.
4. Verificar se o empréstimo já foi devolvido.
5. Informar a data da devolução.
6. Calcular os dias de atraso.
7. Registrar a devolução.
8. Apresentar o resultado da operação.

### Fluxo resumido

```text
Início
   ↓
Informar ID do empréstimo
   ↓
Localizar empréstimo
   ↓
Empréstimo existe?
   ├── Não → Exibir erro → Fim
   │
   └── Sim
         ↓
   Empréstimo já foi devolvido?
         ├── Sim → Exibir erro → Fim
         │
         └── Não
               ↓
       Informar data da devolução
               ↓
       Calcular dias de atraso
               ↓
       Registrar devolução
               ↓
       Exibir resultado
               ↓
              Fim
