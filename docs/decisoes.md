# Registro de Decisões — Sprint 1

## 1. Objetivo

Este documento registra as principais decisões de produto e decisões técnicas tomadas durante a Sprint 1 do projeto MedShift.

O objetivo é manter a rastreabilidade das escolhas realizadas pela equipe, registrar suas justificativas e facilitar a compreensão da evolução do sistema ao longo das Sprints.

As decisões registradas neste documento podem ter origem em:

- requisitos apresentados pelo cliente;
- restrições estabelecidas para o projeto;
- decisões técnicas tomadas pela equipe;
- validações realizadas com o cliente/P2;
- necessidades identificadas durante o desenvolvimento.

Decisões que ainda dependem de confirmação do cliente/P2 devem permanecer identificadas como pendentes até que sejam formalmente validadas.

---

## 2. Identificação

| Informação | Descrição |
|---|---|
| Projeto | MedShift |
| Sprint | Sprint 1 |
| Instituição | FATEC São José dos Campos |
| Curso | Tecnologia em Banco de Dados |
| Semestre | 1º semestre |
| Product Owner | A preencher |
| Scrum Master | A preencher |
| Equipe | A preencher |
| Última atualização | A preencher |

---

## 3. Estados das decisões

As decisões poderão possuir os seguintes estados:

| Estado | Significado |
|---|---|
| Confirmada | Decisão definida pelo cliente, pelo escopo do projeto ou já validada formalmente |
| Decisão técnica | Escolha realizada pela equipe para implementar uma necessidade |
| Pendente | Necessita de validação ou definição antes de ser considerada definitiva |
| Revisada | Decisão anteriormente registrada que foi posteriormente modificada |

---

# 4. Decisões Registradas

## DEC-001 — Utilização do VisuAlg

**Categoria:** Tecnologia  
**Origem:** Restrição do projeto  
**Status:** Confirmada

### Decisão

A implementação principal do MedShift será realizada utilizando pseudocódigo no VisuAlg.

### Justificativa

O VisuAlg é a ferramenta definida para o desenvolvimento do projeto no primeiro semestre.

### Impactos

A equipe deverá considerar as características e limitações da ferramenta durante o desenvolvimento, principalmente:

- ausência de estruturas do tipo registro;
- vetores limitados a no máximo duas dimensões;
- ausência de gravação permanente de dados em arquivos;
- diferenças de comportamento entre versões do VisuAlg;
- necessidade de adaptar a modelagem de dados aos recursos disponíveis.

### Responsável pela decisão

Definido pelo projeto.

---

## DEC-002 — Interface baseada em console

**Categoria:** Interface  
**Origem:** Restrição do projeto  
**Status:** Confirmada

### Decisão

O MedShift utilizará uma interface textual executada em console.

A interação com o sistema será realizada através do teclado.

### Justificativa

A interface gráfica não faz parte dos requisitos do projeto.

O foco da avaliação está na lógica, nas regras implementadas e na capacidade do sistema de apresentar diagnósticos úteis ao usuário.

### Impactos

O sistema deverá:

- apresentar instruções claras no console;
- permitir a seleção das operações sem necessidade de alterar o código;
- solicitar os dados necessários através do teclado;
- apresentar mensagens compreensíveis ao usuário;
- tratar opções inválidas.

---

## DEC-003 — Análise de um plantão por vez

**Categoria:** Escopo  
**Origem:** Requisito da Sprint 1  
**Status:** Confirmada

### Decisão

Durante a Sprint 1, cada análise realizada pelo sistema considerará apenas um plantão por vez.

### Justificativa

O primeiro incremento do MedShift tem como objetivo resolver o problema mais básico da coordenação: analisar um plantão e determinar se ele possui cobertura adequada.

### Impactos

Nesta Sprint não será necessário:

- armazenar vários plantões simultaneamente;
- comparar diferentes plantões;
- manter histórico de plantões;
- analisar uma escala hospitalar completa.

---

## DEC-004 — Turnos utilizados pelo sistema

**Categoria:** Regra de negócio  
**Origem:** Cliente  
**Status:** Confirmada

### Decisão

O hospital trabalha com três turnos:

1. Manhã;
2. Tarde;
3. Noite.

### Justificativa

Os três turnos foram definidos como parte das regras de negócio apresentadas pelo cliente.

### Impactos

Toda análise deverá estar associada a um dos três turnos definidos.

Uma opção diferente das opções disponíveis deverá ser considerada inválida.

---

## DEC-005 — Representação dos turnos no menu

**Categoria:** Decisão técnica  
**Origem:** Equipe  
**Status:** Decisão técnica

### Decisão

Os turnos poderão ser representados no sistema utilizando códigos numéricos.

Padrão adotado:

```text
1 - Manhã
2 - Tarde
3 - Noite
```
---

---

## DEC06 — Proposta de limite máximo de profissionais

**Decisão:**

A equipe propõe o limite máximo de **X profissionais por especialidade em um único plantão**.

**Motivo:**

O Hospital Santa Aurora é apresentado como uma instituição de médio porte e,
na Sprint 1, a cobertura mínima necessária por plantão é de:

- 2 Clínicos Gerais;
- 1 Pediatra;
- 1 Cirurgião.

Considerando essas quantidades, a equipe entende que valores superiores a
X profissionais de uma mesma especialidade em um único plantão podem indicar
um possível erro de digitação.

O valor de X foi proposto com uma margem consideravelmente superior à
cobertura mínima, evitando que quantidades plausíveis sejam rejeitadas
indevidamente.

**Impacto:**

Caso o limite seja aprovado pelo cliente/P2, valores superiores a X
profissionais por especialidade serão considerados inválidos e não poderão
ser utilizados na análise do plantão.

**Status:** Pendente de validação pelo cliente/P2.

---

## 7. DEC06 — Tratamento de entradas inválidas

**Decisão:**

Quando o usuário informar um dado inválido, o sistema deverá apresentar uma
mensagem clara de erro, impedir que esse dado seja utilizado na análise e
encerrar a execução atual.

Nesta Sprint, o sistema não será obrigado a solicitar uma nova digitação após
a identificação do erro.

**São considerados exemplos de entradas inválidas:**

- quantidade negativa de profissionais;
- quantidade superior ao limite máximo validado pelo cliente/P2;
- opção de turno inexistente.

**Motivo:**

O cliente determinou que nenhum dado inválido pode ser aceito como válido e
que o coordenador precisa compreender claramente qual foi o erro cometido.

A equipe optou por encerrar a análise após uma entrada inválida porque a
repetição da entrada não é um requisito obrigatório da Sprint 1.

**Impacto:**

Ao identificar uma entrada inválida:

1. o sistema exibirá uma mensagem explicando o erro;
2. o valor não será utilizado na análise;
3. a execução atual será encerrada;
4. para realizar uma nova análise, o usuário deverá executar novamente o programa.

**Exemplo:**

```text
ERRO: quantidade inválida.

A quantidade de profissionais não pode ser negativa.

Análise encerrada.
```

---

## DEC07 — Informações obrigatórias no resultado final

**Decisão:**

Ao final da análise de um plantão, o sistema deverá apresentar de forma clara:

- o turno analisado;
- se a cobertura mínima foi atingida ou não;
- a especialidade ou as especialidades com cobertura insuficiente, quando houver;
- a quantidade necessária e a quantidade informada para cada especialidade insuficiente;
- a conclusão indicando se o plantão pode ou não ser publicado.

**Motivo:**

O cliente informou que a coordenação precisa compreender claramente o resultado
da análise e, quando o plantão não puder ser publicado, identificar qual
especialidade apresenta cobertura insuficiente.

A equipe optou por manter também a exibição da quantidade necessária e da
quantidade informada, pois esse nível de detalhe foi considerado útil pelo
cliente para compreender o motivo da reprovação.

**Impacto:**

O resultado não deverá apresentar apenas uma mensagem genérica como
"plantão inválido" ou "plantão não pode ser publicado".

A saída deverá fornecer informações suficientes para que a coordenação saiba:

1. qual turno foi analisado;
2. se a cobertura mínima foi atendida;
3. qual especialidade causou a reprovação, quando aplicável;
4. se o plantão pode ou não ser publicado.

**Exemplo de plantão aprovado:**

```text
===== RESULTADO DA ANÁLISE =====

Turno analisado: MANHÃ

Cobertura mínima: ATINGIDA

Conclusão:
Plantão PODE ser publicado.
````
**Exemplo de plantão reprovado:**

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
