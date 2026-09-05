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

## 6. DEC06 — Proposta de limite máximo de profissionais

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
