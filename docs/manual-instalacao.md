# Manual de Instalação

## 1. Objetivo

Este documento apresenta os requisitos e os procedimentos necessários para preparar o ambiente e executar o projeto MedShift.

O MedShift é um sistema de apoio à construção e validação de escalas médicas desenvolvido em pseudocódigo utilizando o VisuAlg.

Por se tratar de um projeto executado diretamente no ambiente do VisuAlg, não existe um processo convencional de instalação do MedShift. É necessário instalar o ambiente de execução, obter os arquivos do projeto e abrir o algoritmo no VisuAlg.

---

## 2. Requisitos do sistema

Para executar o MedShift, é necessário possuir:

- um computador compatível com o VisuAlg;
- sistema operacional compatível com a versão do VisuAlg utilizada;
- VisuAlg instalado;
- acesso aos arquivos do projeto MedShift;
- teclado para interação com o sistema;
- Git instalado, apenas caso o usuário opte por clonar o repositório pelo terminal.

O Git não é obrigatório para executar o MedShift.

---

## 3. Tecnologia utilizada

A implementação principal do projeto é realizada utilizando:

| Tecnologia | Finalidade |
|---|---|
| VisuAlg | Desenvolvimento e execução do pseudocódigo |
| Git | Controle de versão |
| GitHub | Armazenamento, documentação e colaboração no projeto |

O sistema funciona através de interação textual em ambiente de console.

Não é necessária a instalação de banco de dados, servidor web ou outras dependências externas para executar o incremento da Sprint 1.

---

## 4. Instalação do VisuAlg

Antes de executar o MedShift, o VisuAlg deve estar instalado no computador.

### Procedimento

1. Obtenha a versão do VisuAlg utilizada pela equipe ou indicada pela instituição.
2. Execute o instalador do VisuAlg.
3. Siga as instruções apresentadas pelo instalador.
4. Conclua a instalação.
5. Abra o VisuAlg para verificar se o programa está funcionando corretamente.

Recomenda-se utilizar a mesma versão disponível nos laboratórios da instituição ou a versão utilizada durante o desenvolvimento do projeto.

Isso reduz o risco de diferenças de comportamento entre versões.

---

## 5. Obtenção do projeto

O projeto pode ser obtido de duas maneiras:

1. download do repositório pelo GitHub;
2. clone do repositório utilizando Git.

---

## 6. Opção 1 — Download pelo GitHub

Para obter o projeto sem utilizar Git:

1. Acesse o repositório oficial do MedShift no GitHub.
2. Na página principal do repositório, clique no botão `Code`.
3. Selecione a opção `Download ZIP`.
4. Aguarde o download.
5. Localize o arquivo `.zip` no computador.
6. Extraia o conteúdo para uma pasta de sua preferência.

Após a extração, os arquivos do projeto estarão disponíveis localmente.

Exemplo de pasta:

```text
MedShift-API---1-Semestre-BD-FATEC/
```

---

## 7. Opção 2 — Clone utilizando Git

Caso o Git esteja instalado, o repositório também pode ser clonado.

Abra o terminal, Prompt de Comando, PowerShell ou Git Bash e execute:

```bash
git clone https://github.com/D7-BD-FATEC/MedShift-API---1-Semestre-BD-FATEC.git
```

Após a conclusão, acesse a pasta criada:

```bash
cd MedShift-API---1-Semestre-BD-FATEC
```

O conteúdo do projeto estará disponível localmente.

---

## 8. Localização do código-fonte

Após obter o projeto, localize o arquivo que contém o algoritmo correspondente à Sprint 1.

A estrutura do repositório poderá ser atualizada durante o desenvolvimento do projeto.

O usuário deverá localizar o arquivo principal utilizado pela equipe para execução do MedShift.

Caso o código seja posteriormente organizado em uma pasta específica, recomenda-se utilizar uma estrutura semelhante a:

```text
src/
└── medshift.alg
```

O nome e a localização definitivos devem corresponder à organização adotada no repositório.

---

## 9. Abertura do projeto no VisuAlg

Após localizar o arquivo principal:

1. Abra o VisuAlg.
2. Acesse a opção de abertura de arquivo.
3. Navegue até a pasta do projeto MedShift.
4. Selecione o arquivo correspondente ao algoritmo.
5. Abra o arquivo.
6. Verifique se o código foi carregado corretamente no editor.

O algoritmo deverá aparecer na área de edição do VisuAlg.

---

## 10. Execução do MedShift

Com o código aberto no VisuAlg:

1. inicie a execução do algoritmo;
2. aguarde a apresentação das instruções no console;
3. escolha uma das opções disponibilizadas pelo sistema;
4. informe os dados solicitados;
5. aguarde o processamento;
6. verifique o resultado apresentado.

A utilização do sistema deve ocorrer exclusivamente através das opções apresentadas pelo programa.

Não deve ser necessário modificar o código-fonte para realizar uma análise.

---

## 11. Dados utilizados na Sprint 1

Durante a Sprint 1, o MedShift analisa um plantão por vez.

O sistema trabalha com três turnos:

```text
Manhã
Tarde
Noite
```

Também são consideradas três especialidades:

```text
Clínico Geral
Pediatra
Cirurgião
```

A cobertura mínima definida para cada turno é:

| Especialidade | Manhã | Tarde | Noite |
|---|---:|---:|---:|
| Clínico Geral | 2 | 2 | 2 |
| Pediatra | 1 | 1 | 1 |
| Cirurgião | 1 | 1 | 1 |

O sistema deverá utilizar essas informações para determinar se o plantão possui cobertura adequada.

---

## 12. Teste inicial de funcionamento

Após abrir o projeto, recomenda-se realizar um teste simples para verificar se o ambiente está funcionando corretamente.

### Exemplo de cenário válido

Utilize:

```text
Turno: Manhã

Clínicos Gerais: 2
Pediatras: 1
Cirurgiões: 1
```

### Resultado esperado

O sistema deverá indicar que o plantão atende à cobertura mínima e pode ser publicado.

A redação exata da mensagem poderá variar conforme a implementação do algoritmo.

---

## 13. Teste de cobertura insuficiente

Também é recomendado verificar um cenário em que a cobertura mínima não seja atendida.

### Exemplo

```text
Turno: Manhã

Clínicos Gerais: 2
Pediatras: 0
Cirurgiões: 1
```

### Resultado esperado

O sistema deverá:

1. informar que o plantão não pode ser publicado;
2. indicar que existe quantidade insuficiente de Pediatras.

O sistema deve informar o motivo da reprovação e não apenas apresentar uma mensagem genérica de erro.

---

## 14. Teste de entrada inválida

O sistema também deverá tratar dados impossíveis.

### Exemplo

```text
Clínicos Gerais: -1
```

### Resultado esperado

O valor deverá ser rejeitado ou sinalizado como inválido.

Quantidades negativas de profissionais não devem ser aceitas.

---

## 15. Teste de opção inválida

Caso o sistema utilize opções numéricas para selecionar o turno, uma opção inexistente também deverá ser testada.

Exemplo de menu:

```text
1 - Manhã
2 - Tarde
3 - Noite
```

Entrada:

```text
9
```

### Resultado esperado

O sistema deverá informar que a opção selecionada é inválida.

---

## 16. Persistência de dados

Durante a Sprint 1, o MedShift não mantém informações entre execuções.

Ao encerrar o algoritmo, os dados utilizados naquela execução não são armazenados como estado permanente do sistema.

Para realizar uma nova análise, os dados deverão ser informados novamente.

Essa característica é compatível com o escopo da Sprint 1 e com as limitações do VisuAlg.

---

## 17. Uso de arquivos para testes

O VisuAlg possui o comando `arquivo`, que pode ser utilizado para fornecer automaticamente valores aos comandos `leia`.

Esse recurso pode ser utilizado pela equipe para preparar cenários de teste reproduzíveis.

Entretanto, o comando `arquivo` não deve ser interpretado como um mecanismo de armazenamento permanente do sistema.

Ele funciona como uma fonte de entrada de dados para uma execução.

Caso seja utilizado, a ordem dos dados no arquivo deverá corresponder exatamente à ordem dos comandos `leia` executados pelo algoritmo.

---

## 18. Compatibilidade entre versões do VisuAlg

Alguns recursos do VisuAlg podem apresentar diferenças de comportamento entre versões.

Por esse motivo, recomenda-se:

1. utilizar a mesma versão adotada pela equipe;
2. testar o algoritmo na versão existente no laboratório;
3. realizar os testes antes da Sprint Review;
4. evitar depender de recursos cujo comportamento não tenha sido verificado;
5. executar todos os cenários de teste no ambiente que será utilizado durante a apresentação.

---

## 19. Problemas comuns

### 19.1 O arquivo não abre

Verifique:

- se o arquivo correto foi selecionado;
- se o download do projeto foi concluído corretamente;
- se o arquivo não está corrompido;
- se o arquivo está em um formato compatível com o VisuAlg.

---

### 19.2 O VisuAlg apresenta erro de sintaxe

Verifique a linha indicada pelo programa.

Também confirme:

- se o código está completo;
- se nenhuma parte foi removida durante o download ou edição;
- se a versão do VisuAlg é compatível;
- se o arquivo utilizado corresponde à versão atual do projeto.

---

### 19.3 O sistema não inicia

Verifique:

1. se o VisuAlg está funcionando;
2. se o algoritmo correto está aberto;
3. se existem erros de sintaxe;
4. se a execução foi iniciada corretamente.

---

### 19.4 O sistema apresenta resultado diferente do esperado

Execute os cenários definidos em:

```text
docs/sprint-1/testes.md
```

Compare:

- dados de entrada;
- resultado esperado;
- resultado obtido.

Caso o resultado seja diferente, registre o problema e revise a implementação antes de considerar a funcionalidade concluída.

---

### 19.5 O sistema solicita dados em ordem inesperada

Caso esteja utilizando o comando `arquivo`, verifique se os dados presentes no arquivo estão exatamente na mesma ordem dos comandos `leia`.

Um arquivo de entrada incompatível com a sequência do algoritmo pode comprometer a execução do teste.

---

## 20. Atualização do projeto

Caso o projeto tenha sido clonado utilizando Git, é possível obter atualizações executando:

```bash
git pull
```

Antes de utilizar esse comando, certifique-se de estar dentro da pasta do repositório.

Exemplo:

```bash
cd MedShift-API---1-Semestre-BD-FATEC
git pull
```

Caso o projeto tenha sido obtido através de `Download ZIP`, será necessário baixar novamente a versão atualizada do repositório quando desejado.

---

## 21. Estrutura da documentação

A documentação principal do projeto está localizada na pasta:

```text
docs/
```

A estrutura prevista é:

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

---

## 22. Documentos relacionados

Para compreender o funcionamento e o processo de desenvolvimento do projeto, consulte:

### Product Backlog

```text
docs/backlog/product-backlog.md
```

Contém as necessidades, User Stories, prioridades e critérios relacionados ao produto.

### Sprint Backlog

```text
docs/sprint-1/sprint-backlog.md
```

Contém os itens e tarefas selecionados para desenvolvimento durante a Sprint 1.

### Definition of Ready

```text
docs/sprint-1/DoR.md
```

Define os critérios necessários para que um item esteja preparado para entrar em desenvolvimento.

### Definition of Done

```text
docs/sprint-1/DoD.md
```

Define os critérios necessários para considerar uma tarefa ou funcionalidade concluída.

### Cenários de teste

```text
docs/sprint-1/testes.md
```

Contém os cenários utilizados para validar as funcionalidades da Sprint.

### Registro de decisões

```text
docs/sprint-1/decisoes.md
```

Apresenta as principais decisões de produto e decisões técnicas adotadas durante a Sprint.

### Estratégia de branches

```text
docs/branch-strategy.md
```

Define a estratégia utilizada pela equipe para organização das branches do repositório.

### Padrão de commits

```text
docs/commit-pattern.md
```

Define o padrão utilizado nas mensagens de commit.

### Manual do usuário

```text
docs/manual-usuario.md
```

Apresenta as instruções para utilização do MedShift.

---

## 23. Checklist de instalação e execução

Antes de considerar o ambiente preparado, verifique:

- [ ] VisuAlg instalado;
- [ ] versão do VisuAlg compatível;
- [ ] repositório MedShift obtido;
- [ ] arquivos extraídos ou repositório clonado;
- [ ] arquivo principal do algoritmo localizado;
- [ ] algoritmo aberto no VisuAlg;
- [ ] código sem erros de sintaxe;
- [ ] execução iniciada corretamente;
- [ ] cenário de cobertura adequada testado;
- [ ] cenário de cobertura insuficiente testado;
- [ ] entrada inválida testada;
- [ ] opção inválida testada;
- [ ] resultados comparados com os cenários documentados.

---

## 24. Considerações finais

O MedShift não exige um processo convencional de instalação do próprio sistema.

Para utilizá-lo, é necessário preparar o ambiente VisuAlg, obter os arquivos do repositório e abrir o algoritmo correspondente.

A equipe deverá manter o código-fonte e a documentação atualizados durante a evolução das Sprints.

Antes de cada apresentação, recomenda-se validar o funcionamento do sistema no mesmo ambiente que será utilizado durante a demonstração.
