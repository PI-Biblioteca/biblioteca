# Casos de Teste do Cálculo Matemático

## Objetivo

Documentar os casos de teste utilizados para validar o cálculo dos dias de atraso e da multa associada à devolução de livros.

## Modelo matemático

\[
A = \max(0, R - D)
\]

Onde:

- **A** = quantidade de dias de atraso;
- **R** = data efetiva de devolução;
- **D** = data prevista para devolução.

Considerando a regra definida para esta entrega, a multa é calculada por:

\[
M = A \times 1{,}00
\]

Onde **M** representa a multa em reais e a taxa aplicada é de **R$ 1,00 por dia de atraso**.

A função `max(0, R - D)` impede que uma devolução antecipada ou realizada no prazo produza quantidade negativa de dias de atraso.

## Casos de teste

| ID | Condição | Cálculo | Resultado esperado | Relação com a fórmula |
|---|---|---|---|---|
| T01 | Devolução no dia previsto (0 dias de atraso) | `A = max(0, 0) = 0` e `M = 0 × 1,00` | **0 dias de atraso; R$ 0,00** | Valida o limite inferior `max(0, ...)`. |
| T02 | Devolução com 3 dias de atraso | `A = max(0, 3) = 3` e `M = 3 × 1,00` | **3 dias de atraso; R$ 3,00** | Valida o cálculo positivo de atraso e a taxa de R$ 1,00/dia. |
| T03 | Devolução com 10 dias de atraso | `A = max(0, 10) = 10` e `M = 10 × 1,00` | **10 dias de atraso; R$ 10,00** | Valida o cálculo para um atraso maior. |
| T04 | Devolução antes do vencimento | `R - D < 0`, portanto `A = max(0, R - D) = 0` e `M = 0 × 1,00` | **0 dias de atraso; R$ 0,00** | Valida que resultados negativos são limitados a zero. |

## Critérios de validação

Um caso de teste é considerado aprovado quando:

- a condição de entrada está claramente definida;
- o valor de **A** corresponde à fórmula `max(0, R - D)`;
- a multa **M** corresponde a `A × R$ 1,00`;
- devoluções no prazo ou antecipadas não geram atraso nem multa;
- devoluções posteriores ao prazo geram multa proporcional aos dias de atraso.

## Relação com a unidade funcional

Os testes validam a etapa **4.3 — Cálculo dos dias de atraso** da unidade funcional de devolução. Após o cálculo, o resultado pode ser utilizado pelo processo de registro da devolução e apresentado ao usuário.

## Resultado esperado da validação

Os quatro casos mínimos definidos para a Entrega 1 cobrem:

1. limite inferior do cálculo;
2. atraso curto;
3. atraso maior;
4. devolução antecipada.

Assim, a documentação estabelece uma referência objetiva para a futura implementação e para os testes automatizados da regra matemática.
