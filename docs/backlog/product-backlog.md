# Product Backlog

## Priorização do Product Backlog

A ordem de prioridade das User Stories será definida pelo cliente/P2.

Durante a reunião de validação, as sete histórias da Sprint 1 serão
apresentadas ao cliente para que ele determine sua ordem de prioridade.

| ID | User Story | Prioridade | Sprint |
|---|---|---|---|
| US01 | Selecionar o turno do plantão | A definir pelo cliente/P2 | Sprint 1 |
| US02 | Informar a quantidade de profissionais | A definir pelo cliente/P2 | Sprint 1 |
| US03 | Validar as quantidades informadas | A definir pelo cliente/P2 | Sprint 1 |
| US04 | Verificar a cobertura mínima do plantão | A definir pelo cliente/P2 | Sprint 1 |
| US05 | Informar se o plantão pode ser publicado | A definir pelo cliente/P2 | Sprint 1 |
| US06 | Informar o motivo da reprovação do plantão | A definir pelo cliente/P2 | Sprint 1 |
| US07 | Tratar escolhas inválidas | A definir pelo cliente/P2 | Sprint 1 |

### Critério de Priorização

A priorização das User Stories ainda não foi definida.

Conforme orientação do cliente/P2, as sete histórias da Sprint 1 serão
apresentadas para que ele determine a ordem de prioridade de acordo com
o valor de negócio.

Até essa definição, todas as User Stories permanecerão com a prioridade
indicada como **"A definir pelo cliente/P2"**.

---

# User Stories da Sprint 1

## US01 — Selecionar o turno do plantão

Como coordenador de escala,
quero selecionar o turno que desejo analisar,
para verificar a cobertura do plantão correspondente.

**Prioridade:** A definir pelo cliente/P2

### Critérios de Aceitação

**Cenário válido**

Dado que o sistema apresente as opções Manhã, Tarde e Noite,  
Quando o coordenador selecionar uma das opções válidas pelo teclado,  
Então o sistema deve reconhecer corretamente o turno escolhido e prosseguir com a análise.

**Cenário inválido**

Dado que o sistema apresente as opções de turno,  
Quando o coordenador informar uma opção diferente de Manhã, Tarde ou Noite,  
Então o sistema deve informar claramente que a escolha é inválida e não utilizar essa opção na análise.

**Demonstração no VisuAlg**

Dado que o programa esteja sendo executado no VisuAlg,  
Quando forem testados um turno válido e uma opção inválida,  
Então os dois cenários devem ser demonstráveis apenas alterando os dados de entrada, sem modificar o código.

---

## US02 — Informar a quantidade de profissionais

Como coordenador de escala,
quero informar a quantidade de profissionais disponíveis em cada especialidade,
para que o sistema consiga analisar a cobertura do plantão.

**Prioridade:** A definir pelo cliente/P2

### Critérios de Aceitação

**Cenário válido**

Dado que um turno válido tenha sido selecionado,  
Quando o coordenador informar as quantidades de Clínicos Gerais, Pediatras e Cirurgiões,  
Então o sistema deve registrar os valores informados e utilizá-los na análise da cobertura.

**Cenário inválido**

Dado que o sistema esteja solicitando a quantidade de profissionais,  
Quando for informado um valor considerado inválido pelas regras da Sprint,  
Então o sistema não deve utilizar esse valor como uma quantidade válida na análise.

**Demonstração no VisuAlg**

Dado que o programa esteja sendo executado no VisuAlg,  
Quando forem informados diferentes valores pelo teclado,  
Então os cenários devem ser demonstráveis sem qualquer alteração no código.

---

## US03 — Validar as quantidades informadas

Como coordenador de escala,
quero que o sistema valide as quantidades de profissionais informadas,
para evitar que dados impossíveis sejam utilizados na análise do plantão.

**Prioridade:** A definir pelo cliente/P2

### Critérios de Aceitação

**Cenário válido**

Dado que o coordenador informe uma quantidade dentro do intervalo permitido,  
Quando o valor for validado pelo sistema,  
Então ele deve ser aceito e utilizado na análise do plantão.

**Cenário inválido**

Dado que o coordenador informe uma quantidade negativa ou, após a definição e validação do limite máximo, uma quantidade superior a esse limite,  
Quando o sistema realizar a validação,  
Então deve informar claramente que o valor é inválido e impedir que ele seja utilizado na análise.

**Demonstração no VisuAlg**

Dado que o programa esteja sendo executado no VisuAlg,  
Quando forem utilizados valores válidos e inválidos,  
Então os dois comportamentos devem ser demonstráveis apenas pela alteração dos dados de entrada, sem modificar o código.

### Definição do limite máximo

A equipe ainda está definindo internamente um valor máximo plausível de profissionais por especialidade em um único plantão.

Enquanto esse valor não for definido, ele será representado temporariamente por **X** na documentação.

#### Justificativa

O Hospital Santa Aurora é apresentado como uma instituição de médio porte e,
na Sprint 1, a cobertura mínima exigida por plantão é de:

- 2 Clínicos Gerais;
- 1 Pediatra;
- 1 Cirurgião.

Quantidades excessivamente altas podem representar erros de digitação.

Por esse motivo, a equipe deverá definir um valor máximo plausível, com uma
justificativa baseada no contexto do hospital e nas quantidades mínimas exigidas.

Após a definição interna da equipe, o valor proposto será apresentado ao
cliente/P2 para validação antes de ser considerado uma regra definitiva do sistema.

**Valor máximo atual:** X profissionais por especialidade.

**Status:** Em definição pela equipe.

---

## US04 — Verificar a cobertura mínima do plantão

Como coordenador de escala,
quero que o sistema compare a quantidade de profissionais disponíveis com a cobertura mínima exigida,
para saber se o plantão possui cobertura adequada.

**Prioridade:** A definir pelo cliente/P2

### Critérios de Aceitação

**Cenário válido**

Dado que tenham sido informados pelo menos 2 Clínicos Gerais, 1 Pediatra e 1 Cirurgião,  
Quando o sistema verificar a cobertura mínima,  
Então deve identificar que a cobertura do plantão foi atingida.

**Cenário inválido**

Dado que pelo menos uma das especialidades esteja abaixo da quantidade mínima exigida,  
Quando o sistema verificar a cobertura,  
Então deve identificar que a cobertura mínima do plantão não foi atingida.

**Demonstração no VisuAlg**

Dado que o programa esteja sendo executado no VisuAlg,  
Quando forem informadas quantidades suficientes e insuficientes,  
Então ambos os resultados devem ser demonstráveis sem alteração do código.

---

## US05 — Informar se o plantão pode ser publicado

Como coordenador de escala,
quero receber uma conclusão sobre a possibilidade de publicação do plantão,
para saber se a escala está apta para publicação.

**Prioridade:** A definir pelo cliente/P2

### Critérios de Aceitação

**Cenário válido**

Dado que todas as especialidades atendam à cobertura mínima,  
Quando a análise do plantão for concluída,  
Então o sistema deve informar claramente que o plantão pode ser publicado.

**Cenário inválido**

Dado que pelo menos uma especialidade não atenda à cobertura mínima,  
Quando a análise do plantão for concluída,  
Então o sistema deve informar claramente que o plantão não pode ser publicado.

**Demonstração no VisuAlg**

Dado que o programa esteja sendo executado no VisuAlg,  
Quando forem analisados um plantão aprovado e um plantão reprovado,  
Então ambas as conclusões devem ser demonstráveis sem alteração do código.

---

## US06 — Informar o motivo da reprovação do plantão

Como coordenador de escala,
quero saber o motivo pelo qual um plantão não pode ser publicado,
para identificar qual especialidade apresenta cobertura insuficiente.

**Prioridade:** A definir pelo cliente/P2

### Critérios de Aceitação

**Cenário válido**

Dado que uma ou mais especialidades estejam abaixo da cobertura mínima,  
Quando o plantão for considerado inadequado para publicação,  
Então o sistema deve informar qual especialidade está insuficiente, juntamente com a quantidade necessária e a quantidade informada.

**Cenário inválido**

Dado que todas as especialidades atendam à cobertura mínima,  
Quando a análise for concluída,  
Então o sistema não deve apresentar uma especialidade como insuficiente.

**Demonstração no VisuAlg**

Dado que o programa esteja sendo executado no VisuAlg,  
Quando forem utilizados dados que provoquem aprovação e reprovação,  
Então os resultados e seus respectivos motivos devem ser demonstráveis sem alteração do código.

---

## US07 — Tratar escolhas inválidas

Como coordenador de escala,
quero ser informado quando realizar uma escolha inválida,
para evitar que o sistema faça uma análise utilizando uma opção incorreta.

**Prioridade:** A definir pelo cliente/P2

### Critérios de Aceitação

**Cenário válido**

Dado que o sistema apresente as opções disponíveis,  
Quando o coordenador selecionar uma opção válida,  
Então o sistema deve aceitar a escolha e continuar normalmente a execução.

**Cenário inválido**

Dado que o sistema apresente as opções disponíveis,  
Quando o coordenador selecionar uma opção inexistente,  
Então o sistema deve informar claramente que a escolha é inválida e impedir que ela seja utilizada na análise.

**Demonstração no VisuAlg**

Dado que o programa esteja sendo executado no VisuAlg,  
Quando forem realizadas uma escolha válida e uma escolha inválida,  
Então ambos os comportamentos devem ser demonstráveis sem modificar o código.

---

# Regras de Negócio da Sprint 1

## RN01 — Turnos

O hospital trabalha com três turnos:

- Manhã;
- Tarde;
- Noite.

---

## RN02 — Especialidades

Cada plantão considera três especialidades:

- Clínico Geral;
- Pediatra;
- Cirurgião.

---

## RN03 — Cobertura mínima

Cada turno deve possuir no mínimo:

- 2 Clínicos Gerais;
- 1 Pediatra;
- 1 Cirurgião.

---

## RN04 — Publicação do plantão

Um plantão que não atenda à cobertura mínima não pode ser publicado.

---

## RN05 — Motivo da reprovação

Quando um plantão não puder ser publicado, o sistema deve informar
o motivo da reprovação.

---

## RN06 — Quantidades negativas

Quantidades negativas de profissionais são impossíveis e não devem
ser aceitas pelo sistema.

A quantidade `0` é válida e pode representar a ausência de profissionais
disponíveis em determinada especialidade.

---

## RN07 — Quantidade máxima

Quantidades excessivamente altas também devem ser tratadas como possíveis
erros de digitação.

A equipe ainda está definindo internamente um valor máximo plausível de
profissionais por especialidade.

Enquanto esse valor não for definido, ele será representado temporariamente
por **X**.

Após a definição interna, a proposta deverá ser apresentada ao cliente/P2
para validação.

**Valor máximo:** X profissionais por especialidade.

**Status:** Em definição pela equipe e posteriormente sujeito à validação do cliente/P2.

---

## RN08 — Interação com o sistema

A coordenação hospitalar deve conseguir operar o sistema utilizando
teclado e console.

Não deve ser necessário alterar o código para escolher o turno ou
realizar uma operação.

---

# Cenários de Teste da Sprint 1

Os seguintes cenários deverão ser preparados para testar e demonstrar
o funcionamento do sistema.

---

## CT01 — Plantão com cobertura adequada

### Entrada de exemplo

Turno: Manhã

- Clínico Geral: 2
- Pediatra: 1
- Cirurgião: 1

### Resultado esperado

O sistema deve informar que o plantão possui cobertura adequada
e pode ser publicado.

---

## CT02 — Falta de profissional

### Entrada de exemplo

Turno: Manhã

- Clínico Geral: 2
- Pediatra: 0
- Cirurgião: 1

### Resultado esperado

O sistema deve informar que o plantão não pode ser publicado.

Também deve informar que existe quantidade insuficiente de Pediatras.

---

## CT03 — Quantidade impossível

### Entrada de exemplo

Clínico Geral: -1

### Resultado esperado

O sistema deve rejeitar ou sinalizar o valor informado e apresentar
uma mensagem indicando que a quantidade é inválida.

---

## CT04 — Opção inválida

### Entrada de exemplo

O usuário seleciona uma opção que não corresponde a nenhuma operação
válida do sistema.

### Resultado esperado

O sistema deve identificar a escolha como inválida e apresentar
uma mensagem de erro.

---

# Fora do Escopo da Sprint 1

As seguintes funcionalidades não fazem parte da Sprint 1:

- Cadastro nominal de médicos;
- Cadastro completo de profissionais;
- Análise de mais de um plantão por execução;
- Persistência de dados entre diferentes execuções;
- Salvamento dos dados do sistema;
- Interface gráfica;
- Uso obrigatório de vetores ou matrizes antes desse conteúdo ser trabalhado na disciplina.

---

# Funcionalidades Opcionais

Permitir que o usuário realize uma nova análise sem precisar reiniciar
o programa é uma melhoria bem-vinda.

Porém, essa funcionalidade não é obrigatória antes de o conteúdo de
estruturas de repetição ser trabalhado na disciplina.

---

# Itens pendentes de validação com o cliente/P2

Após os esclarecimentos realizados com o cliente/P2, permanecem pendentes os seguintes pontos:

- definição da ordem de prioridade das sete User Stories da Sprint 1 pelo cliente/P2;
- definição interna, pela equipe, de um valor máximo plausível de profissionais por especialidade, atualmente representado por **X**;
- validação desse limite máximo pelo cliente/P2 após a equipe apresentar sua proposta;
- validação da versão revisada dos critérios de aceitação das User Stories.

Os seguintes pontos já foram esclarecidos pelo cliente/P2:

- o resultado final deve informar o turno analisado;
- o sistema deve informar se a cobertura mínima foi atingida ou não;
- quando houver cobertura insuficiente, deve ser informada a especialidade responsável;
- a conclusão deve indicar claramente se o plantão pode ou não ser publicado;
- informar exatamente quantos profissionais faltam é opcional;
- entradas inválidas nunca podem ser utilizadas como dados válidos;
- a forma de tratamento da entrada inválida é uma decisão técnica da equipe;
- realizar uma nova análise sem reiniciar o programa não é requisito obrigatório da Sprint 1.

---

# Sprint 2

As necessidades da Sprint 2 ainda não foram disponibilizadas.

O Product Backlog será atualizado após a Sprint Review da Sprint 1,
quando o cliente/P2 apresentar as próximas necessidades.

---

# Sprint 3

As necessidades da Sprint 3 ainda não foram disponibilizadas.

O Product Backlog será atualizado conforme a evolução do projeto e
os feedbacks apresentados pelo cliente/P2.

---
