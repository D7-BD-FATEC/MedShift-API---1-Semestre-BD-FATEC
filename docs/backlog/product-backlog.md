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

A priorização do Product Backlog foi definida considerando principalmente
o valor de negócio entregue por cada User Story para o objetivo da Sprint 1.

As histórias **US04, US05 e US06** receberam prioridade **Crítica**, pois
estão diretamente relacionadas à principal necessidade apresentada pelo
cliente: analisar a cobertura de um plantão, determinar se ele pode ser
publicado e informar claramente o motivo quando a publicação não for possível.

As histórias **US01, US02 e US03** receberam prioridade **Alta**, pois
fornecem as informações e validações necessárias para que a análise do
plantão seja realizada corretamente.

A **US07** recebeu prioridade **Média**, pois o tratamento de escolhas
inválidas é importante para a confiabilidade e facilidade de uso do sistema,
mas possui menor valor de negócio quando comparado à análise da cobertura
e à decisão de publicação do plantão.

> **Observação:** a prioridade representa o valor de negócio da User Story
> e não necessariamente a ordem técnica de implementação. Algumas histórias
> de prioridade Alta podem precisar ser desenvolvidas antes das histórias
> de prioridade Crítica por serem dependências necessárias para o funcionamento
> da análise.

---

# User Stories da Sprint 1

## US01 — Selecionar o turno do plantão

**Como** coordenador de escala,  
**quero** selecionar o turno que desejo analisar,  
**para** verificar a cobertura do plantão correspondente.

**Prioridade:** 

### Critérios de Aceitação

- O sistema deve permitir a escolha entre os turnos:
  - Manhã;
  - Tarde;
  - Noite.
- A escolha deve ser realizada pelo teclado.
- O usuário não deve precisar alterar o código para selecionar o turno.
- O sistema deve reconhecer corretamente o turno escolhido.
- Uma opção de turno inválida deve ser identificada pelo sistema.
- O resultado deve ser demonstrável no VisuAlg sem alteração do código.

---

## US02 — Informar a quantidade de profissionais

**Como** coordenador de escala,  
**quero** informar a quantidade de profissionais disponíveis em cada especialidade,  
**para** que o sistema consiga analisar a cobertura do plantão.

**Prioridade:** 

### Critérios de Aceitação

O sistema deve solicitar a quantidade de profissionais disponíveis para:

- Clínico Geral;
- Pediatra;
- Cirurgião.

Além disso:

- Os valores devem ser informados pelo teclado.
- Os valores informados devem ser utilizados na análise do plantão.
- O usuário não deve precisar modificar o código para informar os dados.
- O resultado deve ser demonstrável no VisuAlg sem alteração do código.

---

## US03 — Validar as quantidades informadas

**Como** coordenador de escala,  
**quero** que o sistema valide as quantidades de profissionais informadas,  
**para** evitar que dados impossíveis sejam utilizados na análise do plantão.

**Prioridade:** 

### Critérios de Aceitação

- O sistema não deve aceitar quantidades negativas de profissionais.
- Caso uma quantidade negativa seja informada, o sistema deve sinalizar o erro.
- Quantidades absurdamente altas também devem ser consideradas inválidas.
- O sistema deve informar ao usuário quando uma quantidade for considerada inválida.
- O resultado deve ser demonstrável no VisuAlg sem alteração do código.


**Valor máximo permitido: (Definir qual o valor max e o motivo).**

---

## US04 — Verificar a cobertura mínima do plantão

**Como** coordenador de escala,  
**quero** verificar se o plantão possui a quantidade mínima de profissionais,  
**para** saber se sua cobertura está adequada.

**Prioridade:** 

### Regras de Cobertura

A cobertura mínima exigida é:

| Especialidade | Manhã | Tarde | Noite |
|---|---:|---:|---:|
| Clínico Geral | 2 | 2 | 2 |
| Pediatra | 1 | 1 | 1 |
| Cirurgião | 1 | 1 | 1 |

### Critérios de Aceitação

- O plantão deve possuir pelo menos 2 Clínicos Gerais.
- O plantão deve possuir pelo menos 1 Pediatra.
- O plantão deve possuir pelo menos 1 Cirurgião.
- O sistema deve comparar as quantidades informadas com os valores mínimos.
- Caso todas as quantidades mínimas sejam atendidas, o plantão deve ser considerado coberto.
- Caso alguma quantidade mínima não seja atendida, o plantão deve ser considerado inadequado.
- A verificação deve funcionar para Manhã, Tarde e Noite.
- O resultado deve ser demonstrável no VisuAlg sem alteração do código.

---

## US05 — Informar se o plantão pode ser publicado

**Como** coordenador de escala,  
**quero** saber se o plantão pode ou não ser publicado,  
**para** evitar a publicação de uma escala com cobertura inadequada.

**Prioridade:** 

### Critérios de Aceitação

- O sistema deve analisar a cobertura mínima do plantão.
- Caso todas as especialidades atendam à cobertura mínima, o sistema deve informar que o plantão pode ser publicado.
- Caso alguma especialidade não atenda à cobertura mínima, o sistema deve informar que o plantão não pode ser publicado.
- A conclusão deve ser apresentada de forma clara na tela.
- O resultado deve ser demonstrável no VisuAlg sem alteração do código.

---

## US06 — Informar o motivo da reprovação

**Como** coordenador de escala,  
**quero** visualizar o motivo pelo qual um plantão não pode ser publicado,  
**para** identificar rapidamente o problema de cobertura.

**Prioridade:** 

### Critérios de Aceitação

- Quando o plantão não puder ser publicado, o sistema deve informar o motivo.
- O sistema deve indicar qual especialidade possui cobertura insuficiente.
- A mensagem deve ser apresentada na tela.
- O sistema não deve apenas informar que existe um erro.
- A informação apresentada deve ajudar a coordenação a identificar o problema.
- O resultado deve ser demonstrável no VisuAlg sem alteração do código.

### Exemplo de resultado esperado

Plantão NÃO pode ser publicado.

Motivo:

Quantidade insuficiente de Pediatras.

Necessário: 1  
Informado: 0

> Observação: este é apenas um exemplo de apresentação.
> O formato final da mensagem poderá ser validado com o cliente/P2.

---

## US07 — Tratar escolhas inválidas

**Como** coordenador de escala,  
**quero** que escolhas inválidas sejam identificadas pelo sistema,  
**para** evitar operações incorretas durante a utilização do programa.

**Prioridade:** 

### Critérios de Aceitação

- O sistema deve identificar opções inválidas na seleção realizada pelo usuário.
- Uma opção inválida não deve ser considerada uma operação válida.
- O sistema deve apresentar uma mensagem informando que a opção escolhida é inválida.
- O usuário não deve precisar alterar o código para realizar uma operação válida.
- O resultado deve ser demonstrável no VisuAlg sem alteração do código.

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

---

## RN07 — Quantidade máxima

Quantidades absurdamente altas também devem ser tratadas como possíveis
erros de digitação.

A equipe deverá propor um valor máximo plausível e validá-lo com o
cliente/P2.

**Valor máximo: A DEFINIR.**

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

# Itens que precisam ser validados com o cliente/P2

Durante a Sprint, a equipe deverá esclarecer com o cliente:

- Qual deve ser a quantidade máxima plausível de médicos por especialidade;
- Como o cliente prefere visualizar o resultado final;
- Como devem ser apresentadas as mensagens de erro;
- Se existe alguma preferência na organização das opções do sistema;
- Se os critérios de aceite propostos pela equipe representam corretamente a necessidade do cliente.

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

