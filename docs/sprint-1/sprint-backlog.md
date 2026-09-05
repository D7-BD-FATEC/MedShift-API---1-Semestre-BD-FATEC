# Sprint Backlog — Sprint 1

## 1. Projeto

**Projeto:** MedShift  
**Sprint:** Sprint 1  
**Tecnologia principal:** VisuAlg  
**Interface:** Console  
**Status do Sprint Backlog:** Em preparação

---

## 2. Meta da Sprint

Permitir que a coordenação hospitalar analise um plantão médico,
verifique se há cobertura mínima de profissionais por especialidade
e receba uma conclusão clara informando se o plantão pode ou não
ser publicado.

---

## 3. Situação atual

As User Stories previstas para a Sprint 1 já foram levantadas e possuem
critérios de aceitação documentados no Product Backlog.

Entretanto, a ordem de prioridade das histórias ainda será definida pelo
cliente/P2.

Por esse motivo, a seleção definitiva e a ordenação dos itens deste
Sprint Backlog permanecem pendentes.

Nenhuma prioridade será atribuída pela equipe antes da definição do cliente/P2.

---

## 4. User Stories candidatas à Sprint 1

| ID | User Story | Prioridade | Seleção definitiva |
|---|---|---|---|
| US01 | Selecionar o turno do plantão | A definir pelo cliente/P2 | Pendente |
| US02 | Informar a quantidade de profissionais | A definir pelo cliente/P2 | Pendente |
| US03 | Validar as quantidades informadas | A definir pelo cliente/P2 | Pendente |
| US04 | Verificar a cobertura mínima do plantão | A definir pelo cliente/P2 | Pendente |
| US05 | Informar se o plantão pode ser publicado | A definir pelo cliente/P2 | Pendente |
| US06 | Informar o motivo da reprovação do plantão | A definir pelo cliente/P2 | Pendente |
| US07 | Tratar escolhas inválidas | A definir pelo cliente/P2 | Pendente |

A tabela será atualizada após a definição da ordem de prioridade pelo cliente/P2.

---

## 5. Tarefas preliminares

As tarefas abaixo representam uma decomposição inicial das User Stories.

Elas poderão ser revisadas durante a Sprint Planning após a definição
das prioridades.

---

### US01 — Selecionar o turno do plantão

#### Tarefas

- [ ] Criar o menu de seleção de turno.
- [ ] Apresentar as opções Manhã, Tarde e Noite.
- [ ] Ler a opção escolhida pelo teclado.
- [ ] Identificar o turno correspondente à opção selecionada.
- [ ] Garantir que a escolha possa ser realizada sem alterar o código.
- [ ] Testar uma opção válida de turno.

#### Dependências

Nenhuma dependência funcional obrigatória.

---

### US02 — Informar a quantidade de profissionais

#### Tarefas

- [ ] Solicitar a quantidade de Clínicos Gerais.
- [ ] Solicitar a quantidade de Pediatras.
- [ ] Solicitar a quantidade de Cirurgiões.
- [ ] Armazenar os valores informados.
- [ ] Garantir que os dados sejam fornecidos pelo teclado.
- [ ] Preparar os valores para utilização na análise de cobertura.

#### Dependências

- US01 — Selecionar o turno do plantão.

---

### US03 — Validar as quantidades informadas

#### Tarefas

- [ ] Verificar se alguma quantidade informada é negativa.
- [ ] Aceitar o valor 0 como uma entrada válida.
- [ ] Apresentar uma mensagem clara quando uma quantidade for inválida.
- [ ] Impedir que valores inválidos sejam utilizados na análise.
- [ ] Encerrar a análise atual quando uma quantidade inválida for identificada.
- [ ] Implementar a validação do limite máximo após sua definição e validação.

#### Dependências

- US02 — Informar a quantidade de profissionais.
- Definição interna do limite máximo de profissionais.
- Validação posterior do limite máximo pelo cliente/P2.

#### Observação

O limite máximo de profissionais ainda está em definição pela equipe.

Enquanto não houver um valor definido e validado, ele será representado
por **X** na documentação.

O símbolo **X não representa um valor numérico definitivo**.

---

### US04 — Verificar a cobertura mínima do plantão

#### Tarefas

- [ ] Comparar a quantidade de Clínicos Gerais com o mínimo de 2.
- [ ] Comparar a quantidade de Pediatras com o mínimo de 1.
- [ ] Comparar a quantidade de Cirurgiões com o mínimo de 1.
- [ ] Identificar se todas as especialidades atendem aos mínimos.
- [ ] Identificar quais especialidades estão abaixo da cobertura mínima.
- [ ] Registrar internamente o resultado da verificação.

#### Dependências

- US02 — Informar a quantidade de profissionais.
- US03 — Validar as quantidades informadas.

---

### US05 — Informar se o plantão pode ser publicado

#### Tarefas

- [ ] Utilizar o resultado da verificação de cobertura.
- [ ] Identificar se a cobertura mínima foi atingida.
- [ ] Informar que o plantão pode ser publicado quando todos os mínimos forem atendidos.
- [ ] Informar que o plantão não pode ser publicado quando algum mínimo não for atendido.
- [ ] Apresentar a conclusão de forma clara no console.

#### Dependências

- US04 — Verificar a cobertura mínima do plantão.

---

### US06 — Informar o motivo da reprovação do plantão

#### Tarefas

- [ ] Identificar a especialidade com cobertura insuficiente.
- [ ] Apresentar a especialidade responsável pela reprovação.
- [ ] Apresentar a quantidade mínima necessária.
- [ ] Apresentar a quantidade informada pelo usuário.
- [ ] Tratar o caso em que mais de uma especialidade esteja abaixo do mínimo.
- [ ] Garantir que o motivo seja apresentado junto à conclusão da análise.

#### Dependências

- US04 — Verificar a cobertura mínima do plantão.
- US05 — Informar se o plantão pode ser publicado.

---

### US07 — Tratar escolhas inválidas

#### Tarefas

- [ ] Identificar uma opção de turno inexistente.
- [ ] Apresentar uma mensagem clara de erro.
- [ ] Impedir que a opção inválida seja utilizada na análise.
- [ ] Encerrar a análise atual após a escolha inválida.
- [ ] Testar pelo menos uma opção inválida.

#### Dependências

- US01 — Selecionar o turno do plantão.

---

## 6. Regras de negócio relacionadas

Durante o desenvolvimento da Sprint 1 deverão ser respeitadas as seguintes regras:

- existem três turnos: Manhã, Tarde e Noite;
- são analisadas as especialidades Clínico Geral, Pediatra e Cirurgião;
- a cobertura mínima é de 2 Clínicos Gerais, 1 Pediatra e 1 Cirurgião;
- todas as especialidades precisam atingir o mínimo para que o plantão possa ser publicado;
- quantidades negativas são inválidas;
- a quantidade 0 é válida;
- opções de turno inexistentes são inválidas;
- o limite máximo de profissionais ainda está em definição;
- entradas inválidas não podem ser utilizadas na análise;
- quando o plantão não puder ser publicado, o motivo deverá ser informado;
- uma única análise por execução é suficiente para atender ao escopo obrigatório da Sprint 1.

---

## 7. Definition of Ready

Antes de uma User Story entrar em desenvolvimento, ela deverá atender aos
critérios estabelecidos no documento:

```text
docs/sprint-1/DoR.md
```

Entre os principais critérios estão:

- descrição clara e compreensível;
- formato adequado de User Story;
- prioridade definida;
- valor de negócio identificado;
- critérios de aceitação definidos;
- regras de negócio identificadas;
- cenário válido previsto;
- cenário inválido previsto, quando aplicável;
- dúvidas importantes esclarecidas;
- dependências identificadas;
- tarefas de desenvolvimento definidas;
- viabilidade para desenvolvimento dentro da Sprint;
- possibilidade de demonstração no VisuAlg sem alteração do código.

### Situação atual do DoR

As User Stories já possuem descrição, critérios de aceitação, regras de negócio
e cenários previstos.

Entretanto, a prioridade ainda depende da definição do cliente/P2.

Por esse motivo, a verificação definitiva do DoR ocorrerá durante a Sprint Planning,
após a priorização.

---

## 8. Definition of Done

Uma User Story somente poderá ser considerada concluída quando atender aos
critérios estabelecidos no documento:

```text
docs/sprint-1/DoD.md
```

Entre os principais critérios estão:

- funcionalidade implementada no VisuAlg;
- algoritmo executando corretamente;
- critérios de aceitação atendidos;
- regras de negócio respeitadas;
- cenário válido testado;
- cenário inválido testado, quando aplicável;
- entradas inválidas tratadas corretamente;
- mensagens claras para o usuário;
- possibilidade de demonstração sem alterar o código;
- código versionado no GitHub;
- commits seguindo o padrão definido;
- documentação atualizada;
- cenários de teste registrados;
- funcionalidade integrada ao incremento da Sprint;
- funcionalidade pronta para apresentação na Sprint Review.

---

## 9. Cenários de teste

Os cenários de teste detalhados da Sprint 1 estão documentados em:

```text
docs/sprint-1/testes.md
```

Entre os principais cenários previstos estão:

| Cenário | Descrição |
|---|---|
| CT01 | Plantão com cobertura mínima adequada |
| CT02 | Falta de Pediatra |
| CT03 | Quantidade negativa |
| CT04 | Opção de turno inválida |
| CT05 | Cobertura acima do mínimo |
| CT06 | Falta de Clínico Geral |
| CT07 | Falta de Cirurgião |
| CT08 | Quantidade exatamente no limite máximo |
| CT09 | Quantidade superior ao limite máximo |
| CT10 | Mais de uma especialidade com cobertura insuficiente |

Os cenários CT08 e CT09 permanecem dependentes da definição interna do limite
máximo pela equipe e da posterior validação pelo cliente/P2.

### Demonstração na Sprint Review

A equipe deverá estar preparada para demonstrar pelo menos:

1. um plantão que atende à cobertura mínima;
2. um plantão com falta de profissional de uma especialidade;
3. uma entrada de quantidade impossível;
4. uma escolha de turno inválida.

Os cenários deverão ser executados diretamente no VisuAlg por meio da alteração
dos dados de entrada, sem necessidade de modificar o código-fonte entre as demonstrações.

---

## 10. Pendências antes da finalização do Sprint Backlog

Antes que o Sprint Backlog seja considerado definitivo, permanecem as seguintes pendências:

- [ ] cliente/P2 definir a ordem de prioridade das sete User Stories;
- [ ] equipe registrar no Product Backlog a ordem definida pelo cliente/P2;
- [ ] equipe confirmar quais User Stories serão selecionadas para desenvolvimento;
- [ ] equipe ordenar os itens selecionados de acordo com a prioridade;
- [ ] equipe revisar a decomposição das histórias em tarefas;
- [ ] equipe realizar as estimativas das tarefas;
- [ ] equipe confirmar que as histórias selecionadas atendem ao DoR;
- [ ] equipe definir internamente um valor máximo plausível de profissionais;
- [ ] equipe justificar o valor máximo escolhido;
- [ ] proposta do limite máximo ser apresentada ao cliente/P2;
- [ ] cliente/P2 validar ou solicitar alteração do limite máximo.

---

## 11. Atualização após a Sprint Planning

Após a Sprint Planning, esta seção deverá registrar a composição definitiva
do Sprint Backlog.

A tabela abaixo não deverá ser preenchida com prioridades presumidas pela equipe.

A ordem deverá refletir a priorização realizada pelo cliente/P2.

| Ordem | ID | User Story | Prioridade definida pelo cliente/P2 | Status |
|---:|---|---|---|---|
| 1 | A definir | A definir | A definir | Pendente |
| 2 | A definir | A definir | A definir | Pendente |
| 3 | A definir | A definir | A definir | Pendente |
| 4 | A definir | A definir | A definir | Pendente |
| 5 | A definir | A definir | A definir | Pendente |
| 6 | A definir | A definir | A definir | Pendente |
| 7 | A definir | A definir | A definir | Pendente |

Após a definição do cliente/P2, a equipe deverá atualizar:

- a ordem das User Stories;
- a seleção definitiva;
- as tarefas da Sprint;
- as estimativas;
- o status dos itens.

---

## 12. Relação com outros documentos

O Sprint Backlog deverá permanecer alinhado aos seguintes documentos:

### Product Backlog

```text
docs/backlog/product-backlog.md
```

Contém as User Stories, critérios de aceitação, regras de negócio e prioridades.

### Definition of Ready

```text
docs/sprint-1/DoR.md
```

Define os critérios necessários para uma User Story estar pronta para desenvolvimento.

### Definition of Done

```text
docs/sprint-1/DoD.md
```

Define os critérios necessários para uma User Story ser considerada concluída.

### Cenários de Teste

```text
docs/sprint-1/testes.md
```

Contém os cenários utilizados para verificar o comportamento do sistema.

### Registro de Decisões

```text
docs/sprint-1/decisoes.md
```

Contém as principais decisões de negócio e decisões técnicas da Sprint.

---

## 13. Status geral

**Sprint Backlog:** Em preparação.

### Motivo

A estrutura inicial, as User Stories candidatas e as tarefas preliminares já estão documentadas.

Entretanto, a composição definitiva depende da priorização das User Stories pelo cliente/P2 e da realização da Sprint Planning.

Nenhuma prioridade deverá ser inventada ou presumida pela equipe.

Após a definição do cliente/P2, este documento deverá ser atualizado para representar
o Sprint Backlog definitivo da Sprint 1.
