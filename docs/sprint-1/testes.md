# Cenários de Teste — Sprint 1

## 1. Objetivo

Este documento apresenta os cenários de teste utilizados para validar o incremento desenvolvido durante a Sprint 1 do projeto MedShift.

Os testes têm como objetivo verificar se o sistema analisa corretamente um plantão médico, identifica problemas de cobertura e apresenta mensagens adequadas ao usuário.

---

## 2. Regras consideradas nos testes

O sistema deve considerar os seguintes turnos:

- Manhã
- Tarde
- Noite

Cada plantão deve possuir profissionais das seguintes especialidades:

- Clínico Geral
- Pediatra
- Cirurgião

A cobertura mínima exigida para todos os turnos é:

| Especialidade | Manhã | Tarde | Noite |
|---|---:|---:|---:|
| Clínico Geral | 2 | 2 | 2 |
| Pediatra | 1 | 1 | 1 |
| Cirurgião | 1 | 1 | 1 |

Um plantão somente poderá ser publicado quando todas as especialidades atenderem à cobertura mínima exigida.

Quantidades negativas não devem ser aceitas.

O valor máximo permitido para a quantidade de profissionais deverá utilizar o limite definido e validado com o cliente/P2.

---

## 3. Cenários de teste

### CT01 — Plantão com cobertura adequada

**Objetivo:** verificar se o sistema aprova um plantão que atende à cobertura mínima.

**Dados de entrada:**

| Campo | Valor |
|---|---|
| Turno | Manhã |
| Clínicos Gerais | 2 |
| Pediatras | 1 |
| Cirurgiões | 1 |

**Resultado esperado:**

O sistema deve informar que o plantão possui cobertura adequada e pode ser publicado.

**Status:** A executar

---

### CT02 — Plantão com falta de profissional

**Objetivo:** verificar se o sistema identifica a falta de profissionais de uma especialidade.

**Dados de entrada:**

| Campo | Valor |
|---|---|
| Turno | Manhã |
| Clínicos Gerais | 2 |
| Pediatras | 0 |
| Cirurgiões | 1 |

**Resultado esperado:**

O sistema deve informar que o plantão não pode ser publicado e indicar que a quantidade de Pediatras é insuficiente.

**Status:** A executar

---

### CT03 — Quantidade negativa

**Objetivo:** verificar se o sistema impede a utilização de uma quantidade impossível de profissionais.

**Dados de entrada:**

| Campo | Valor |
|---|---|
| Turno | Tarde |
| Clínicos Gerais | -1 |

**Resultado esperado:**

O sistema deve rejeitar o valor informado e apresentar uma mensagem indicando que a quantidade é inválida.

**Status:** A executar

---

### CT04 — Opção de turno inválida

**Objetivo:** verificar o comportamento do sistema quando uma opção inexistente é selecionada.

**Dados de entrada:**

| Campo | Valor |
|---|---|
| Opção de turno | 9 |

**Resultado esperado:**

O sistema deve informar que a opção selecionada é inválida.

**Status:** A executar

---

### CT05 — Cobertura acima do mínimo

**Objetivo:** verificar se o sistema aprova um plantão cuja quantidade de profissionais seja superior ao mínimo exigido.

**Dados de entrada:**

| Campo | Valor |
|---|---|
| Turno | Noite |
| Clínicos Gerais | 4 |
| Pediatras | 2 |
| Cirurgiões | 2 |

**Resultado esperado:**

O sistema deve informar que o plantão possui cobertura adequada e pode ser publicado.

**Status:** A executar

---

### CT06 — Falta de Clínico Geral

**Objetivo:** verificar se o sistema identifica cobertura insuficiente de Clínicos Gerais.

**Dados de entrada:**

| Campo | Valor |
|---|---|
| Turno | Tarde |
| Clínicos Gerais | 1 |
| Pediatras | 1 |
| Cirurgiões | 1 |

**Resultado esperado:**

O sistema deve informar que o plantão não pode ser publicado e indicar que a quantidade de Clínicos Gerais é insuficiente.

**Status:** A executar

---

### CT07 — Falta de Cirurgião

**Objetivo:** verificar se o sistema identifica cobertura insuficiente de Cirurgiões.

**Dados de entrada:**

| Campo | Valor |
|---|---|
| Turno | Noite |
| Clínicos Gerais | 2 |
| Pediatras | 1 |
| Cirurgiões | 0 |

**Resultado esperado:**

O sistema deve informar que o plantão não pode ser publicado e indicar que a quantidade de Cirurgiões é insuficiente.

**Status:** A executar

---

## 4. Registro da execução

Após a execução de cada teste, a equipe deverá atualizar a coluna de status.

Os estados utilizados serão:

- A executar
- Aprovado
- Reprovado

Caso um teste seja reprovado, o problema identificado deverá ser corrigido antes que a funcionalidade seja considerada concluída.

---

## 5. Roteiro para a Sprint Review

Durante a Sprint Review, a equipe deverá demonstrar pelo menos os seguintes cenários:

1. Plantão que atende à cobertura mínima.
2. Plantão com falta de profissional de uma especialidade.
3. Entrada de uma quantidade inválida.
4. Seleção de uma opção inválida.

A demonstração deverá ser realizada diretamente no sistema, sem necessidade de alteração do código durante a apresentação.

---

## 6. Resultado dos testes

| Cenário | Descrição | Status |
|---|---|---|
| CT01 | Cobertura mínima adequada | A executar |
| CT02 | Falta de Pediatra | A executar |
| CT03 | Quantidade negativa | A executar |
| CT04 | Opção de turno inválida | A executar |
| CT05 | Cobertura acima do mínimo | A executar |
| CT06 | Falta de Clínico Geral | A executar |
| CT07 | Falta de Cirurgião | A executar |

---

## 7. Critério de conclusão

Os testes relacionados às funcionalidades implementadas devem ser executados antes da conclusão da Sprint.

Uma funcionalidade somente poderá ser considerada concluída quando atender aos critérios de aceite definidos e produzir o resultado esperado nos cenários de teste correspondentes.
