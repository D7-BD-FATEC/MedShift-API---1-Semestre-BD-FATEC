# Estratégia de Branches

## 1. Objetivo

A estratégia de branches do projeto MedShift tem como objetivo organizar o desenvolvimento, reduzir conflitos entre alterações e manter a branch principal do projeto em um estado estável.

A equipe utilizará branches separadas para o desenvolvimento de funcionalidades, correções, testes e alterações de documentação.

O desenvolvimento deverá ocorrer de forma organizada, permitindo identificar facilmente qual User Story, correção ou documento está relacionado a cada alteração.

---

## 2. Branch principal

### `main`

A branch `main` representa a versão estável do projeto.

Somente alterações concluídas, revisadas e consideradas adequadas pela equipe deverão ser incorporadas à `main`.

O desenvolvimento de novas funcionalidades não deverá ser realizado diretamente nessa branch.

A `main` deverá conter:

- código considerado estável;
- documentação oficial do projeto;
- funcionalidades concluídas;
- correções revisadas;
- versões utilizadas nas apresentações e entregas.

---

## 3. Branches de funcionalidades

Para o desenvolvimento de funcionalidades relacionadas às User Stories, será utilizado o seguinte padrão:

```text
feature/USXX-descricao
```

Onde:

- `feature` indica o desenvolvimento de uma nova funcionalidade;
- `USXX` identifica a User Story relacionada;
- `descricao` apresenta resumidamente a funcionalidade desenvolvida.

### Exemplos

```text
feature/US01-selecao-turno
feature/US02-quantidade-profissionais
feature/US03-validacao-quantidades
feature/US04-verificacao-cobertura
feature/US05-publicacao-plantao
feature/US06-motivo-reprovacao
feature/US07-escolha-invalida
```

Cada branch de funcionalidade deverá, sempre que possível, estar associada a uma User Story específica.

---

## 4. Branches de correção

Para correções de funcionalidades existentes, será utilizado o prefixo:

```text
fix/
```

Formato:

```text
fix/USXX-descricao
```

### Exemplos

```text
fix/US03-validacao-negativos
fix/US04-calculo-cobertura
fix/US07-turno-invalido
```

Caso a correção não esteja diretamente relacionada a uma User Story, poderá ser utilizada uma descrição objetiva.

Exemplo:

```text
fix/mensagem-resultado
```

---

## 5. Branches de documentação

Para alterações exclusivamente relacionadas à documentação, será utilizado o prefixo:

```text
docs/
```

Formato recomendado:

```text
docs/descricao
```

### Exemplos

```text
docs/product-backlog
docs/sprint-backlog
docs/cenarios-teste
docs/manual-usuario
docs/manual-instalacao
docs/registro-decisoes
```

Alterações pequenas de documentação relacionadas diretamente a uma funcionalidade também poderão ser realizadas na mesma branch da User Story.

---

## 6. Branches de testes

Quando for necessária uma branch específica para criação ou ajuste de cenários de teste, será utilizado:

```text
test/
```

Formato:

```text
test/CTXX-descricao
```

### Exemplos

```text
test/CT01-cobertura-adequada
test/CT03-quantidade-negativa
test/CT04-turno-invalido
```

Caso os testes façam parte diretamente do desenvolvimento de uma User Story, eles poderão permanecer na branch da própria funcionalidade.

---

# 7. Regras para nomes das branches

Os nomes das branches deverão seguir as seguintes regras:

- utilizar letras minúsculas sempre que possível;
- não utilizar espaços;
- utilizar hífen para separar palavras;
- utilizar nomes curtos e objetivos;
- identificar a User Story quando a alteração estiver relacionada a uma história;
- evitar nomes genéricos como `teste`, `nova`, `alteracao` ou `branch1`.

### Correto

```text
feature/US01-selecao-turno
```

### Evitar

```text
branch-nova
teste
alteracoes
lucas
codigo-novo
```

---

# 8. Fluxo de desenvolvimento

O fluxo recomendado para desenvolvimento será:

```text
main
  |
  | cria nova branch
  v
feature/USXX-descricao
  |
  | desenvolvimento
  | commits
  | testes
  v
Pull Request
  |
  | revisão
  v
main
```

---

## 9. Criação de uma nova branch

Antes de iniciar o desenvolvimento de uma funcionalidade, a equipe deverá partir da versão mais recente da `main`.

Exemplo:

```bash
git checkout main
git pull origin main
```

Depois deverá criar a branch correspondente à tarefa.

Exemplo:

```bash
git checkout -b feature/US01-selecao-turno
```

---

## 10. Desenvolvimento

Durante o desenvolvimento, os integrantes deverão realizar commits conforme o padrão definido no projeto.

O padrão de commits está documentado em:

```text
docs/commit-pattern.md
```

Exemplo:

```text
feat: US01 - adiciona menu de seleção de turno
```

Os commits deverão representar alterações compreensíveis e relacionadas ao trabalho realizado.

---

## 11. Envio da branch para o GitHub

Após realizar os commits locais, a branch deverá ser enviada ao GitHub.

Exemplo:

```bash
git push -u origin feature/US01-selecao-turno
```

Após esse comando, a branch ficará disponível no repositório remoto.

---

# 12. Pull Request

Quando o desenvolvimento da branch estiver concluído, deverá ser criado um Pull Request para integrar as alterações à `main`.

O Pull Request deverá indicar:

- qual User Story ou tarefa foi desenvolvida;
- o que foi alterado;
- quais testes foram realizados;
- se existem pendências conhecidas.

### Exemplo de título

```text
US01 - Implementa seleção de turno
```

### Exemplo de descrição

```text
## User Story

US01 — Selecionar o turno do plantão.

## Alterações

- criado menu de seleção de turno;
- adicionadas opções Manhã, Tarde e Noite;
- implementada leitura pelo teclado.

## Testes

- seleção de turno válido;
- seleção de opção inválida.

## Status

Pronto para revisão.
```

---

# 13. Revisão

Antes da integração com a `main`, as alterações deverão ser verificadas.

A revisão deverá observar, quando aplicável:

- funcionamento correto do algoritmo;
- atendimento aos critérios de aceitação;
- respeito às regras de negócio;
- tratamento de entradas inválidas;
- clareza das mensagens apresentadas;
- funcionamento no VisuAlg;
- atualização da documentação;
- realização dos cenários de teste relacionados.

Alterações que apresentarem problemas deverão ser corrigidas antes da integração.

---

# 14. Merge

Após a revisão e aprovação do Pull Request, as alterações poderão ser integradas à `main`.

O objetivo é garantir que somente funcionalidades consideradas prontas façam parte da versão principal do projeto.

Após o merge, a `main` deverá permanecer executável e consistente com a documentação do projeto.

---

# 15. Exclusão da branch

Depois que uma branch for incorporada à `main`, ela poderá ser excluída.

Isso ajuda a evitar o acúmulo de branches que já não estão sendo utilizadas.

Exemplo:

```bash
git branch -d feature/US01-selecao-turno
```

Para remover também a branch remota:

```bash
git push origin --delete feature/US01-selecao-turno
```

A exclusão deverá ocorrer somente depois que a equipe confirmar que as alterações foram integradas corretamente.

---

# 16. Correção após revisão

Caso um problema seja identificado durante a revisão do Pull Request, não será necessário criar outra branch.

A correção poderá ser realizada na mesma branch.

Exemplo:

```text
feature/US03-validacao-quantidades
```

Após a correção:

```bash
git add .
git commit -m "fix: US03 - corrige validação de quantidade negativa"
git push
```

O Pull Request será atualizado automaticamente com o novo commit.

---

# 17. Conflitos

Caso ocorram conflitos entre branches, a equipe deverá:

1. identificar os arquivos em conflito;
2. analisar as alterações realizadas;
3. manter as partes corretas de cada versão;
4. testar novamente o projeto;
5. realizar um novo commit após a resolução.

A equipe deverá evitar resolver conflitos sem compreender as alterações envolvidas.

---

# 18. Responsabilidade dos integrantes

Todos os integrantes da equipe deverão seguir a estratégia de branches definida neste documento.

### Desenvolvedores

Responsáveis por:

- criar branches para suas funcionalidades;
- realizar commits organizados;
- testar as alterações;
- abrir Pull Requests;
- corrigir problemas identificados durante a revisão.

### Product Owner

Responsável por auxiliar na verificação de:

- atendimento à necessidade da User Story;
- critérios de aceitação;
- comportamento esperado pelo cliente.

### Scrum Master

Responsável por auxiliar a equipe na aplicação do fluxo definido e na organização do processo de desenvolvimento.

---

# 19. Relação com a Definition of Done

Uma funcionalidade não deverá ser considerada concluída apenas porque foi implementada em uma branch.

Para ser considerada concluída, deverá atender à Definition of Done registrada em:

```text
docs/sprint-1/DoD.md
```

Entre os critérios estão:

- implementação concluída;
- funcionamento no VisuAlg;
- critérios de aceitação atendidos;
- testes realizados;
- documentação atualizada;
- código versionado;
- integração ao incremento da Sprint.

---

# 20. Exemplo completo

Para desenvolver a US01:

### 1. Atualizar a `main`

```bash
git checkout main
git pull origin main
```

### 2. Criar a branch

```bash
git checkout -b feature/US01-selecao-turno
```

### 3. Desenvolver a funcionalidade

Implementar a seleção de turno no VisuAlg.

### 4. Adicionar os arquivos

```bash
git add .
```

### 5. Criar o commit

```bash
git commit -m "feat: US01 - adiciona seleção de turno"
```

### 6. Enviar a branch

```bash
git push -u origin feature/US01-selecao-turno
```

### 7. Criar um Pull Request

```text
feature/US01-selecao-turno
        ↓
       main
```

### 8. Revisar

A equipe verifica:

- critérios de aceitação;
- funcionamento;
- testes;
- documentação.

### 9. Realizar o merge

Após aprovação, a funcionalidade poderá ser incorporada à `main`.

---

# 21. Resumo da estratégia

| Tipo de alteração | Padrão da branch |
|---|---|
| Funcionalidade | `feature/USXX-descricao` |
| Correção | `fix/USXX-descricao` |
| Documentação | `docs/descricao` |
| Testes | `test/CTXX-descricao` |

A branch `main` deverá permanecer como referência estável do projeto.

Novas funcionalidades deverão ser desenvolvidas em branches separadas e integradas à `main` após revisão.

Essa estratégia será utilizada durante o desenvolvimento do MedShift para melhorar a organização, a rastreabilidade e a colaboração entre os integrantes da equipe.
