# Requisitos para Fase 2 - Data a Definir

**Data da Entrega:** A definir  
**Projeto:** Casa Mãe Paulistana  
**Responsável:** CodeBoa Software

---

## 📋 Escopo da Entrega

A Fase 2 expande o sistema para incluir o **registro de dados** coletados durante a **Triagem** e **Atendimentos** especializados, além do cadastro e gestão de **Oficinas** (incluindo inscrições e controle de presença).

**Importante:** Esta fase **NÃO** inclui:
- Sistema de agendamentos (será Fase 3)
- Upload ou armazenamento de documentos/imagens
- Documentação técnica detalhada

### Pré-requisitos
- Fase 1 concluída e em produção
- Cadastros aprovados disponíveis no sistema
- Sistema de autenticação e autorização funcional

---

## 📊 Resumo Executivo

### Objetivo
Criar funcionalidades para registrar e gerenciar dados coletados após a aprovação do cadastro inicial, permitindo o acompanhamento completo do ciclo de atendimento dos responsáveis.

### Módulos da Fase 2

| Módulo | Descrição | Principais Telas |
|--------|-----------|------------------|
| **Triagem** | Registro de dados coletados na triagem presencial | • Formulário de Triagem<br>• Lista de Responsáveis<br>• Visualização de Detalhes |
| **Atendimentos** | Cadastro de profissionais e registro de atendimentos realizados | • Cadastro de Profissionais<br>• Registro de Atendimento<br>• Histórico de Atendimentos |
| **Oficinas** | Gestão completa de oficinas com inscrições e presença | • Cadastro de Oficinas<br>• Lista de Oficinas<br>• Inscrição de Participantes<br>• Controle de Presença |

### Estimativa de Complexidade

**Formulários:** 6 principais
- Formulário de Triagem (complexo)
- Edição de Responsável (médio)
- Cadastro de Profissional (simples)
- Registro de Atendimento (médio)
- Cadastro de Oficina (médio)
- Controle de Presença (simples)

**Listagens/Telas de Visualização:** 8 principais
- Lista de Responsáveis
- Detalhes do Responsável
- Lista de Profissionais
- Histórico de Atendimentos
- Lista de Oficinas
- Lista de Inscritos
- Dashboard com Métricas
- Busca Global

**Funcionalidades Especiais:**
- Controle de vagas em oficinas
- Validações de inscrição
- Registro de presença por encontro
- Estatísticas de frequência
- Exportações (Excel/CSV)
- Controle de permissões por perfil

---

## 1. Módulo de Triagem

**Descrição:** Sistema para registrar dados coletados durante o atendimento inicial presencial (triagem), criando a entidade completa do Responsável no sistema.

### 1.1 Formulário de Triagem

**Objetivo:** Formulário para registro das informações coletadas durante a triagem presencial.

**Categorias de Dados:**
- Dados pessoais completos do Responsável
- Dados do(s) Dependente(s)
- Avaliação social
- Necessidades identificadas
- Campo de observações

**Funcionalidades:**
- Salvamento automático (draft)
- Validação de campos obrigatórios
- Registro de quem preencheu e quando
- Ao concluir: criar entidade Responsável e Dependente(s) no sistema

### 1.2 Tela: Lista de Responsáveis

**Objetivo:** Visualizar e gerenciar todos os responsáveis cadastrados.

**Funcionalidades:**
- Listagem com busca e filtros
- Visualização de detalhes completos
- Editar informações cadastrais
- Adicionar observações
- Ver histórico de atendimentos
- Ver oficinas participadas
- Exportar dados (Excel/CSV)

---

## 2. Módulo de Atendimentos Especializados

**Descrição:** Sistema para registrar atendimentos realizados com profissionais especializados (advogados, psicólogos e assistentes sociais).

**Nota:** Sistema de agendamento será implementado na Fase 3. Esta fase contempla apenas o registro dos atendimentos já realizados.

### 2.1 Cadastro de Profissionais

**Objetivo:** Gerenciar cadastro de profissionais.

**Dados do Profissional:**
- Informações básicas (nome, especialidade, registro profissional)
- Contato
- Status (Ativo/Inativo)

**Funcionalidades:**
- Criar, editar, visualizar e desativar profissionais
- Listar profissionais por especialidade

### 2.2 Formulário de Registro de Atendimento

**Objetivo:** Registrar dados de atendimentos realizados.

**Dados do Atendimento:**
- Responsável atendido
- Profissional que atendeu
- Data e hora do atendimento
- Tipo de atendimento (primeira consulta, retorno, etc)
- Resumo do atendimento
- Orientações e encaminhamentos
- Campo de observações

**Funcionalidades:**
- Salvamento automático (draft)
- Apenas profissional e administradores visualizam registros
- Histórico de edições

### 2.3 Tela: Histórico de Atendimentos

**Objetivo:** Visualizar histórico de atendimentos.

**Funcionalidades:**
- Lista de atendimentos por responsável
- Filtros: data, especialidade, profissional
- Visualização detalhada de cada atendimento
- Estatísticas básicas (total por especialidade, último atendimento)
- Exportar dados (Excel/CSV)

---

## 3. Módulo de Oficinas

**Descrição:** Sistema para cadastrar oficinas, gerenciar inscrições e registrar presenças.

### 3.1 Cadastro de Oficinas

**Objetivo:** Gerenciar oficinas oferecidas.

**Dados da Oficina:**
- Informações básicas (nome, descrição, categoria)
- Configurações (limite de participantes, datas, horários, local)
- Instrutor/facilitador
- Status da oficina

**Funcionalidades:**
- Criar, editar, visualizar oficinas
- Controlar status (rascunho, ativa, concluída, cancelada)
- Duplicar oficina (para criar similar)
- Visualizar vagas disponíveis vs ocupadas

### 3.2 Tela: Lista de Oficinas

**Objetivo:** Visualizar e gerenciar oficinas.

**Funcionalidades:**
- Listagem com filtros (status, categoria, período)
- Busca por nome
- Visualizar detalhes da oficina
- Ver lista de inscritos
- Ações rápidas (editar, inscrever participante)

### 3.3 Inscrição em Oficinas

**Objetivo:** Inscrever responsáveis em oficinas.

**Fluxo de Inscrição:**
- Selecionar responsável (busca por nome/CPF)
- Selecionar oficina
- Validações: vagas disponíveis, não duplicar inscrição
- Confirmar inscrição

**Funcionalidades:**
- Registro de inscrições
- Controle de vagas
- Cancelamento de inscrição (com motivo)

### 3.4 Gestão de Inscritos

**Objetivo:** Gerenciar inscritos de cada oficina.

**Tela: Lista de Inscritos**
- Visualizar todos os inscritos da oficina
- Informações de contato
- Status da inscrição
- Exportar lista (Excel/CSV)

### 3.5 Controle de Presença

**Objetivo:** Registrar presença dos participantes em cada encontro da oficina.

**Funcionalidades:**
- Registrar presença por encontro/data
- Marcar como presente, ausente ou justificado
- Visualizar histórico de presença por participante
- Estatísticas de presença
- Exportar relatório de frequência

---

## ✅ Checklist de Implementação

### 1. Módulo de Triagem

- [ ] **Formulário de Triagem**
  - [ ] Formulário para dados do responsável
  - [ ] Formulário para dados do(s) dependente(s)
  - [ ] Seção de avaliação social
  - [ ] Salvamento automático (draft)
  - [ ] Validações de campos obrigatórios
  - [ ] Criar entidades ao concluir

- [ ] **Tela: Lista de Responsáveis**
  - [ ] Listagem com busca e filtros
  - [ ] Visualização de detalhes completos
  - [ ] Edição de informações
  - [ ] Adicionar observações
  - [ ] Ver histórico de atendimentos
  - [ ] Ver oficinas participadas
  - [ ] Exportação (Excel/CSV)

### 2. Módulo de Atendimentos Especializados

- [ ] **Cadastro de Profissionais**
  - [ ] Formulário CRUD de profissionais
  - [ ] Especialidades (Advogado, Psicólogo, Assistente Social)
  - [ ] Status ativo/inativo

- [ ] **Formulário de Registro de Atendimento**
  - [ ] Seleção de responsável e profissional
  - [ ] Campos de registro do atendimento
  - [ ] Salvamento automático
  - [ ] Privacidade (apenas profissional e admin visualizam)

- [ ] **Tela: Histórico de Atendimentos**
  - [ ] Lista de atendimentos por responsável
  - [ ] Filtros (data, especialidade, profissional)
  - [ ] Visualização detalhada
  - [ ] Estatísticas básicas
  - [ ] Exportação (Excel/CSV)

### 3. Módulo de Oficinas

- [ ] **Cadastro de Oficinas**
  - [ ] Formulário de criação/edição
  - [ ] Configurações (limite, datas, horários)
  - [ ] Status da oficina
  - [ ] Duplicar oficina

- [ ] **Tela: Lista de Oficinas**
  - [ ] Listagem com filtros
  - [ ] Busca
  - [ ] Visualizar detalhes e inscritos
  - [ ] Controle de vagas

- [ ] **Inscrição em Oficinas**
  - [ ] Tela de nova inscrição
  - [ ] Validações (vagas, duplicação)
  - [ ] Controle de vagas

- [ ] **Gestão de Inscritos**
  - [ ] Lista de inscritos por oficina
  - [ ] Cancelamento de inscrição
  - [ ] Exportação de lista

- [ ] **Controle de Presença**
  - [ ] Registrar presença por encontro
  - [ ] Histórico de presença
  - [ ] Estatísticas de frequência
  - [ ] Exportar relatório de presença

### 4. Funcionalidades Transversais

- [ ] **Dashboard Administrativo**
  - [ ] Métricas gerais (triagens, atendimentos, oficinas)
  - [ ] Indicadores principais

- [ ] **Permissões e Segurança**
  - [ ] Controle de acesso por perfil
  - [ ] LGPD e privacidade de dados

- [ ] **Busca Global**
  - [ ] Busca unificada por responsáveis (nome, CPF, protocolo)

- [ ] **Exportações**
  - [ ] Excel/CSV para todas as listagens principais

### 5. UX/UI

- [ ] Design responsivo (mobile e desktop)
- [ ] Acessibilidade (leitores de tela, alto contraste)
- [ ] Feedback visual claro
- [ ] Mensagens de erro amigáveis
- [ ] Confirmações para ações críticas

---

## 🔄 Fluxos Principais do Sistema

### Fluxo 1: Triagem e Registro de Atendimento

```
1. CADASTRO APROVADO (da Fase 1)
   ↓
2. TRIAGEM PRESENCIAL
   ├─ Equipe preenche formulário de triagem
   ├─ Coleta dados completos do responsável e dependente(s)
   ├─ Faz avaliação social
   └─ Conclui triagem
   ↓
3. CRIAÇÃO DA ENTIDADE RESPONSÁVEL
   ├─ Sistema cria Responsável no banco
   ├─ Sistema cria Dependente(s)
   └─ Status: "Triagem Concluída"
   ↓
4. ATENDIMENTO REALIZADO
   ├─ Profissional atende o responsável
   ├─ Acessa sistema e registra atendimento
   ├─ Preenche informações da sessão
   └─ Salva registro
   ↓
5. HISTÓRICO ATUALIZADO
   └─ Atendimento aparece no histórico do Responsável
```

### Fluxo 2: Gestão de Oficinas

```
1. CRIAÇÃO DA OFICINA
   ├─ Admin cadastra nova oficina
   ├─ Define limite de participantes
   ├─ Configura horários e datas
   └─ Ativa oficina
   ↓
2. INSCRIÇÃO DE RESPONSÁVEL
   ├─ Equipe acessa "Nova Inscrição"
   ├─ Busca Responsável
   ├─ Seleciona Oficina
   ├─ Valida vagas disponíveis
   └─ Confirma inscrição
   ↓
3. CONTROLE DE PRESENÇA
   ├─ A cada encontro da oficina
   ├─ Equipe marca presença dos participantes
   └─ Sistema registra frequência
   ↓
4. CONCLUSÃO DA OFICINA
   ├─ Oficina finaliza
   ├─ Sistema gera estatísticas de presença
   └─ Histórico atualizado no perfil do Responsável
```

### Fluxo 3: Ciclo Completo do Responsável

```
FASE 1: CADASTRO E APROVAÇÃO
   ├─ Formulário público preenchido
   ├─ Documentos enviados
   └─ Cadastro aprovado
   ↓
FASE 2: TRIAGEM
   ├─ Triagem presencial realizada
   ├─ Dados completos coletados
   └─ Entidade criada no sistema
   ↓
FASE 2: ATENDIMENTOS
   ├─ Atendimentos especializados realizados
   ├─ Registros salvos no sistema
   └─ Histórico de acompanhamento
   ↓
FASE 2: OFICINAS
   ├─ Inscrição em oficinas
   ├─ Participação e presença registrada
   └─ Desenvolvimento contínuo
```

---

## 📝 Notas Importantes

### Considerações Gerais

**Escopo Simplificado:**
- Foco no registro de dados, não em agendamentos
- Sem upload/armazenamento de documentos ou imagens
- Formulários para coleta de informações estruturadas
- Objetivo: estimativa de horas e precificação

**Validações Importantes:**
- Controle de vagas em oficinas
- Evitar inscrições duplicadas
- Campos obrigatórios claramente definidos
- Privacidade de registros de atendimentos (apenas profissional e admin)

**Permissões:**
- Administrador: acesso completo
- Profissionais: registram e visualizam seus atendimentos
- Coordenadores: visualizam dados e estatísticas
- Recepção: acesso limitado a funções operacionais

---

### Perguntas/Decisões Pendentes

- [ ] Quais campos específicos incluir em cada formulário?
- [ ] Triagem pode ser editada depois de concluída?
- [ ] Profissionais terão login próprio ou apenas admin registra?
- [ ] Profissional pode ver registros de outros profissionais?
- [ ] Limite de oficinas simultâneas por responsável?
- [ ] Definir categorias de oficinas

---

## 🎯 Resumo de Funcionalidades

### Funcionalidades Principais

**1. Triagem**
- Formulário de coleta de dados completos
- Lista e busca de responsáveis
- Histórico e visualizações

**2. Atendimentos**
- Cadastro de profissionais
- Registro de atendimentos realizados
- Histórico de atendimentos por responsável

**3. Oficinas**
- Cadastro e gestão de oficinas
- Inscrição de responsáveis
- Controle de vagas
- Registro de presença
- Estatísticas de frequência

**4. Transversal**
- Dashboard com métricas
- Busca global de responsáveis
- Exportações (Excel/CSV)
- Controle de permissões

---

## 🔗 Referências

- [Requisitos Fase 1 - Cadastro e Aprovação](../fase-1/fase-1-cadastro-e-aprovacao.md)
- [Estimativa de Horas Fase 2](./estimativa-horas-entrega-2.md)
- [Precificação Fase 2](./precificacao-entrega-2.md)
- [README Principal do Projeto](../../README.md)

---

*Documento sujeito a alterações conforme validação com stakeholders e equipe de desenvolvimento.*
