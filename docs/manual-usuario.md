# Manual do Usuário

## 1. Objetivo

Este documento apresenta as instruções de utilização do sistema MedShift durante a Sprint 1.

O MedShift é um sistema de apoio à análise e validação de plantões médicos, desenvolvido para auxiliar a coordenação do Hospital Santa Aurora na verificação da cobertura mínima de profissionais.

O sistema permite informar os dados de um plantão, analisar a quantidade de profissionais disponíveis e apresentar uma conclusão indicando se o plantão pode ou não ser publicado.

---

## 2. Público-alvo

O sistema é destinado à coordenação responsável pela organização e validação das escalas médicas do Hospital Santa Aurora.

O usuário não precisa possuir conhecimento de programação para utilizar o MedShift.

Todas as operações devem ser realizadas através das opções apresentadas pelo sistema no console.

---

## 3. Forma de utilização

O MedShift funciona através de uma interface textual executada no VisuAlg.

A interação ocorre utilizando o teclado.

Durante a utilização, o sistema deverá:

1. apresentar as opções disponíveis;
2. solicitar os dados necessários;
3. validar as informações inseridas;
4. analisar a cobertura do plantão;
5. apresentar o resultado da análise.

O usuário não precisa modificar o código-fonte para utilizar o sistema.

---

## 4. Inicialização

Para utilizar o MedShift:

1. abra o VisuAlg;
2. abra o arquivo principal do projeto;
3. inicie a execução do algoritmo;
4. aguarde as opções serem apresentadas no console;
5. informe os dados solicitados pelo sistema.

As instruções para preparação do ambiente estão disponíveis em:

```text
docs/manual-instalacao.md
```

---

## 5. Escopo da Sprint 1

Durante a Sprint 1, o MedShift realiza a análise de um plantão por execução.

O sistema não possui, nesta etapa:

- cadastro nominal de médicos;
- análise simultânea de vários plantões;
- armazenamento permanente dos dados;
- interface gráfica;
- continuidade automática dos dados entre execuções.

O objetivo da Sprint 1 é verificar se um determinado plantão possui cobertura mínima adequada e informar se ele pode ou não ser publicado.

---

## 6. Turnos disponíveis

O Hospital Santa Aurora trabalha com três turnos:

1. Manhã;
2. Tarde;
3. Noite.

O sistema deverá permitir que o usuário selecione um desses turnos.

Exemplo de menu:

```text
Selecione o turno:

1 - Manhã
2 - Tarde
3 - Noite
```

O usuário deverá informar a opção correspondente ao turno desejado.

Exemplo:

```text
Opção: 1
```

Nesse caso, o turno selecionado será Manhã.

---

## 7. Opção de turno inválida

Caso seja informada uma opção que não corresponda a nenhum dos turnos disponíveis, o sistema deverá informar claramente o erro.

Exemplo:

```text
Selecione o turno:

1 - Manhã
2 - Tarde
3 - Noite

Opção: 9
```

Resultado esperado:

```text
ERRO: turno inválido.

Escolha uma das opções disponíveis:
1 - Manhã
2 - Tarde
3 - Noite

Análise encerrada.
```

A opção inválida não poderá ser utilizada na análise.

Durante a Sprint 1, após a identificação desse erro, a execução atual será encerrada.

Para realizar uma nova análise, o usuário deverá executar novamente o programa.

---

## 8. Especialidades analisadas

Cada plantão é analisado considerando três especialidades:

- Clínico Geral;
- Pediatra;
- Cirurgião.

O sistema deverá solicitar ao usuário a quantidade de profissionais disponíveis em cada especialidade.

Exemplo:

```text
Informe a quantidade de Clínicos Gerais:
2

Informe a quantidade de Pediatras:
1

Informe a quantidade de Cirurgiões:
1
```

---

## 9. Cobertura mínima

A quantidade mínima exigida para cada plantão é:

| Especialidade | Manhã | Tarde | Noite |
|---|---:|---:|---:|
| Clínico Geral | 2 | 2 | 2 |
| Pediatra | 1 | 1 | 1 |
| Cirurgião | 1 | 1 | 1 |

Portanto, para qualquer um dos três turnos, o plantão deverá possuir no mínimo:

```text
2 Clínicos Gerais
1 Pediatra
1 Cirurgião
```

Todas as condições precisam ser atendidas para que o plantão possa ser considerado com cobertura adequada.

---

## 10. Critério para publicação

Um plantão somente poderá ser publicado quando todas as especialidades atenderem à cobertura mínima.

A condição pode ser representada da seguinte forma:

```text
Clínicos Gerais >= 2
E
Pediatras >= 1
E
Cirurgiões >= 1
```

Se todas as condições forem verdadeiras, o plantão poderá ser publicado.

Se pelo menos uma das condições não for atendida, o plantão não poderá ser publicado.

---

## 11. Plantão com cobertura adequada

### Exemplo de entrada

```text
Turno: Manhã

Clínicos Gerais: 2
Pediatras: 1
Cirurgiões: 1
```

### Resultado esperado

```text
===== RESULTADO DA ANÁLISE =====

Turno analisado: MANHÃ

Cobertura mínima: ATINGIDA

Conclusão:
Plantão PODE ser publicado.
```

O mesmo comportamento deverá ocorrer quando as quantidades forem maiores que o mínimo exigido, desde que estejam dentro dos limites considerados válidos pelo sistema.

---

## 12. Plantão com quantidade superior ao mínimo

### Exemplo de entrada

```text
Turno: Noite

Clínicos Gerais: 4
Pediatras: 2
Cirurgiões: 2
```

Como todas as quantidades são iguais ou superiores à cobertura mínima, o plantão deverá ser considerado adequado.

### Resultado esperado

```text
===== RESULTADO DA ANÁLISE =====

Turno analisado: NOITE

Cobertura mínima: ATINGIDA

Conclusão:
Plantão PODE ser publicado.
```

---

## 13. Plantão com falta de Clínico Geral

### Exemplo de entrada

```text
Turno: Tarde

Clínicos Gerais: 1
Pediatras: 1
Cirurgiões: 1
```

A quantidade mínima de Clínicos Gerais é 2.

### Resultado esperado

```text
===== RESULTADO DA ANÁLISE =====

Turno analisado: TARDE

Cobertura mínima: NÃO ATINGIDA

Especialidade com cobertura insuficiente:
Clínico Geral

Quantidade necessária: 2
Quantidade informada: 1

Conclusão:
Plantão NÃO pode ser publicado.
```

---

## 14. Plantão com falta de Pediatra

### Exemplo de entrada

```text
Turno: Manhã

Clínicos Gerais: 2
Pediatras: 0
Cirurgiões: 1
```

A quantidade mínima de Pediatras é 1.

A quantidade `0` é uma entrada válida. Nesse caso, significa que nenhum Pediatra está disponível para o plantão.

### Resultado esperado

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

---

## 15. Plantão com falta de Cirurgião

### Exemplo de entrada

```text
Turno: Noite

Clínicos Gerais: 2
Pediatras: 1
Cirurgiões: 0
```

A quantidade mínima de Cirurgiões é 1.

A quantidade `0` é válida e representa a ausência de Cirurgiões disponíveis para aquele plantão.

### Resultado esperado

```text
===== RESULTADO DA ANÁLISE =====

Turno analisado: NOITE

Cobertura mínima: NÃO ATINGIDA

Especialidade com cobertura insuficiente:
Cirurgião

Quantidade necessária: 1
Quantidade informada: 0

Conclusão:
Plantão NÃO pode ser publicado.
```

---

## 16. Plantão com mais de uma especialidade abaixo do mínimo

Caso mais de uma especialidade esteja abaixo da cobertura mínima, o sistema deverá informar todas as especialidades insuficientes.

### Exemplo de entrada

```text
Turno: Manhã

Clínicos Gerais: 1
Pediatras: 0
Cirurgiões: 1
```

### Resultado esperado

```text
===== RESULTADO DA ANÁLISE =====

Turno analisado: MANHÃ

Cobertura mínima: NÃO ATINGIDA

Especialidades com cobertura insuficiente:

Clínico Geral
Quantidade necessária: 2
Quantidade informada: 1

Pediatra
Quantidade necessária: 1
Quantidade informada: 0

Conclusão:
Plantão NÃO pode ser publicado.
```

O sistema deverá apresentar todas as especialidades que não atingirem a cobertura mínima para que a coordenação compreenda claramente o motivo da reprovação.

---

## 17. Quantidades negativas

Quantidades negativas de profissionais são inválidas e não poderão ser utilizadas na análise.

Exemplo:

```text
Quantidade de Clínicos Gerais: -1
```

### Resultado esperado

```text
ERRO: quantidade inválida.

A quantidade de profissionais não pode ser negativa.

Análise encerrada.
```

Após identificar uma quantidade negativa, o sistema deverá:

1. informar claramente o erro;
2. impedir que o valor seja utilizado;
3. encerrar a análise atual.

A quantidade `0` é válida, pois pode representar a ausência de profissionais disponíveis em determinada especialidade.

---

## 18. Quantidade máxima

Valores excessivamente altos podem representar erros de digitação.

A equipe propõe o limite máximo de **30 profissionais por especialidade em um único plantão**.

A proposta considera que o Hospital Santa Aurora é uma instituição de médio porte e que as coberturas mínimas exigidas na Sprint 1 são significativamente inferiores a esse valor.

Dessa forma, a equipe considera que quantidades superiores a 30 profissionais de uma mesma especialidade em um único plantão podem indicar um possível erro de digitação.

### Limite máximo proposto

```text
30 profissionais por especialidade
```

Exemplos considerando a proposta:

```text
0  → válido
1  → válido
30 → válido
31 → inválido
```

**Status:** Pendente de validação pelo cliente/P2.

Enquanto o cliente/P2 não validar formalmente esse valor, o limite de 30 deverá ser tratado como uma proposta da equipe e não como uma regra definitiva do produto.

Após a validação, esta seção deverá ser atualizada para registrar o limite como regra aprovada.

---

## 19. Mensagens apresentadas pelo sistema

As mensagens apresentadas ao usuário deverão ser claras e permitir a compreensão do resultado da análise.

Ao concluir normalmente uma análise, o sistema deverá informar:

- o turno analisado;
- se a cobertura mínima foi atingida ou não;
- a especialidade ou as especialidades insuficientes, quando houver;
- a quantidade necessária e a quantidade informada para cada especialidade insuficiente;
- se o plantão pode ou não ser publicado.

### Exemplo de aprovação

```text
Turno analisado: MANHÃ

Cobertura mínima: ATINGIDA

Conclusão:
Plantão PODE ser publicado.
```

### Exemplo de reprovação

```text
Turno analisado: MANHÃ

Cobertura mínima: NÃO ATINGIDA

Especialidade com cobertura insuficiente:
Pediatra

Quantidade necessária: 1
Quantidade informada: 0

Conclusão:
Plantão NÃO pode ser publicado.
```

### Exemplo de entrada inválida

```text
ERRO: quantidade inválida.

A quantidade de profissionais não pode ser negativa.

Análise encerrada.
```

A redação exata das mensagens poderá variar durante a implementação, desde que todas as informações obrigatórias sejam apresentadas de forma clara.

---

## 20. Exemplo completo de utilização — Plantão aprovado

### Entrada

```text
MEDSHIFT

Selecione o turno:

1 - Manhã
2 - Tarde
3 - Noite

Opção: 1

Informe a quantidade de Clínicos Gerais:
2

Informe a quantidade de Pediatras:
1

Informe a quantidade de Cirurgiões:
1
```

### Análise

O sistema deverá verificar:

```text
Clínicos Gerais >= 2
Pediatras >= 1
Cirurgiões >= 1
```

Todas as condições foram atendidas.

### Resultado esperado

```text
===== RESULTADO DA ANÁLISE =====

Turno analisado: MANHÃ

Cobertura mínima: ATINGIDA

Conclusão:
Plantão PODE ser publicado.
```

---

## 21. Exemplo completo de utilização — Plantão reprovado

### Entrada

```text
MEDSHIFT

Selecione o turno:

1 - Manhã
2 - Tarde
3 - Noite

Opção: 3

Informe a quantidade de Clínicos Gerais:
2

Informe a quantidade de Pediatras:
1

Informe a quantidade de Cirurgiões:
0
```

### Análise

O sistema deverá verificar:

```text
Clínicos Gerais >= 2
Pediatras >= 1
Cirurgiões >= 1
```

A condição referente aos Cirurgiões não foi atendida.

### Resultado esperado

```text
===== RESULTADO DA ANÁLISE =====

Turno analisado: NOITE

Cobertura mínima: NÃO ATINGIDA

Especialidade com cobertura insuficiente:
Cirurgião

Quantidade necessária: 1
Quantidade informada: 0

Conclusão:
Plantão NÃO pode ser publicado.
```

---

## 22. Exemplo completo de utilização — Entrada inválida

### Entrada

```text
Informe a quantidade de Clínicos Gerais:
-3
```

### Resultado esperado

```text
ERRO: quantidade inválida.

A quantidade de profissionais não pode ser negativa.

Análise encerrada.
```

O sistema não deverá utilizar o valor negativo para realizar a análise.

Após identificar o erro, a execução atual será encerrada.

---

## 23. Exemplo completo de utilização — Turno inválido

### Entrada

```text
Selecione o turno:

1 - Manhã
2 - Tarde
3 - Noite

Opção: 7
```

### Resultado esperado

```text
ERRO: turno inválido.

Escolha uma das opções disponíveis:
1 - Manhã
2 - Tarde
3 - Noite

Análise encerrada.
```

A opção inválida não deverá ser utilizada na análise.

---

## 24. Nova análise

Durante a Sprint 1, cada execução do MedShift realizará a análise de um plantão.

Após a conclusão da análise, o programa poderá ser encerrado.

Para analisar outro plantão, o usuário deverá executar novamente o algoritmo.

A realização de várias análises durante uma única execução não é requisito obrigatório da Sprint 1.

A funcionalidade poderá ser adicionada futuramente por meio de estruturas de repetição, caso a equipe decida implementá-la.

---

## 25. Armazenamento dos dados

O MedShift não mantém permanentemente os dados informados durante a Sprint 1.

Após o encerramento do programa, as informações daquela execução não ficam armazenadas como estado do sistema.

Para realizar uma nova análise, os dados deverão ser inseridos novamente.

---

## 26. Resumo das regras de utilização

| Situação | Resultado esperado |
|---|---|
| Clínicos >= 2, Pediatras >= 1 e Cirurgiões >= 1 | Cobertura atingida e plantão pode ser publicado |
| Clínicos < 2 | Cobertura não atingida e plantão não pode ser publicado |
| Pediatras < 1 | Cobertura não atingida e plantão não pode ser publicado |
| Cirurgiões < 1 | Cobertura não atingida e plantão não pode ser publicado |
| Quantidade igual a 0 | Entrada válida e utilizada na análise |
| Quantidade negativa | Entrada inválida e análise encerrada |
| Quantidade acima do limite máximo validado | Entrada inválida e análise encerrada |
| Turno inexistente | Opção inválida e análise encerrada |
| Todos os dados válidos | Sistema realiza normalmente a análise |

O limite máximo atualmente proposto pela equipe é de 30 profissionais por especialidade, porém permanece pendente de validação pelo cliente/P2.

---

## 27. Cenários utilizados na Sprint Review

Durante a Sprint Review, a equipe deverá estar preparada para demonstrar pelo menos:

1. um plantão que atende à cobertura mínima;
2. um plantão em que falta profissional de uma especialidade;
3. uma tentativa de informar um dado impossível;
4. uma tentativa de selecionar uma opção inválida.

Caso o limite máximo proposto seja validado antes da Review, a equipe também poderá demonstrar:

5. uma quantidade exatamente igual ao limite máximo;
6. uma quantidade superior ao limite máximo.

O sistema deverá executar os diferentes cenários sem necessidade de alteração do código-fonte durante a demonstração.

---

## 28. Cenários de teste

Os testes utilizados pela equipe estão registrados em:

```text
docs/sprint-1/testes.md
```

Esse documento contém os dados de entrada, resultados esperados e status dos cenários testados.

---

## 29. Limitações conhecidas da Sprint 1

As seguintes funcionalidades não fazem parte do escopo obrigatório desta Sprint:

- cadastro de médicos por nome;
- cadastro de CRM;
- armazenamento permanente dos dados;
- consulta de histórico;
- análise de múltiplos plantões simultaneamente;
- realização obrigatória de várias análises em uma única execução;
- interface gráfica;
- gerenciamento completo da escala hospitalar.

Essas funcionalidades não devem ser consideradas falhas do incremento da Sprint 1.

---

## 30. Problemas comuns

### 30.1 O sistema informa que o turno é inválido

Verifique se a opção digitada corresponde a uma das opções apresentadas no menu.

Exemplo:

```text
1 - Manhã
2 - Tarde
3 - Noite
```

Utilize somente uma das opções disponíveis.

Caso seja informada uma opção inexistente, a análise será encerrada e será necessário iniciar novamente o programa.

---

### 30.2 O sistema informa quantidade inválida

Verifique se foi digitada uma quantidade permitida.

Quantidades negativas não são aceitas.

A quantidade `0` é válida e representa que não existem profissionais disponíveis naquela especialidade.

A equipe também propôs o limite máximo de 30 profissionais por especialidade.

Caso esse limite seja validado pelo cliente/P2, valores superiores a 30 serão considerados inválidos.

---

### 30.3 O plantão foi reprovado mesmo possuindo profissionais

Ter profissionais disponíveis não significa necessariamente possuir cobertura adequada.

É necessário atender simultaneamente aos mínimos:

```text
2 Clínicos Gerais
1 Pediatra
1 Cirurgião
```

Exemplo:

```text
5 Clínicos Gerais
0 Pediatras
3 Cirurgiões
```

Nesse caso, o plantão não pode ser publicado porque não existe Pediatra disponível.

O resultado deverá informar a especialidade insuficiente.

---

### 30.4 O sistema não mantém os dados da análise anterior

Esse comportamento é esperado durante a Sprint 1.

O sistema não possui persistência de dados entre execuções.

---

### 30.5 O programa encerrou após uma entrada inválida

Esse comportamento é esperado durante a Sprint 1.

Quando uma entrada inválida for identificada, o sistema deverá:

1. informar o erro;
2. impedir que o dado seja utilizado;
3. encerrar a análise atual.

Para tentar novamente, execute o programa outra vez.

---

## 31. Documentação relacionada

Os principais documentos do projeto estão localizados no diretório `docs`.

```text
docs/
│
├── backlog/
│   └── product-backlog.md
│
├── sprint-1/
│   ├── sprint-backlog.md
│   ├── DoR.md
│   ├── DoD.md
│   ├── testes.md
│   └── decisoes.md
│
├── branch-strategy.md
├── commit-pattern.md
├── manual-instalacao.md
└── manual-usuario.md
```

### Manual de instalação

```text
docs/manual-instalacao.md
```

Apresenta os procedimentos necessários para preparar o ambiente e executar o sistema.

### Product Backlog

```text
docs/backlog/product-backlog.md
```

Apresenta as User Stories, regras, critérios de aceitação e informações de prioridade do produto.

### Sprint Backlog

```text
docs/sprint-1/sprint-backlog.md
```

Apresenta os itens selecionados para a Sprint 1 e suas respectivas tarefas.

### Cenários de teste

```text
docs/sprint-1/testes.md
```

Apresenta os cenários utilizados para verificar o funcionamento do sistema.

### Registro de decisões

```text
docs/sprint-1/decisoes.md
```

Apresenta as principais decisões tomadas durante a Sprint.

---

## 32. Checklist de utilização

Antes de iniciar uma análise:

- [ ] VisuAlg aberto;
- [ ] arquivo correto do MedShift carregado;
- [ ] algoritmo executando sem erro;
- [ ] turno selecionado corretamente;
- [ ] quantidade de Clínicos Gerais informada;
- [ ] quantidade de Pediatras informada;
- [ ] quantidade de Cirurgiões informada.

Após a análise:

- [ ] turno analisado apresentado;
- [ ] situação da cobertura mínima apresentada;
- [ ] condição de publicação informada;
- [ ] especialidade insuficiente apresentada em caso de reprovação;
- [ ] quantidade necessária e quantidade informada apresentadas em caso de reprovação;
- [ ] entradas inválidas tratadas corretamente.

---

## 33. Fluxo resumido de utilização

O funcionamento básico do MedShift durante a Sprint 1 pode ser representado da seguinte forma:

```text
Iniciar MedShift
       |
       v
Selecionar turno
       |
       v
Turno válido?
       |
   +---+---+
   |       |
  Sim     Não
   |       |
   |       v
   |   Informar erro
   |       |
   |       v
   |   Encerrar análise
   |
   v
Informar quantidade de Clínicos Gerais
       |
       v
Informar quantidade de Pediatras
       |
       v
Informar quantidade de Cirurgiões
       |
       v
Validar quantidades
       |
       v
Dados válidos?
       |
   +---+---+
   |       |
  Sim     Não
   |       |
   |       v
   |   Informar erro
   |       |
   |       v
   |   Encerrar análise
   |
   v
Verificar cobertura mínima
       |
       v
Todos os mínimos foram atendidos?
       |
   +---+---+
   |       |
  Sim     Não
   |       |
   v       v
Cobertura  Cobertura
atingida   não atingida
   |       |
   v       v
Pode      Identificar
publicar  especialidade(s)
           insuficiente(s)
              |
              v
          Não pode
          publicar
```

---

## 34. Considerações finais

O MedShift foi desenvolvido para fornecer à coordenação hospitalar uma forma simples e objetiva de analisar a cobertura de um plantão.

Durante a Sprint 1, o sistema deverá permitir que o usuário:

- escolha um turno;
- informe as quantidades de Clínicos Gerais, Pediatras e Cirurgiões;
- receba validação das entradas;
- saiba se a cobertura mínima foi atingida;
- saiba qual turno foi analisado;
- saiba se o plantão pode ser publicado;
- identifique a especialidade ou as especialidades insuficientes quando o plantão for reprovado;
- visualize a quantidade necessária e a quantidade informada para cada especialidade insuficiente;
- receba uma mensagem clara quando informar um dado inválido.

O usuário deverá conseguir realizar todo o processo através do console do VisuAlg, sem necessidade de acessar ou alterar o código-fonte.

Nesta Sprint, uma execução poderá analisar um único plantão.

O limite máximo atualmente proposto pela equipe é de 30 profissionais por especialidade e permanece pendente de validação pelo cliente/P2.
