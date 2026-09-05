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

Decisões que ainda dependem de definição ou confirmação devem permanecer identificadas como pendentes até que sejam formalmente estabelecidas.

---

## 2. Estados das decisões

As decisões poderão possuir os seguintes estados:

| Estado | Significado |
|---|---|
| Confirmada | Decisão definida pelo cliente, pelo escopo do projeto ou já validada formalmente |
| Decisão técnica | Escolha realizada pela equipe para implementar uma necessidade |
| Em definição | Decisão que ainda está sendo discutida internamente pela equipe |
| Pendente de validação | Proposta definida pela equipe, mas que ainda precisa ser validada pelo cliente/P2 |
| Revisada | Decisão anteriormente registrada que foi posteriormente modificada |

---

# 3. Decisões Registradas

## DEC01 — Uso do VisuAlg

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

---

## DEC02 — Interface textual

**Categoria:** Interface  
**Origem:** Restrição do projeto  
**Status:** Confirmada

### Decisão

O MedShift utilizará uma interface textual executada em console.

A interação com o sistema será realizada através do teclado.

### Justificativa

A interface gráfica não faz parte dos requisitos do projeto.

O foco da Sprint está na lógica, nas regras implementadas e na capacidade do sistema de apresentar um diagnóstico útil ao usuário.

### Impactos

O sistema deverá:

- apresentar instruções claras no console;
- permitir a seleção das operações sem necessidade de alterar o código;
- solicitar os dados necessários através do teclado;
- apresentar mensagens compreensíveis ao usuário;
- tratar opções inválidas.

---

## DEC03 — Análise de um plantão por execução

**Categoria:** Escopo  
**Origem:** Requisito da Sprint 1  
**Status:** Confirmada

### Decisão

Durante a Sprint 1, cada execução do sistema poderá analisar um único plantão.

Após a conclusão da análise, uma nova execução poderá ser iniciada para analisar outro plantão.

### Justificativa

A realização de várias análises em uma única execução não é requisito obrigatório da Sprint 1.

O cliente/P2 informou que essa funcionalidade é bem-vinda caso a equipe já domine estruturas de repetição, mas sua ausência não compromete o atendimento do escopo atual.

### Impactos

Nesta Sprint não será obrigatório:

- repetir automaticamente a análise;
- manter vários plantões em memória;
- armazenar histórico entre execuções.

---

## DEC04 — Turnos utilizados pelo sistema

**Categoria:** Regra de negócio  
**Origem:** Cliente/P2  
**Status:** Confirmada

### Decisão

O hospital trabalha com três turnos:

1. Manhã;
2. Tarde;
3. Noite.

### Justificativa

Os três turnos fazem parte das regras de negócio informadas para a Sprint 1.

### Impactos

Toda análise deverá estar associada a um desses três turnos.

Uma opção diferente das opções disponíveis deverá ser considerada inválida.

---

## DEC05 — Representação dos turnos no menu

**Categoria:** Decisão técnica  
**Origem:** Equipe  
**Status:** Decisão técnica

### Decisão

Os turnos serão representados no sistema utilizando opções numéricas.

Padrão adotado:

```text
1 - Manhã
2 - Tarde
3 - Noite
```

### Justificativa

A utilização de opções numéricas simplifica a interação pelo console e facilita o tratamento da escolha no VisuAlg.

### Impactos

O usuário deverá conseguir escolher o turno pelo teclado sem qualquer alteração no código-fonte.

---

## DEC06 — Definição do limite máximo de profissionais

**Categoria:** Regra em definição  
**Origem:** Equipe, com posterior validação do cliente/P2  
**Status:** Em definição

### Decisão

A equipe deverá definir um valor máximo plausível de profissionais por especialidade em um único plantão.

Enquanto o valor não for definido internamente, ele será representado temporariamente por **X** na documentação.

Após a definição da equipe, a proposta será apresentada ao cliente/P2 para validação antes de ser considerada uma regra definitiva do sistema.

### Justificativa

Quantidades absurdamente altas podem representar erros de digitação e não devem ser aceitas automaticamente como dados válidos.

O cliente/P2 determinou que a equipe deve propor um limite plausível e justificar essa escolha.

### Impactos

Até a definição e validação do valor:

- **X** não representa um número definitivo;
- o limite não deverá ser tratado como regra aprovada;
- os documentos deverão deixar claro que o valor está em definição.

Depois que a equipe definir a proposta, esta decisão deverá ser atualizada para **Pendente de validação**.

Após a aprovação do cliente/P2, deverá ser atualizada para **Confirmada**.

---

## DEC07 — Tratamento de entradas inválidas

**Categoria:** Decisão técnica  
**Origem:** Equipe, com base na necessidade informada pelo cliente/P2  
**Status:** Decisão técnica

### Decisão

Quando o usuário informar um dado inválido, o sistema deverá apresentar uma mensagem clara de erro, impedir que esse dado seja utilizado na análise e encerrar a execução atual.

Nesta Sprint, o sistema não será obrigado a solicitar uma nova digitação após a identificação do erro.

### Exemplos de entradas inválidas

- quantidade negativa de profissionais;
- quantidade superior ao limite máximo, após esse limite ser definido e validado;
- opção de turno inexistente.

A quantidade **0 não é inválida**.

Ela pode representar a ausência de profissionais disponíveis em determinada especialidade e deverá participar normalmente da análise de cobertura.

### Justificativa

O cliente/P2 determinou que nenhum dado inválido pode ser aceito como válido e que a coordenação precisa compreender claramente o que foi informado de forma incorreta.

A forma exata de tratamento foi deixada como decisão técnica da equipe.

### Impactos

Ao identificar uma entrada inválida:

1. o sistema exibirá uma mensagem explicando o erro;
2. o valor não será utilizado na análise;
3. a execução atual será encerrada;
4. para realizar uma nova análise, o usuário deverá executar novamente o programa.

### Exemplo

```text
ERRO: quantidade inválida.

A quantidade de profissionais não pode ser negativa.

Análise encerrada.
```

---

## DEC08 — Informações obrigatórias no resultado final

**Categoria:** Regra de apresentação  
**Origem:** Cliente/P2 e decisão complementar da equipe  
**Status:** Confirmada

### Decisão

Ao final de uma análise concluída normalmente, o sistema deverá apresentar de forma clara:

- o turno analisado;
- se a cobertura mínima foi atingida ou não;
- a especialidade ou as especialidades com cobertura insuficiente, quando houver;
- a conclusão indicando se o plantão pode ou não ser publicado.

A equipe também decidiu manter a exibição da quantidade necessária e da quantidade informada para cada especialidade insuficiente.

### Justificativa

O cliente/P2 informou que a coordenação precisa compreender claramente o resultado da análise e, quando o plantão não puder ser publicado, identificar qual especialidade apresenta cobertura insuficiente.

A exibição das quantidades necessária e informada acrescenta detalhe ao diagnóstico.

### Impactos

O resultado não deverá apresentar apenas uma mensagem genérica como:

```text
Plantão inválido.
```

ou:

```text
Plantão não pode ser publicado.
```

O sistema deverá apresentar informações suficientes para que a coordenação compreenda o resultado.

### Exemplo de plantão aprovado

```text
===== RESULTADO DA ANÁLISE =====

Turno analisado: MANHÃ

Cobertura mínima: ATINGIDA

Conclusão:
Plantão PODE ser publicado.
```

### Exemplo de plantão reprovado

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
```

Caso mais de uma especialidade esteja abaixo da cobertura mínima, o sistema deverá informar as especialidades insuficientes.

---

## DEC09 — Separação entre verificação de cobertura e decisão de publicação

**Categoria:** Organização das responsabilidades do produto  
**Origem:** Equipe, após esclarecimento solicitado pelo cliente/P2  
**Status:** Confirmada pela equipe

### Decisão

A equipe manterá separadas as responsabilidades da **US04 — Verificar a cobertura mínima do plantão** e da **US05 — Informar se o plantão pode ser publicado**.

A US04 será responsável por comparar as quantidades de profissionais informadas com os valores mínimos exigidos para cada especialidade e determinar se a cobertura mínima foi atingida.

A US05 utilizará o resultado dessa verificação para apresentar ao coordenador a conclusão de negócio: o plantão pode ou não ser publicado.

### Justificativa

As duas User Stories representam etapas diferentes do processamento.

A US04 responde à pergunta:

> A cobertura mínima foi atingida?

A US05 responde à pergunta:

> Com base nessa verificação, o plantão pode ser publicado?

Essa separação mantém cada User Story com uma responsabilidade específica e facilita a compreensão do fluxo do sistema.

### Exemplo

Considere:

- Clínicos Gerais: 2;
- Pediatras: 0;
- Cirurgiões: 1.

A US04 identifica que a cobertura mínima não foi atingida, pois a quantidade de Pediatras está abaixo do mínimo exigido.

A US05 utiliza esse resultado e conclui que o plantão não pode ser publicado.

### Impactos

A lógica do sistema deverá seguir, de forma conceitual, esta sequência:

1. receber e validar os dados de entrada;
2. verificar a cobertura mínima de cada especialidade;
3. determinar se a cobertura do plantão foi atingida;
4. apresentar a conclusão sobre a publicação do plantão;
5. quando houver reprovação, apresentar o motivo ao usuário.

---

# 4. Pendências relacionadas às decisões

No momento, permanece pendente:

- definição interna do valor máximo plausível de profissionais por especialidade, representado temporariamente por **X**;
- posterior validação desse valor com o cliente/P2.

Após a equipe definir o valor máximo, a DEC06 deverá ser atualizada para registrar a proposta concreta.

Depois que o cliente/P2 validar ou solicitar alteração da proposta, o status da decisão deverá ser atualizado.
