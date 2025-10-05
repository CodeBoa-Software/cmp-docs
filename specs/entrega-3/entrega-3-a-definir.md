# Requisitos para Entrega 3

**Data da Entrega:** A definir  
**Projeto:** Casa Mãe Paulistana  
**Responsável:** CodeBoa Software

---

## 📋 Escopo da Entrega

### 1. Liberação/Encaminhamento para Atendimentos

**Descrição:** Sistema para liberar beneficiários triados para atendimentos com profissionais específicos.

#### 1.1 Funcionalidades
- Aprovação de beneficiários pós-triagem
- Encaminhamento para profissionais específicos
  - Psicólogo
  - Assistente Social
  - Terapeuta Ocupacional
  - Fonoaudiólogo
  - Outros profissionais
- Definição de tipo/frequência de atendimento
- Criação de agenda/cronograma de atendimentos
- Notificação aos beneficiários sobre encaminhamento
- Notificação aos profissionais sobre novos pacientes

#### 1.2 Fluxo Sugerido
```
Triagem Concluída
    ↓
Equipe analisa resultado
    ↓
Define profissionais necessários
    ↓
Encaminha para profissionais
    ↓
Profissional aceita/recebe paciente
    ↓
Agendamento inicial
    ↓
Início dos atendimentos
```

---

### 2. Formulários dos Atendimentos

**Descrição:** Sistema completo para registro de atendimentos realizados pelos profissionais (substitui o MVP Google Forms).

#### 2.1 Funcionalidades Principais
- Formulários específicos por tipo de profissional
- Registro de evolução do paciente
- Anexo de documentos/relatórios
- Assinatura digital (profissional e/ou responsável)
- Versionamento de formulários
- Templates reutilizáveis

#### 2.2 Tipos de Formulários
- **Psicologia:** Sessões, avaliações psicológicas, plano terapêutico
- **Assistência Social:** Entrevistas, visitas, acompanhamento familiar
- **Terapia Ocupacional:** Avaliações, planos de intervenção, evolução
- **Fonoaudiologia:** Avaliações de fala/linguagem, planos terapêuticos
- **Atendimento Geral:** Observações, encaminhamentos

#### 2.3 Campos Comuns
- Data e hora do atendimento
- Profissional responsável
- Beneficiário atendido
- Tipo de atendimento
- Descrição/observações
- Próximos passos
- Data do próximo atendimento
- Status do paciente

---

### 3. Visualização dos Dados

**Descrição:** Dashboards e relatórios para visualização de dados dos atendimentos e acompanhamento de beneficiários.

#### 3.1 Painéis de Visualização

##### 3.1.1 Painel do Profissional
- Lista de pacientes ativos
- Agenda de atendimentos
- Histórico de atendimentos por paciente
- Estatísticas pessoais (atendimentos/mês, etc)
- Pendências e tarefas

##### 3.1.2 Painel Administrativo
- Visão geral de todos os atendimentos
- Estatísticas gerais
  - Total de beneficiários ativos
  - Atendimentos por período
  - Atendimentos por profissional
  - Atendimentos por tipo
- Lista de beneficiários por status
- Profissionais e suas cargas de trabalho

##### 3.1.3 Prontuário do Beneficiário
- Dados cadastrais completos
- Histórico de documentos
- Histórico de triagem
- Histórico completo de atendimentos (todos os profissionais)
- Linha do tempo de evolução
- Relatórios gerados

#### 3.2 Relatórios

##### Relatórios Operacionais
- Atendimentos realizados por período
- Atendimentos por profissional
- Beneficiários ativos/inativos
- Taxa de comparecimento vs faltas
- Lista de espera

##### Relatórios Gerenciais
- Indicadores de desempenho (KPIs)
- Evolução de beneficiários
- Produtividade da equipe
- Relatórios para prestação de contas

##### Relatórios Personalizados
- Filtros customizáveis
- Exportação (PDF, Excel, CSV)
- Agendamento de relatórios automáticos

---

## ✅ Checklist de Implementação

### Liberação/Encaminhamento
- [ ] Interface para seleção de profissionais
- [ ] Sistema de encaminhamento/atribuição
- [ ] Notificações automáticas
- [ ] Gestão de agenda/vagas por profissional
- [ ] Histórico de encaminhamentos
- [ ] Possibilidade de reatribuir/transferir paciente
- [ ] Status de aceite do profissional

### Formulários de Atendimentos
- [ ] Editor de formulários (admin)
- [ ] Templates por especialidade
- [ ] Campos customizáveis
- [ ] Validações específicas
- [ ] Upload de anexos
- [ ] Assinatura digital
- [ ] Modo offline (PWA?)
- [ ] Salvamento automático (rascunho)
- [ ] Versionamento de formulários
- [ ] Migração de dados do Google Forms

### Visualização de Dados
- [ ] Dashboard do profissional
- [ ] Dashboard administrativo
- [ ] Prontuário completo do beneficiário
- [ ] Gráficos e estatísticas
- [ ] Filtros e buscas avançadas
- [ ] Exportação de relatórios
- [ ] Impressão de prontuários
- [ ] Controle de acesso (LGPD)
- [ ] Logs de auditoria (quem acessou o quê)

### Backend/Infraestrutura
- [ ] API para formulários dinâmicos
- [ ] Banco de dados para atendimentos
- [ ] Sistema de permissões granular
- [ ] Cache para performance
- [ ] Backup automático
- [ ] Índices para consultas rápidas

---

## 📝 Notas

### Considerações Técnicas

**Formulários Dinâmicos:**
- Permitir criação de novos campos sem código
- Versionamento para não perder histórico
- Suporte a diferentes tipos de campo:
  - Texto curto/longo
  - Número
  - Data/hora
  - Seleção única/múltipla
  - Escala (1-5, 1-10)
  - Upload de arquivo
  - Assinatura

**Performance:**
- Paginação de listas grandes
- Cache de dashboards
- Queries otimizadas
- Lazy loading de históricos

**Segurança e Privacidade:**
- Criptografia de dados sensíveis
- Controle de acesso por função
- Profissional só vê seus pacientes
- Admin vê tudo mas com auditoria
- Logs de acesso ao prontuário (LGPD)
- Anonimização para relatórios gerais

**Migração do Google Forms:**
- Script de importação de dados
- Mapeamento de campos antigos → novos
- Validação de integridade
- Backup dos dados originais

### Perguntas/Decisões Pendentes

- [ ] Quais especialidades/tipos de profissionais exatamente?
- [ ] Campos específicos de cada formulário de atendimento?
- [ ] Um beneficiário pode ter múltiplos profissionais simultaneamente?
- [ ] Como funciona o aceite do profissional ao receber encaminhamento?
- [ ] Profissional pode recusar paciente?
- [ ] Sistema de fila/lista de espera por profissional?
- [ ] Relatórios: quais KPIs específicos são importantes?
- [ ] Periodicidade de relatórios automáticos?
- [ ] Integração com sistema de agendamento externo ou interno?

### Dependências

- ✅ Entrega 1 concluída (pré-cadastro)
- ✅ Entrega 2 concluída (triagem e WhatsApp)
- Dados migrados do Google Forms
- Definição de estrutura dos formulários por especialidade
- Aprovação de layouts de dashboards

### Riscos

- Complexidade de formulários dinâmicos
- Volume de dados crescente (performance)
- Migração de dados do Google Forms
- Curva de aprendizado da equipe no novo sistema
- Necessidade de treinamento extensivo

---

## 🎯 Diferencial desta Entrega

**Sistema Completo vs MVP:**
- Substitui Google Forms por solução robusta
- Centraliza todos os dados em um único sistema
- Permite análises e insights impossíveis com planilhas
- Prontuário eletrônico unificado
- Gestão efetiva de equipe e pacientes

---

## 🔄 Evolução Futura (pós-Entrega 3)

**Possíveis próximas funcionalidades:**
- Agendamento online para beneficiários
- App mobile nativo para profissionais
- Telemedicina/videochamadas integradas
- IA para sugestões de encaminhamento
- Integração com sistemas de saúde municipais
- Portal para beneficiários visualizarem seu histórico

---

## 🔗 Referências

- [Entrega 1 - Pré-cadastro](./entrega-1-22-outubro.md)
- [Entrega 2 - Triagem e WhatsApp](./entrega-2-a-definir.md)
- [Ideias e Discussões](../docs/ideias-discussoes.md)
- [LGPD - Proteção de Dados](http://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709.htm)
- [CFM - Prontuário Eletrônico](https://portal.cfm.org.br/)
