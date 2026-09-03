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

Durante a Sprint 1, o MedShift realiza a análise de um plantão por vez.

O sistema não possui, nesta etapa:

- cadastro nominal de médicos;
- análise simultânea de vários plantões;
- armazenamento permanente dos dados;
- interface gráfica;
- continuidade automática dos dados entre execuções.

O objetivo da Sprint 1 é verificar se um determinado plantão possui cobertura mínima adequada.

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

Caso seja informada uma opção que não corresponda a nenhum dos turnos disponíveis, o sistema deverá sinalizar o erro.

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
Opção inválida.
```

O sistema não deverá considerar uma opção inexistente como válida.

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

Todas as condições precisam ser atendidas para que o plantão possa ser considerado adequado.

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
Plantão com cobertura adequada.
Plantão pode ser publicado.
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
Plantão com cobertura adequada.
Plantão pode ser publicado.
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
Plantão não pode ser publicado.
Quantidade insuficiente de Clínicos Gerais.
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

### Resultado esperado

```text
Plantão não pode ser publicado.
Quantidade insuficiente de Pediatras.
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

### Resultado esperado

```text
Plantão não pode ser publicado.
Quantidade insuficiente de Cirurgiões.
```

---

## 16. Plantão com mais de uma especialidade abaixo do mínimo

Caso mais de uma especialidade esteja abaixo da cobertura mínima, o sistema deverá deixar claro que o plantão não pode ser publicado.

Exemplo:

```text
Turno: Manhã

Clínicos Gerais: 1
Pediatras: 0
Cirurgiões: 1
```

O sistema deverá indicar os problemas de cobertura identificados de acordo com a implementação adotada pela equipe.

Exemplo de saída possível:

```text
Plantão não pode ser publicado.

Quantidade insuficiente de Clínicos Gerais.
Quantidade insuficiente de Pediatras.
```

O requisito principal é que o usuário consiga compreender o motivo pelo qual o plantão foi reprovado.

---

## 17. Quantidades negativas

Quantidades negativas de profissionais são inválidas.

Exemplo:

```text
Quantidade de Clínicos Gerais: -1
```

O sistema deverá impedir ou sinalizar a operação.

Exemplo de resultado:

```text
Quantidade inválida.
```

Uma quantidade negativa não poderá ser utilizada na análise do plantão.

---

## 18. Quantidade máxima

Valores excessivamente altos também podem representar erro de digitação.

Por esse motivo, o projeto prevê a definição de uma quantidade máxima plausível de profissionais.

O valor deverá ser proposto pela equipe e validado com o cliente/P2.

Enquanto esse valor não estiver formalmente validado, ele não deverá ser tratado na documentação como uma regra definitiva.

Após a validação, esta seção deverá ser atualizada.

### Valor máximo validado

```text
A definir com o cliente/P2.
```

---

## 19. Mensagens apresentadas pelo sistema

As mensagens apresentadas ao usuário deverão ser claras e permitir a compreensão do resultado.

Exemplos de mensagens possíveis:

```text
Plantão pode ser publicado.
```

```text
Plantão não pode ser publicado.
```

```text
Quantidade insuficiente de Clínicos Gerais.
```

```text
Quantidade insuficiente de Pediatras.
```

```text
Quantidade insuficiente de Cirurgiões.
```

```text
Quantidade inválida.
```

```text
Opção inválida.
```

A redação exata poderá variar conforme a implementação, desde que o significado seja apresentado de forma clara.

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
Plantão com cobertura adequada.
Plantão pode ser publicado.
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
Plantão não pode ser publicado.
Quantidade insuficiente de Cirurgiões.
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
Quantidade inválida.
```

O sistema não deverá utilizar o valor negativo para realizar a análise.

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
Opção inválida.
```

---

## 24. Nova análise

Durante a Sprint 1, cada análise considera um plantão por vez.

Caso o sistema esteja configurado para finalizar após uma análise, será necessário executar novamente o algoritmo para analisar outro plantão.

A repetição automática de análises na mesma execução poderá ser implementada caso a equipe utilize estruturas de repetição, mas não é uma exigência inicial da Sprint 1.

---

## 25. Armazenamento dos dados

O MedShift não mantém permanentemente os dados informados durante a Sprint 1.

Após o encerramento do programa, as informações daquela execução não ficam armazenadas como estado do sistema.

Para realizar uma nova análise, os dados deverão ser inseridos novamente.

---

## 26. Resumo das regras de utilização

| Situação | Resultado esperado |
|---|---|
| Clínicos >= 2, Pediatras >= 1 e Cirurgiões >= 1 | Plantão pode ser publicado |
| Clínicos < 2 | Plantão não pode ser publicado |
| Pediatras < 1 | Plantão não pode ser publicado |
| Cirurgiões < 1 | Plantão não pode ser publicado |
| Quantidade negativa | Entrada inválida |
| Quantidade acima do limite validado | Entrada inválida |
| Turno inexistente | Opção inválida |
| Todos os dados válidos | Sistema realiza a análise |

---

## 27. Cenários utilizados na Sprint Review

Durante a Sprint Review, a equipe deverá estar preparada para demonstrar pelo menos:

1. um plantão que atende à cobertura mínima;
2. um plantão em que falta profissional de uma especialidade;
3. uma tentativa de informar um dado impossível;
4. uma tentativa de selecionar uma opção inválida.

O sistema deverá executar esses cenários sem necessidade de alteração do código-fonte durante a demonstração.

---

## 28. Cenários de teste

Os testes utilizados pela equipe estão registrados em:

```text
docs/sprint-1/testes.md
```

Esse documento contém os dados de entrada, resultados esperados e status dos cenários testados.

---

## 29. Limitações conhecidas da Sprint 1

As seguintes funcionalidades não fazem parte do escopo desta Sprint:

- cadastro de médicos por nome;
- cadastro de CRM;
- armazenamento permanente dos dados;
- consulta de histórico;
- análise de múltiplos plantões simultaneamente;
- interface gráfica;
- gerenciamento completo da escala hospitalar.

Essas funcionalidades não devem ser consideradas falhas do incremento da Sprint 1.

---

## 30. Problemas comuns

### 30.1 O sistema informa que a opção é inválida

Verifique se a opção digitada corresponde a uma das opções apresentadas no menu.

Exemplo:

```text
1 - Manhã
2 - Tarde
3 - Noite
```

Utilize somente uma das opções disponíveis.

---

### 30.2 O sistema informa quantidade inválida

Verifique se foi digitada uma quantidade permitida.

Quantidades negativas não são aceitas.

Também poderão ser rejeitadas quantidades excessivamente altas de acordo com o limite máximo validado com o cliente/P2.

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

---

### 30.4 O sistema não mantém os dados da análise anterior

Esse comportamento é esperado durante a Sprint 1.

O sistema não possui persistência de dados entre execuções.

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

Apresenta as User Stories, prioridades, regras e critérios relacionados ao produto.

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

- [ ] resultado apresentado;
- [ ] condição de publicação informada;
- [ ] motivo apresentado caso o plantão seja reprovado;
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
Informar quantidade de Clínicos Gerais
       |
       v
Informar quantidade de Pediatras
       |
       v
Informar quantidade de Cirurgiões
       |
       v
Validar dados
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
Pode     Não pode
publicar publicar
           |
           v
      Informar motivo
```

---

## 34. Considerações finais

O MedShift foi desenvolvido para fornecer à coordenação hospitalar uma forma simples e objetiva de analisar a cobertura de um plantão.

Durante a Sprint 1, o sistema deve permitir que o usuário:

- escolha um turno;
- informe as quantidades de profissionais;
- receba validação das entradas;
- saiba se a cobertura mínima foi atendida;
- saiba se o plantão pode ser publicado;
- identifique o motivo quando o plantão for reprovado.

O usuário deverá conseguir realizar todo o processo através do console, sem necessidade de acessar ou alterar o código-fonte.
