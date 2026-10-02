# Modelagem Matemática da Multa por Atraso

## Objetivo

Definir o modelo matemático utilizado pelo Sistema Biblioteca para determinar a quantidade de dias de atraso e o valor da multa na devolução de um livro.

## Variáveis

| Variável | Definição | Unidade |
|---|---|---|
| **D** | Data prevista para a devolução do livro | Data |
| **R** | Data efetiva da devolução do livro | Data |
| **A** | Quantidade de dias de atraso | Dias |
| **V** | Valor da multa por dia de atraso | Reais/dia |
| **M** | Valor total da multa | Reais |

Nesta entrega, considera-se inicialmente **V = R$ 1,00 por dia de atraso**.

## Cálculo dos dias de atraso

A quantidade de dias de atraso é determinada pela diferença entre a data efetiva de devolução e a data prevista:

$$
A = max(0, R - D)
$$

A função max garante que o resultado mínimo seja zero.

Portanto:

- Se R < D, a devolução ocorreu antes do prazo e **A = 0**.
- Se R = D, a devolução ocorreu no prazo e **A = 0**.
- Se R > D, houve atraso e **A = R - D**.

Essa regra evita que uma devolução antecipada produza uma quantidade negativa de dias de atraso.

## Cálculo da multa

A multa é proporcional à quantidade de dias de atraso:

$$
M =
\begin{cases}
A \times V, & \text{se } A > 0 \\
0, & \text{se } A = 0
\end{cases}
$$

Como o valor inicial definido para a taxa diária é **V = R$ 1,00**, temos:

$$
M =
\begin{cases}
A \times 1{,}00, & \text{se houver atraso} \\
0, & \text{caso contrário}
\end{cases}
$$

Assim, para atrasos positivos, cada dia adicional acrescenta **R$ 1,00** ao valor da multa.

## Exemplos

| Data prevista (D) | Data efetiva (R) | Atraso (A) | Valor diário (V) | Multa (M) |
|---|---|---:|---:|---:|
| 10/10 | 10/10 | 0 dias | R$ 1,00 | R$ 0,00 |
| 10/10 | 08/10 | 0 dias | R$ 1,00 | R$ 0,00 |
| 10/10 | 13/10 | 3 dias | R$ 1,00 | R$ 3,00 |
| 10/10 | 20/10 | 10 dias | R$ 1,00 | R$ 10,00 |

## Relação com a unidade funcional de devolução

O modelo matemático é aplicado durante o processamento da devolução:

1. O sistema identifica a **data prevista (D)**.
2. Recebe a **data efetiva (R)**.
3. Calcula os **dias de atraso (A)**.
4. Determina a **multa (M)** utilizando o valor diário **V**.
5. Registra e apresenta o resultado da devolução.

A modelagem matemática fornece a regra quantitativa utilizada pelo algoritmo de devolução e serve como referência para os casos de teste documentados em [Casos de Teste do Cálculo Matemático](./casos-de-teste.md).

## Critérios de validação

O modelo deve produzir os seguintes comportamentos:

- devolução antecipada → **0 dias de atraso e R$ 0,00**;
- devolução no prazo → **0 dias de atraso e R$ 0,00**;
- devolução com atraso → multa proporcional aos dias de atraso;
- cada dia de atraso → **R$ 1,00** de multa na configuração inicial.

O modelo é parametrizado pela variável **V**, permitindo alterar futuramente o valor diário sem modificar a definição da quantidade de dias de atraso.
