# Padrão de Mensagens de Commit

## 1. Objetivo

Este documento define o padrão de mensagens de commit adotado pela equipe responsável pelo desenvolvimento do projeto MedShift.

O objetivo é manter o histórico do repositório organizado, facilitar a identificação das alterações realizadas e permitir a rastreabilidade entre commits, tarefas, cenários de teste e User Stories do projeto.

---

## 2. Estrutura do commit

As mensagens de commit deverão seguir o seguinte formato:

```text
tipo: referência - descrição
```

### Exemplos

```text
feat: US01 - adiciona menu de seleção de turno
fix: US03 - corrige validação de quantidade negativa
docs: backlog - atualiza Product Backlog
test: CT01 - adiciona cenário de cobertura adequada
refactor: US04 - reorganiza verificação da cobertura mínima
chore: projeto - organiza arquivos do repositório
```

---

## 3. Tipos de commit

Os seguintes tipos serão utilizados pela equipe:

| Tipo | Finalidade |
|---|---|
| `feat` | Adição de uma nova funcionalidade |
| `fix` | Correção de erro ou comportamento incorreto |
| `docs` | Alteração exclusivamente de documentação |
| `test` | Criação ou alteração de testes |
| `refactor` | Reorganização do código sem alterar seu comportamento esperado |
| `chore` | Organização, manutenção ou alteração auxiliar do projeto |

---

## 4. `feat` — Nova funcionalidade

O tipo `feat` deverá ser utilizado quando uma nova funcionalidade for adicionada ao sistema.

Formato:

```text
feat: USXX - descrição
```

### Exemplos

```text
feat: US01 - adiciona seleção de turno
feat: US02 - adiciona entrada de quantidade de profissionais
feat: US03 - adiciona validação de quantidades
feat: US04 - adiciona verificação de cobertura mínima
feat: US05 - adiciona conclusão de publicação do plantão
feat: US06 - adiciona motivo da reprovação
feat: US07 - adiciona tratamento de escolha inválida
```

Sempre que possível, o commit deverá indicar a User Story relacionada.

---

## 5. `fix` — Correção

O tipo `fix` deverá ser utilizado para corrigir erros encontrados durante o desenvolvimento ou os testes.

Formato:

```text
fix: USXX - descrição
```

### Exemplos

```text
fix: US03 - corrige validação de quantidade negativa
fix: US04 - corrige comparação da cobertura mínima
fix: US06 - corrige mensagem de especialidade insuficiente
fix: US07 - corrige tratamento de turno inválido
```

Caso a correção não esteja diretamente relacionada a uma User Story, poderá ser utilizada uma referência descritiva.

Exemplo:

```text
fix: resultado - corrige mensagem final da análise
```

---

## 6. `docs` — Documentação

O tipo `docs` deverá ser utilizado quando a alteração afetar apenas arquivos de documentação.

Formato:

```text
docs: referência - descrição
```

### Exemplos

```text
docs: backlog - atualiza Product Backlog
docs: sprint backlog - estrutura planejamento da Sprint 1
docs: testes - atualiza cenários de teste
docs: decisoes - registra decisões da Sprint 1
docs: manual - atualiza Manual do Usuário
docs: instalacao - atualiza Manual de Instalação
docs: branches - atualiza estratégia de branches
```

Alterações de documentação que acompanham uma funcionalidade poderão ser incluídas no mesmo desenvolvimento da User Story, desde que o commit continue claro.

---

## 7. `test` — Testes

O tipo `test` deverá ser utilizado para criação ou alteração de cenários de teste.

Formato:

```text
test: CTXX - descrição
```

### Exemplos

```text
test: CT01 - adiciona cenário de cobertura adequada
test: CT02 - adiciona cenário de falta de Pediatra
test: CT03 - adiciona cenário de quantidade negativa
test: CT04 - adiciona cenário de turno inválido
```

Caso vários cenários relacionados sejam atualizados ao mesmo tempo, poderá ser utilizada uma descrição geral.

Exemplo:

```text
test: sprint 1 - atualiza cenários de validação
```

---

## 8. `refactor` — Refatoração

O tipo `refactor` deverá ser utilizado quando o código for reorganizado sem alterar o comportamento esperado da funcionalidade.

Formato:

```text
refactor: USXX - descrição
```

### Exemplos

```text
refactor: US04 - reorganiza verificação da cobertura mínima
refactor: US06 - reorganiza exibição das especialidades insuficientes
```

A refatoração não deverá introduzir uma nova funcionalidade.

---

## 9. `chore` — Manutenção

O tipo `chore` deverá ser utilizado para tarefas de manutenção ou organização que não representem diretamente uma funcionalidade, correção, teste ou documentação.

### Exemplos

```text
chore: projeto - organiza estrutura de diretórios
chore: repositorio - remove arquivo duplicado
chore: projeto - ajusta organização dos arquivos
```

---

# 10. Referência da tarefa

Sempre que possível, a mensagem deverá identificar a User Story, cenário de teste ou documento relacionado.

### User Stories

```text
US01
US02
US03
US04
US05
US06
US07
```

### Cenários de teste

```text
CT01
CT02
CT03
CT04
CT05
CT06
CT07
CT08
CT09
CT10
```

### Documentação

Podem ser utilizadas referências como:

```text
backlog
sprint backlog
testes
decisoes
manual
instalacao
branches
commits
```

---

# 11. Descrição do commit

A descrição deverá informar de forma objetiva o que foi alterado.

Preferencialmente, deverá começar com um verbo no presente.

### Exemplos adequados

```text
adiciona seleção de turno
corrige validação de quantidade negativa
atualiza critérios de aceitação
adiciona cenário de teste
remove documentação duplicada
organiza verificação da cobertura
```

### Evitar

```text
alteração
mudança
teste
atualização
coisas novas
mexi no código
arrumei
final
final mesmo
versão nova
```

O objetivo é permitir que qualquer integrante compreenda o que foi realizado apenas lendo a mensagem do commit.

---

# 12. Tamanho do commit

Cada commit deverá representar uma alteração lógica e compreensível.

Sempre que possível, deverão ser evitados commits que misturem diversas alterações sem relação entre si.

Por exemplo, o desenvolvimento da seleção de turno não deverá ser misturado, no mesmo commit, com uma alteração não relacionada no Manual de Instalação.

Commits menores e objetivos facilitam:

- revisão;
- identificação de erros;
- rastreabilidade;
- compreensão do histórico;
- reversão de alterações, quando necessária.

---

# 13. Exemplos por User Story

## US01 — Seleção de turno

```text
feat: US01 - adiciona menu de seleção de turno
test: CT04 - adiciona teste de turno inválido
fix: US01 - corrige identificação do turno selecionado
```

## US02 — Quantidade de profissionais

```text
feat: US02 - adiciona entrada das quantidades de profissionais
fix: US02 - corrige leitura da quantidade de Cirurgiões
```

## US03 — Validação

```text
feat: US03 - adiciona validação de quantidades negativas
fix: US03 - permite quantidade zero como entrada válida
```

A validação do limite máximo somente deverá ser adicionada após a equipe definir o valor e o cliente/P2 validá-lo.

Depois dessa definição, poderá ser utilizado um commit semelhante a:

```text
feat: US03 - adiciona validação do limite máximo
```

## US04 — Cobertura mínima

```text
feat: US04 - adiciona verificação da cobertura mínima
fix: US04 - corrige condição de cobertura dos Pediatras
```

## US05 — Publicação

```text
feat: US05 - adiciona conclusão sobre publicação do plantão
```

## US06 — Motivo da reprovação

```text
feat: US06 - adiciona motivo da reprovação do plantão
fix: US06 - corrige exibição da quantidade informada
```

## US07 — Escolhas inválidas

```text
feat: US07 - adiciona tratamento de opção inválida
test: CT04 - valida comportamento de turno inexistente
```

---

# 14. Exemplos de documentação

```text
docs: backlog - atualiza critérios de aceitação
docs: backlog - corrige status do limite máximo
docs: sprint backlog - estrutura planejamento da Sprint 1
docs: testes - corrige status do limite máximo
docs: decisoes - registra decisões da Sprint 1
docs: manual - atualiza regras de utilização
docs: branches - completa estratégia de desenvolvimento
docs: commits - completa padrão de mensagens
```

---

# 15. Exemplos incorretos

Os seguintes formatos deverão ser evitados:

```text
Update README.md
Update testes.md
Update arquivo
mudanças
teste
commit
novo
ajustes
arrumei
final
versão final
```

Essas mensagens não explicam adequadamente o motivo ou o conteúdo da alteração.

Também deverá ser evitado:

```text
feat: alteracoes
```

O formato correto deverá incluir uma referência e uma descrição clara.

Exemplo:

```text
feat: US01 - adiciona seleção de turno
```

---

# 16. Commits e branches

Os commits deverão ser realizados preferencialmente nas branches correspondentes ao trabalho em desenvolvimento.

Exemplo:

```text
Branch:
feature/US01-selecao-turno

Commit:
feat: US01 - adiciona menu de seleção de turno
```

Outro exemplo:

```text
Branch:
fix/US03-validacao-negativos

Commit:
fix: US03 - corrige validação de quantidade negativa
```

A estratégia completa de branches está documentada em:

```text
docs/branch-strategy.md
```

---

# 17. Relação com Pull Requests

Os commits realizados em uma branch serão apresentados no Pull Request correspondente.

Por isso, mensagens claras facilitam a revisão das alterações pela equipe.

Exemplo de histórico adequado:

```text
feat: US01 - adiciona menu de seleção de turno
feat: US01 - identifica turno selecionado
test: CT04 - adiciona teste de turno inválido
fix: US01 - corrige mensagem de turno inválido
```

Ao analisar o Pull Request, a equipe conseguirá compreender a evolução da funcionalidade.

---

# 18. Regra da equipe

A partir da adoção deste padrão, novos commits deverão seguir a estrutura:

```text
tipo: referência - descrição
```

Exemplos:

```text
feat: US01 - adiciona seleção de turno
fix: US03 - corrige validação de quantidade negativa
docs: backlog - atualiza Product Backlog
test: CT01 - adiciona cenário de cobertura adequada
```

Não é necessário alterar ou apagar commits antigos que foram realizados antes da definição deste padrão.

O padrão deverá ser aplicado principalmente aos novos commits realizados pela equipe.

---

# 19. Resumo

| Tipo | Utilização | Exemplo |
|---|---|---|
| `feat` | Nova funcionalidade | `feat: US01 - adiciona seleção de turno` |
| `fix` | Correção | `fix: US03 - corrige validação negativa` |
| `docs` | Documentação | `docs: backlog - atualiza Product Backlog` |
| `test` | Testes | `test: CT01 - adiciona cenário de teste` |
| `refactor` | Reorganização do código | `refactor: US04 - reorganiza verificação` |
| `chore` | Manutenção | `chore: projeto - organiza arquivos` |

O uso consistente desse padrão permitirá manter o histórico do projeto MedShift organizado e facilitará a rastreabilidade entre desenvolvimento, documentação, testes e User Stories.
