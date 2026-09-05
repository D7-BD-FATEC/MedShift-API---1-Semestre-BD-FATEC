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

# 5. Tarefas preliminares

As tarefas abaixo representam uma decomposição inicial das User Stories.

Elas poderão ser revisadas durante a Sprint Planning após a definição
das prioridades.

---

## US01 — Selecionar o turno do plantão

### Tarefas

- [ ] Criar o menu de seleção de turno.
- [ ] Apresentar as opções Manhã, Tarde e Noite.
- [ ] Ler a opção escolhida pelo teclado.
- [ ] Identificar o turno correspondente à opção selecionada.
- [ ] Garantir que a escolha possa ser realizada sem alterar o código.
- [ ] Testar uma opção válida de turno.

### Dependências

Nenhuma dependência funcional obrigatória.

---

## US02 — Informar a quantidade de profissionais

### Tarefas

- [ ] Solicitar a quantidade de Clínicos Gerais.
- [ ] Solicitar a quantidade de Pediatras.
- [ ] Solicitar a quantidade de Cirurgiões.
- [ ] Armazenar os valores informados.
- [ ] Garantir que os dados sejam fornecidos pelo teclado.
- [ ] Preparar os valores para utilização na análise de cobertura.

### Dependências

- US01 — Selecionar o turno do plantão.

---

## US03 — Validar as quantidades informadas

### Tarefas

- [ ] Verificar se alguma quantidade informada é negativa.
- [ ] Aceitar o valor 0 como uma entrada válida.
- [ ] Apresentar uma mensagem clara quando uma quantidade for inválida.
- [ ] Impedir que valores inválidos sejam utilizados na análise.
- [ ] Encerrar a análise atual quando uma quantidade inválida for identificada.
- [ ] Implementar a validação do limite máximo após sua definição e validação.

### Dependências

- US02 — Informar a quantidade de profissionais.
- Definição interna do limite máximo de profissionais.
- Validação posterior do limite máximo pelo cliente/P2.

### Observação

O limite máximo de profissionais ainda está em definição pela equipe.

Enquanto não houver um valor definido e validado, ele será representado
por **X** na documentação.

---

## US04 — Verificar a cobertura mínima do plantão

### Tarefas

- [ ] Comparar a quantidade de Clínicos Gerais com o mínimo de 2.
- [ ] Comparar a quantidade de Pediatras com o mínimo de 1.
- [ ] Comparar a quantidade de Cirurgiões com o mínimo de 1.
- [ ] Identificar se todas as especialidades atendem aos mínimos.
- [ ] Identificar quais especialidades estão abaixo da cobertura mínima.
- [ ] Registrar internamente o resultado da verificação.

### Dependências

- US02 — Informar a quantidade de profissionais.
- US03 — Validar as quantidades informadas.

---

## US05 — Informar se o plantão pode ser publicado

### Tarefas

- [ ] Utilizar o resultado da verificação de cobertura.
- [ ] Identificar se a cobertura mínima foi atingida.
- [ ] Informar que o plantão pode ser publicado quando todos os mínimos forem atendidos.
- [ ] Informar que o plantão não pode ser publicado quando algum mínimo não for atendido.
- [ ] Apresentar a conclusão de forma clara no console.

### Dependências

- US04 — Verificar a cobertura mínima do plantão.

---

## US06 — Informar o motivo da reprovação do plantão

### Tarefas

- [ ] Identificar a especialidade com cobertura insuficiente.
- [ ] Apresentar a especialidade responsável pela reprovação.
- [ ] Apresentar a quantidade mínima necessária.
- [ ] Apresentar a quantidade informada pelo usuário.
- [ ] Tratar o caso em que mais de uma especialidade esteja abaixo do mínimo.
- [ ] Garantir que o motivo seja apresentado junto à conclusão da análise.

### Dependências

- US04 — Verificar a cobertura mínima do plantão.
- US05 — Informar se o plantão pode ser publicado.

---

## US07 — Tratar escolhas inválidas

### Tarefas

- [ ] Identificar uma opção de turno inexistente.
- [ ] Apresentar uma mensagem clara de erro.
- [ ] Impedir que a opção inválida seja utilizada na análise.
- [ ] Encerrar a análise atual após a escolha inválida.
- [ ] Testar pelo menos uma opção inválida.

### Dependências

- US01 — Selecionar o turno do plantão.

---

# 6. Regras de negócio relacionadas

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

# 7. Definition of Ready

Antes de uma User Story entrar em desenvolvimento, ela deverá atender aos
critérios estabelecidos no documento:

```text
docs/sprint-1/DoR.md
