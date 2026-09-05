# MedShift - API Banco de Dados (FATEC SJC)

Repositório criado para o desenvolvimento de um sistema para criação de escalas de plantões médicos no VisualG.

**Feito por alunos do 1º Semestre 2026/2 do curso de Banco de Dados da FATEC de São José dos Campos.**

## Sobre o projeto

O MedShift é um sistema desenvolvido para apoiar a análise e
validação de plantões médicos do Hospital fictício Santa Aurora.

O sistema tem como objetivo auxiliar a coordenação hospitalar
a identificar se um plantão possui cobertura adequada e apontar
os motivos quando a escala não puder ser publicada.

## Desafio

O Hospital Santa Aurora possui médicos de diferentes
especialidades trabalhando em regime de plantão.

Atualmente, a montagem e conferência das escalas é realizada
manualmente, o que pode causar erros, falta de profissionais
em determinados turnos, ausência de especialidades e retrabalho.

O MedShift busca auxiliar a coordenação na análise dessas
escalas por meio de regras claras de validação.

## Tecnologias Utilizadas

- VisuAlg
- Git
- GitHub
- Scrum

## Sprint 1

### Meta da Sprint

Permitir que a coordenação hospitalar analise um plantão médico,
verifique se há cobertura mínima de profissionais por especialidade
e receba uma conclusão clara informando se o plantão pode ou não
ser publicado.

### Documentação

- [Product Backlog](docs/backlog/product-backlog.md)
- [Sprint Backlog](docs/sprint-1/sprint-backlog.md)
- [Definition of Ready](docs/sprint-1/DoR.md)
- [Definition of Done](docs/sprint-1/DoD.md)
- [Cenários de Teste](docs/sprint-1/testes.md)
- [Registro de Decisões](docs/sprint-1/decisoes.md)
- [Estratégia de Branches](docs/branch-strategy.md)
- [Padrão de Commits](docs/commit-pattern.md)
- [Manual de Instalação](docs/manual-instalacao.md)
- [Manual do Usuário](docs/manual-usuario.md)

## Equipe

| Integrante | Papel |
| --- | --- |
| **Lucas Augusto** | Product Owner |
| **Fernanda Martins** | Scrum Master |
| **Augusto** | Desenvolvedor |
| **Sara Andrade** | Desenvolvedor |
| **Karina** | Desenvolvedor |
| **Allan Almeida** | Desenvolvedor |
| **Arthur Peres** | Desenvolvedor |

---
## Organização do Desenvolvimento

O desenvolvimento do MedShift utiliza uma estratégia de branches para manter a branch principal estável e facilitar a organização das alterações realizadas pela equipe.

Novas funcionalidades, correções, testes e alterações de documentação devem ser realizadas em branches específicas e posteriormente integradas à `main` por meio de Pull Requests.

A estratégia completa está documentada em:

- [Estratégia de Branches](docs/branch-strategy.md)
- [Padrão de Mensagens de Commit](docs/commit-pattern.md)
