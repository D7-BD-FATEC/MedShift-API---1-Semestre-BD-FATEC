# Registro de Decisões — Sprint 1

## 1. Objetivo

Este documento registra as principais decisões tomadas pela equipe durante o desenvolvimento da Sprint 1 do projeto MedShift.

O objetivo é manter um histórico das decisões relacionadas ao produto, às regras de negócio, à organização dos dados e à implementação do sistema.

---

## 2. DEC01 — Uso do VisuAlg

**Decisão:**  
O sistema será desenvolvido utilizando pseudocódigo no VisuAlg.

**Motivo:**  
O uso do VisuAlg é uma restrição definida para o projeto.

**Impacto:**  
A equipe deverá considerar as limitações da ferramenta durante o desenvolvimento, principalmente em relação à utilização de vetores, matrizes e ausência de estruturas do tipo registro.

**Status:** Confirmada.

---

## 3. DEC02 — Interface textual

**Decisão:**  
O sistema será executado por meio de interação textual utilizando teclado e console.

**Motivo:**  
A interface gráfica não faz parte do escopo do projeto.

**Impacto:**  
Todas as operações deverão ser acessíveis por menus, opções numéricas e entradas realizadas pelo usuário através do teclado.

**Status:** Confirmada.

---

## 4. DEC03 — Análise de um plantão por execução

**Decisão:**  
Durante a Sprint 1, o sistema analisará um plantão por vez.

**Motivo:**  
Essa é uma restrição definida para o primeiro incremento do produto.

**Impacto:**  
Não será necessário armazenar ou analisar múltiplos plantões simultaneamente nesta Sprint.

**Status:** Confirmada.

---

## 5. DEC04 — Identificação dos turnos

**Decisão:**  
Os três turnos do hospital serão representados através de opções numéricas no sistema.

Exemplo:

```text
1 - Manhã
2 - Tarde
3 - Noite
