# Casa Mãe Paulistana - Documentação do Projeto

Este repositório contém a documentação técnica e de decisões arquiteturais do projeto Casa Mãe Paulistana (CMP).

## 📖 Sobre o Projeto

A **Casa Mãe Paulistana** é uma iniciativa dedicada ao suporte e acolhimento de **mães de pessoas com deficiência**. O sistema digital desenvolvido pela CodeBoa Software tem como objetivo facilitar e organizar o acesso aos serviços oferecidos pela instituição.

### Público-Alvo
- **Responsáveis** (na maioria dos casos, mães) de pessoas com deficiência
- Equipe administrativa da Casa Mãe Paulistana
- Profissionais especializados (advogados, psicólogos, assistentes sociais)

### Visão Geral do Sistema

O sistema gerencia todo o ciclo de atendimento dos beneficiários, desde o cadastro inicial até a participação em oficinas e atendimentos especializados.

#### Fluxo Principal:

```
1. CADASTRO PÚBLICO
   └─ Responsável preenche formulário em formato de chat
   └─ Upload de documentos obrigatórios
   └─ Geração de protocolo único

2. APROVAÇÃO INTERNA
   └─ Equipe analisa documentos
   └─ Aprovação ou rejeição do cadastro

3. TRIAGEM
   └─ Atendimento inicial presencial
   └─ Criação da entidade do responsável no sistema
   └─ Avaliação das necessidades

4. ATENDIMENTOS ESPECIALIZADOS
   └─ Agendamento com profissionais
   └─ Advogados
   └─ Psicólogos
   └─ Assistentes Sociais

5. OFICINAS
   └─ Cadastro e participação em oficinas
   └─ Gestão de vagas e inscrições
```

### Entidade Principal: Responsável

O **Responsável** é a entidade central do sistema, representando a mãe ou cuidador(a) legal da pessoa com deficiência. Todo o fluxo do sistema gira em torno do cadastro, aprovação, atendimento e acompanhamento deste responsável.

## 📁 Estrutura do Repositório

- `/docs` - Documentação geral do projeto e análises
- `/Detalhamento por Entregas` - Requisitos e especificações por fase de entrega
  - `/fase-1` - Cadastro e Aprovação (Entrega: 10/11/2025)
  - `/fase-2` - Triagem, Atendimentos e Oficinas
  - `/entrega-3` - Funcionalidades futuras

## Como Contribuir

1. Crie uma branch a partir da `main`
2. Faça suas alterações
3. Submeta um Pull Request para revisão

## ADRs (Architecture Decision Records)

As decisões arquiteturais importantes são documentadas usando o padrão ADR na pasta `/adrs`.
