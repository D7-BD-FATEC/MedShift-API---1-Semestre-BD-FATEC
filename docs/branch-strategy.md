# Estratégia de Branches

## 1. Objetivo

A estratégia de branches do projeto MedShift tem como objetivo organizar o desenvolvimento, reduzir conflitos entre alterações e manter a branch principal do projeto em um estado estável.

A equipe utilizará branches separadas para o desenvolvimento de funcionalidades, correções e alterações de documentação.

---

## 2. Branch principal

### `main`

A branch `main` representa a versão estável do projeto.

Somente alterações concluídas, testadas e revisadas devem ser incorporadas à `main`.

O desenvolvimento de novas funcionalidades não deve ser realizado diretamente nessa branch.

---

## 3. Branches de funcionalidades

Para o desenvolvimento de funcionalidades relacionadas às User Stories, será utilizado o seguinte padrão:

```text
feature/USXX-descricao
