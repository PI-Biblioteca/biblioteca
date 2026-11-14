
# Definir variáveis e política de atraso e multa

## 1. Objetivo

Definir uma regra de negócio para identificar atrasos na devolução de livros e calcular a multa correspondente, garantindo que o sistema utilize critérios padronizados.

## 2. Variáveis e unidades

| Variável | Descrição | Unidade |
|---|---|---|
| data_prevista | Data limite para devolução do livro | Data (DD/MM/AAAA) |
| data_efetiva | Data em que o livro foi devolvido | Data (DD/MM/AAAA) |
| dias_atraso | Quantidade de dias após o prazo de devolução | Dias |
| valor_diario | Valor cobrado por dia de atraso | Reais (R$) |
| valor_multa | Valor total da multa | Reais (R$) |

## 3. Regra de identificação do atraso

O atraso será identificado por meio da comparação entre a data prevista e a data efetiva de devolução.

- Se a devolução ocorrer antes ou na data prevista, não haverá atraso.
- Se ocorrer depois da data prevista, será calculada a quantidade de dias de atraso.
- A diferença entre as datas será utilizada para determinar o período de atraso.

**Fórmula:**

```text
dias_atraso = data_efetiva - data_prevista
```

## 4. Política de multa

A multa será calculada multiplicando a quantidade de dias de atraso pelo valor diário estabelecido.

**Fórmula:**

```text
valor_multa = dias_atraso * valor_diario
```

Será adotado o valor diário de **R$ 2,00 por dia de atraso**.

Esse valor foi definido como referência para o projeto acadêmico, permitindo estabelecer um critério simples e uniforme para os cálculos e testes.

## 5. Critérios de contagem

- Serão considerados dias corridos, incluindo sábados, domingos e feriados.
- A comparação será realizada considerando apenas as datas, sem levar em conta os horários.
- O dia seguinte à data prevista será considerado o primeiro dia de atraso.
- A devolução realizada na própria data prevista não gerará multa.

## 6. Exemplos de aplicação

| Data prevista | Data efetiva | Dias de atraso | Multa |
|---|---|---|---|
| 10/11/2026 | 10/11/2026 | 0 | R$ 0,00 |
| 10/11/2026 | 11/11/2026 | 1 | R$ 2,00 |
| 10/11/2026 | 13/11/2026 | 3 | R$ 6,00 |
| 10/11/2026 | 17/11/2026 | 7 | R$ 14,00 |

## 7. Decisões de negócio

Foram estabelecidas as seguintes regras:

- Valor diário da multa: R$ 2,00.
- Contagem de atraso em dias corridos.
- Comparação entre datas sem considerar horários.
- Não haverá cobrança quando a devolução ocorrer dentro do prazo.
- A multa será proporcional à quantidade de dias de atraso.

## 8. Conclusão

A política definida estabelece critérios objetivos para identificar atrasos e calcular multas no Sistema de Biblioteca.

Essas regras servirão como referência para a futura implementação da funcionalidade de devolução e para a elaboração dos testes, garantindo consistência nos resultados apresentados pelo sistema.
