# Cenários de Teste — Sprint 1

## 1. Objetivo

Este documento apresenta os cenários de teste utilizados para validar o incremento desenvolvido durante a Sprint 1 do projeto MedShift.

Os testes têm como objetivo verificar se o sistema:

- recebe corretamente os dados necessários para a análise de um plantão;
- valida as entradas informadas;
- verifica a cobertura mínima das especialidades;
- identifica especialidades com quantidade insuficiente de profissionais;
- informa se o plantão pode ou não ser publicado;
- apresenta mensagens claras em situações de erro;
- produz os resultados esperados no VisuAlg sem necessidade de alteração do código entre os cenários.

---

## 2. Regras consideradas nos testes

O sistema deve considerar os seguintes turnos:

- Manhã;
- Tarde;
- Noite.

Cada plantão deve possuir informações sobre as seguintes especialidades:

- Clínico Geral;
- Pediatra;
- Cirurgião.

### Cobertura mínima

| Especialidade | Manhã | Tarde | Noite |
|---|---:|---:|---:|
| Clínico Geral | 2 | 2 | 2 |
| Pediatra | 1 | 1 | 1 |
| Cirurgião | 1 | 1 | 1 |

Um plantão somente poderá ser publicado quando todas as especialidades atenderem à cobertura mínima exigida.

Quantidades negativas de profissionais não devem ser aceitas.

A quantidade **0 é considerada uma entrada válida**, pois pode representar a ausência de profissionais disponíveis de determinada especialidade.

Nesse caso, o valor deverá ser utilizado normalmente na análise da cobertura.

### Limite máximo em definição

A equipe ainda está definindo internamente um valor máximo plausível de profissionais por especialidade em um único plantão.

Enquanto esse valor não for definido, ele será representado temporariamente por **X** na documentação.

O símbolo **X não representa um valor numérico definitivo**.

Depois que a equipe definir um valor máximo e elaborar sua justificativa, a proposta será apresentada ao cliente/P2 para validação.

Somente após essa validação o limite poderá ser considerado uma regra definitiva do sistema.

**Valor máximo atual:** X profissionais por especialidade.

**Status do limite máximo:** Em definição pela equipe.

### Tratamento de entradas inválidas

Quando uma entrada inválida for identificada, o sistema deverá:

1. informar claramente o erro;
2. impedir que o dado inválido seja utilizado na análise;
3. encerrar a análise atual.

Nesta Sprint, não é obrigatório solicitar uma nova digitação após um erro.

São consideradas entradas inválidas:

- quantidades negativas;
- opções de turno inexistentes;
- futuramente, quantidades superiores ao limite máximo, após esse limite ser definido pela equipe e validado pelo cliente/P2.

A quantidade **0 não é inválida**.

### Resultado final da análise

Quando a análise for concluída normalmente, o sistema deverá informar:

- o turno analisado;
- se a cobertura mínima foi atingida ou não;
- a especialidade ou as especialidades insuficientes, quando houver;
- a quantidade necessária e a quantidade informada para cada especialidade insuficiente;
- se o plantão pode ou não ser publicado.

---

# 3. Cenários de Teste

## CT01 — Plantão com cobertura mínima adequada

**Objetivo:**

Verificar se o sistema aprova um plantão que atende exatamente à cobertura mínima exigida.

**Dados de entrada:**

| Campo | Valor |
|---|---:|
| Turno | Manhã |
| Clínicos Gerais | 2 |
| Pediatras | 1 |
| Cirurgiões | 1 |

**Resultado esperado:**

```text
===== RESULTADO DA ANÁLISE =====

Turno analisado: MANHÃ

Cobertura mínima: ATINGIDA

Conclusão:
Plantão PODE ser publicado.
```

**Critério de sucesso:**

O teste será aprovado se o sistema reconhecer que todas as especialidades atendem à cobertura mínima e concluir que o plantão pode ser publicado.

**Status:** A executar

---

## CT02 — Falta de Pediatra

**Objetivo:**

Verificar se o sistema identifica corretamente uma quantidade insuficiente de Pediatras.

Este teste também confirma que o valor **0 é uma entrada válida** e deve participar da análise.

**Dados de entrada:**

| Campo | Valor |
|---|---:|
| Turno | Manhã |
| Clínicos Gerais | 2 |
| Pediatras | 0 |
| Cirurgiões | 1 |

**Resultado esperado:**

```text
===== RESULTADO DA ANÁLISE =====

Turno analisado: MANHÃ

Cobertura mínima: NÃO ATINGIDA

Especialidade com cobertura insuficiente:
Pediatra

Quantidade necessária: 1
Quantidade informada: 0

Conclusão:
Plantão NÃO pode ser publicado.
```

**Critério de sucesso:**

O teste será aprovado se o sistema aceitar o valor 0 como entrada válida, identificar a insuficiência de Pediatras e impedir a publicação do plantão.

**Status:** A executar

---

## CT03 — Quantidade negativa

**Objetivo:**

Verificar se o sistema impede a utilização de uma quantidade impossível de profissionais.

**Dados de entrada:**

| Campo | Valor |
|---|---:|
| Turno | Tarde |
| Clínicos Gerais | -1 |

**Resultado esperado:**

```text
ERRO: quantidade inválida.

A quantidade de profissionais não pode ser negativa.

Análise encerrada.
```

**Critério de sucesso:**

O teste será aprovado se o sistema rejeitar o valor negativo, explicar claramente o erro, não utilizar o valor na análise e encerrar a execução atual.

**Status:** A executar

---

## CT04 — Opção de turno inválida

**Objetivo:**

Verificar o comportamento do sistema quando o coordenador seleciona uma opção de turno inexistente.

**Dados de entrada:**

| Campo | Valor |
|---|---:|
| Opção de turno | 9 |

**Resultado esperado:**

```text
ERRO: turno inválido.

Escolha uma das opções disponíveis:
1 - Manhã
2 - Tarde
3 - Noite

Análise encerrada.
```

**Critério de sucesso:**

O teste será aprovado se o sistema identificar a opção inválida, informar o erro, impedir que a opção seja utilizada e encerrar a análise atual.

**Status:** A executar

---

## CT05 — Cobertura acima do mínimo

**Objetivo:**

Verificar se o sistema aprova um plantão quando as quantidades de profissionais são superiores às coberturas mínimas exigidas.

**Dados de entrada:**

| Campo | Valor |
|---|---:|
| Turno | Noite |
| Clínicos Gerais | 4 |
| Pediatras | 2 |
| Cirurgiões | 2 |

**Resultado esperado:**

```text
===== RESULTADO DA ANÁLISE =====

Turno analisado: NOITE

Cobertura mínima: ATINGIDA

Conclusão:
Plantão PODE ser publicado.
```

**Critério de sucesso:**

O teste será aprovado se o sistema reconhecer que valores superiores ao mínimo continuam atendendo à cobertura e permitir a publicação do plantão.

**Status:** A executar

---

## CT06 — Falta de Clínico Geral

**Objetivo:**

Verificar se o sistema identifica corretamente a cobertura insuficiente de Clínicos Gerais.

**Dados de entrada:**

| Campo | Valor |
|---|---:|
| Turno | Tarde |
| Clínicos Gerais | 1 |
| Pediatras | 1 |
| Cirurgiões | 1 |

**Resultado esperado:**

```text
===== RESULTADO DA ANÁLISE =====

Turno analisado: TARDE

Cobertura mínima: NÃO ATINGIDA

Especialidade com cobertura insuficiente:
Clínico Geral

Quantidade necessária: 2
Quantidade informada: 1

Conclusão:
Plantão NÃO pode ser publicado.
```

**Critério de sucesso:**

O teste será aprovado se o sistema identificar corretamente a insuficiência de Clínicos Gerais e concluir que o plantão não pode ser publicado.

**Status:** A executar

---

## CT07 — Falta de Cirurgião

**Objetivo:**

Verificar se o sistema identifica corretamente a cobertura insuficiente de Cirurgiões.

**Dados de entrada:**

| Campo | Valor |
|---|---:|
| Turno | Noite |
| Clínicos Gerais | 2 |
| Pediatras | 1 |
| Cirurgiões | 0 |

**Resultado esperado:**

```text
===== RESULTADO DA ANÁLISE =====

Turno analisado: NOITE

Cobertura mínima: NÃO ATINGIDA

Especialidade com cobertura insuficiente:
Cirurgião

Quantidade necessária: 1
Quantidade informada: 0

Conclusão:
Plantão NÃO pode ser publicado.
```

**Critério de sucesso:**

O teste será aprovado se o sistema identificar corretamente a insuficiência de Cirurgiões e concluir que o plantão não pode ser publicado.

**Status:** A executar

---

## CT08 — Quantidade exatamente no limite máximo

**Objetivo:**

Verificar se o próprio limite máximo continua sendo aceito como entrada válida.

**Observação:**

Este cenário ainda não pode ser executado de forma definitiva porque o valor máximo permanece **em definição pela equipe**.

Enquanto não houver um número definido, o limite continuará sendo representado por **X**.

Após a definição da equipe, o valor deverá ser apresentado ao cliente/P2 para validação.

**Dados de entrada futuros:**

| Campo | Valor |
|---|---:|
| Turno | Manhã |
| Clínicos Gerais | X |
| Pediatras | 1 |
| Cirurgiões | 1 |

**Resultado esperado após a definição e validação do limite:**

```text
===== RESULTADO DA ANÁLISE =====

Turno analisado: MANHÃ

Cobertura mínima: ATINGIDA

Conclusão:
Plantão PODE ser publicado.
```

**Critério de sucesso:**

Depois que o limite máximo for definido pela equipe e validado pelo cliente/P2, o teste será aprovado se a quantidade exatamente igual ao limite for aceita normalmente.

**Status:** Aguardando definição da equipe e validação do cliente/P2

---

## CT09 — Quantidade superior ao limite máximo

**Objetivo:**

Verificar se o sistema rejeita uma quantidade superior ao limite máximo.

**Observação:**

Este cenário ainda não pode ser executado de forma definitiva porque o valor máximo permanece **em definição pela equipe**.

Enquanto não houver um número definido, será utilizada apenas a representação conceitual **X+1**.

**Dados de entrada futuros:**

| Campo | Valor |
|---|---:|
| Turno | Manhã |
| Clínicos Gerais | X+1 |

**Resultado esperado após a definição e validação do limite:**

```text
ERRO: quantidade inválida.

A quantidade informada está acima do limite máximo permitido.

Análise encerrada.
```

**Critério de sucesso:**

Depois que o limite máximo for definido pela equipe e validado pelo cliente/P2, o teste será aprovado se o sistema rejeitar uma quantidade superior ao limite, informar claramente o erro e encerrar a análise sem utilizar o valor informado.

**Status:** Aguardando definição da equipe e validação do cliente/P2

---

## CT10 — Mais de uma especialidade com cobertura insuficiente

**Objetivo:**

Verificar se o sistema identifica todas as especialidades insuficientes quando mais de uma não atende à cobertura mínima.

**Dados de entrada:**

| Campo | Valor |
|---|---:|
| Turno | Manhã |
| Clínicos Gerais | 1 |
| Pediatras | 0 |
| Cirurgiões | 1 |

**Resultado esperado:**

```text
===== RESULTADO DA ANÁLISE =====

Turno analisado: MANHÃ

Cobertura mínima: NÃO ATINGIDA

Especialidades com cobertura insuficiente:

Clínico Geral
Quantidade necessária: 2
Quantidade informada: 1

Pediatra
Quantidade necessária: 1
Quantidade informada: 0

Conclusão:
Plantão NÃO pode ser publicado.
```

**Critério de sucesso:**

O teste será aprovado se o sistema identificar todas as especialidades abaixo da cobertura mínima e concluir que o plantão não pode ser publicado.

**Status:** A executar

---

# 4. Registro da execução

Após a execução de cada teste, a equipe deverá atualizar seu status.

Os estados utilizados serão:

- **A executar:** cenário ainda não testado;
- **Aprovado:** comportamento obtido corresponde ao resultado esperado;
- **Reprovado:** comportamento obtido não corresponde ao resultado esperado;
- **Aguardando definição e validação:** cenário depende de uma regra que ainda precisa ser definida pela equipe e posteriormente validada pelo cliente/P2.

Caso um teste seja reprovado, o problema identificado deverá ser corrigido e o cenário executado novamente antes que a funcionalidade correspondente seja considerada concluída.

---

# 5. Roteiro para a Sprint Review

Durante a Sprint Review, a equipe deverá demonstrar obrigatoriamente pelo menos os seguintes cenários:

1. **Plantão que atende à cobertura mínima**  
   Sugestão: CT01.

2. **Plantão com falta de profissional de uma especialidade**  
   Sugestão: CT02.

3. **Entrada de uma quantidade impossível**  
   Sugestão: CT03.

4. **Seleção de uma opção inválida**  
   Sugestão: CT04.

Caso o limite máximo seja definido pela equipe e validado pelo cliente/P2 antes da Sprint Review, a equipe também poderá demonstrar os cenários CT08 e CT09.

Enquanto o limite máximo não estiver definido e validado, os cenários CT08 e CT09 deverão permanecer pendentes.

A demonstração deverá ser realizada diretamente no VisuAlg.

Os diferentes cenários deverão ser executados por meio da alteração dos dados de entrada, sem necessidade de modificar o código-fonte entre as demonstrações.

---

# 6. Resultado dos testes

| Cenário | Descrição | Status |
|---|---|---|
| CT01 | Cobertura mínima adequada | A executar |
| CT02 | Falta de Pediatra | A executar |
| CT03 | Quantidade negativa | A executar |
| CT04 | Opção de turno inválida | A executar |
| CT05 | Cobertura acima do mínimo | A executar |
| CT06 | Falta de Clínico Geral | A executar |
| CT07 | Falta de Cirurgião | A executar |
| CT08 | Quantidade exatamente no limite máximo | Aguardando definição e validação |
| CT09 | Quantidade acima do limite máximo | Aguardando definição e validação |
| CT10 | Mais de uma especialidade insuficiente | A executar |

---

# 7. Critério de conclusão

Os testes relacionados às funcionalidades implementadas deverão ser executados antes da conclusão da Sprint.

Uma funcionalidade somente poderá ser considerada concluída quando:

- atender aos critérios de aceitação da User Story correspondente;
- produzir o resultado esperado nos cenários de teste;
- impedir que entradas inválidas sejam utilizadas;
- apresentar ao usuário informações claras sobre o resultado da análise;
- puder ser demonstrada no VisuAlg sem alteração do código entre os diferentes cenários.

Os testes CT08 e CT09 somente poderão ser considerados definitivos depois que:

1. a equipe definir internamente um valor máximo plausível;
2. a equipe justificar a escolha desse valor;
3. a proposta for apresentada ao cliente/P2;
4. o cliente/P2 validar o limite máximo.

Até que essas etapas sejam concluídas, os cenários CT08 e CT09 permanecerão com o status **Aguardando definição e validação**.
