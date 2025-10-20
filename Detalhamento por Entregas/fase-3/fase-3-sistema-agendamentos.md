# Requisitos para Fase 3 - Data a Definir

**Data da Entrega:** A definir  
**Projeto:** Casa Mãe Paulistana  
**Responsável:** CodeBoa Software

---

## 📋 Escopo da Entrega

A Fase 3 implementa um **sistema completo de agendamentos** que se integra às funcionalidades entregues nas Fases 1 e 2, criando uma gestão unificada de agenda para todos os serviços da Casa Mãe Paulistana.

**Importante:** Esta fase **NÃO** inclui:
- Integração com sistemas externos de pagamento
- Sistema de videoconferência
- Aplicativo mobile nativo
- Documentação técnica detalhada

### Pré-requisitos
- Fase 1 concluída (Cadastro e Aprovação)
- Fase 2 concluída (Triagem, Atendimentos e Oficinas)
- Sistema de notificações funcional

---

## 📊 Resumo Executivo

### Objetivo
Criar um sistema completo de agendamentos que permita o gerenciamento eficiente da agenda de profissionais, salas e responsáveis, com notificações internas e controle de disponibilidade.

### Módulos da Fase 3

| Módulo | Descrição | Principais Funcionalidades |
|--------|-----------|---------------------------|
| **Agendamento de Triagem** | Agendamento manual pela equipe após aprovação do cadastro | • Seleção de horário disponível<br>• Bloqueio de agenda<br>• Notificações internas |
| **Agendamento de Atendimentos** | Agendamento de atendimentos especializados | • Agendamento por profissional<br>• Controle de conflitos<br>• Gestão de salas<br>• Reagendamentos |
| **Agendamento de Oficinas** | Bloqueio automático de agenda para oficinas | • Bloqueio de responsável<br>• Bloqueio de profissional/instrutor<br>• Sincronização com cadastro de oficinas |
| **Gestão de Disponibilidade** | Cadastro de horários e indisponibilidades | • Horário de trabalho<br>• Feriados<br>• Bloqueios personalizados<br>• Agenda por profissional |
| **Agenda Global** | Visualização unificada de todos os agendamentos | • Visão consolidada<br>• Filtros múltiplos<br>• Exportações<br>• Dashboard de ocupação |

### Estimativa de Complexidade

**Formulários/Interfaces:** 7 principais
- Interface de agendamento de triagem
- Formulário de agendamento de atendimento
- Cadastro de disponibilidade do profissional
- Cadastro de feriados/bloqueios
- Reagendamento
- Cancelamento de agendamento
- Gestão de salas

**Telas de Visualização:** 6 principais
- Agenda Global (calendário)
- Agenda por Profissional
- Agenda por Sala
- Agenda do Responsável
- Lista de Agendamentos
- Dashboard de Ocupação

**Funcionalidades Especiais:**
- Sistema de notificações internas
- Validações de conflitos múltiplos
- Cálculo de disponibilidade em tempo real
- Gestão de fila de espera
- Histórico de agendamentos
- Cancelamentos e reagendamentos
- Exportações e relatórios

---

## 1. Módulo de Agendamento de Triagem

**Descrição:** Sistema para a equipe agendar a triagem presencial após a aprovação do cadastro.

### 1.1 Agendamento pela Equipe

**Objetivo:** Permitir que a equipe agende a triagem após aprovação do cadastro.

**Fluxo:**
1. Cadastro aprovado pela equipe (Fase 1)
2. Equipe acessa lista de "Aprovados Aguardando Triagem"
3. Equipe seleciona responsável
4. Sistema exibe horários disponíveis
5. Equipe escolhe data e horário
6. Sistema confirma agendamento
7. Agenda do profissional é bloqueada automaticamente

### 1.2 Interface de Agendamento de Triagem

**Objetivo:** Interface para a equipe agendar triagens.

**Funcionalidades:**
- Visualização de horários disponíveis
- Calendário interativo ou lista de opções
- Filtro por período (manhã/tarde)
- Confirmação clara do horário escolhido
- Validação de disponibilidade em tempo real

### 1.3 Notificações Internas

**Objetivo:** Sistema básico de notificações internas.

**Notificações:**
- Notificação interna quando triagem é agendada
- Dashboard mostra agendamentos próximos
- Lista de triagens do dia/semana

### 1.4 Bloqueio de Agenda

**Objetivo:** Garantir que o horário escolhido fique reservado.

**Funcionalidades:**
- Bloqueio automático ao confirmar agendamento
- Reserva temporária durante seleção (timeout de 10 minutos)
- Liberação automática em caso de cancelamento
- Visualização do bloqueio na agenda do profissional

---

## 2. Módulo de Agendamento de Atendimentos

**Descrição:** Sistema para agendar atendimentos especializados com advogados, psicólogos e assistentes sociais, com controle completo de conflitos.

### 2.1 Criação de Agendamento

**Objetivo:** Permitir que a equipe agende atendimentos para os responsáveis.

**Dados do Agendamento:**
- Responsável a ser atendido
- Profissional selecionado
- Tipo de atendimento (primeira consulta, retorno, etc.)
- Data e horário
- Duração estimada
- Sala (se aplicável)
- Observações

**Funcionalidades:**
- Busca de responsável por nome/CPF
- Seleção de profissional por especialidade
- Visualização de horários disponíveis
- Sugestão de próximos horários livres
- Salvamento e confirmação

### 2.2 Validação de Conflitos

**Objetivo:** Evitar agendamentos simultâneos que gerem conflitos.

**Validações Automáticas:**
- ✓ Profissional não pode ter dois agendamentos no mesmo horário
- ✓ Responsável não pode ter dois agendamentos no mesmo horário
- ✓ Sala não pode estar ocupada no mesmo horário
- ✓ Profissional deve estar disponível (dentro do horário de trabalho)
- ✓ Verificar se não é feriado ou dia bloqueado

**Feedback ao Usuário:**
- Mensagens claras sobre conflitos encontrados
- Sugestão de horários alternativos
- Indicação visual de indisponibilidade

### 2.3 Gestão de Salas

**Objetivo:** Cadastrar e gerenciar salas de atendimento.

**Dados da Sala:**
- Nome/número da sala
- Capacidade
- Tipo (consultório, sala de grupo, etc.)
- Recursos disponíveis
- Status (ativa/inativa)

**Funcionalidades:**
- Cadastro de salas
- Visualização de ocupação por sala
- Reserva de sala para atendimentos
- Agenda por sala

### 2.4 Reagendamentos e Cancelamentos

**Objetivo:** Permitir alterações em agendamentos existentes.

**Reagendamento:**
- Buscar agendamento existente
- Selecionar novo horário
- Validar conflitos
- Liberar horário anterior
- Confirmar novo horário

**Cancelamento:**
- Buscar agendamento
- Registrar motivo do cancelamento
- Liberar horário na agenda
- Registrar no histórico

### 2.5 Notificações de Atendimento

**Objetivo:** Manter responsável e equipe informados.

**Notificações Internas:**
- Confirmação ao criar agendamento
- Alerta de agendamentos próximos
- Notificação de reagendamento
- Notificação de cancelamento

---

## 3. Módulo de Agendamento de Oficinas

**Descrição:** Bloqueio automático de agenda quando responsáveis e profissionais estão participando de oficinas.

### 3.1 Bloqueio Automático para Responsáveis

**Objetivo:** Evitar agendamento de atendimentos durante oficinas que o responsável participa.

**Funcionamento:**
- Ao inscrever responsável em oficina (Fase 2)
- Sistema identifica datas e horários da oficina
- Bloqueia automaticamente agenda do responsável nesses períodos
- Impede novos agendamentos de atendimento nos horários da oficina

**Validação:**
- Ao tentar agendar atendimento, verificar se responsável tem oficina
- Exibir mensagem clara: "Responsável possui oficina agendada neste horário"
- Sugerir horários alternativos

### 3.2 Bloqueio Automático para Profissionais/Instrutores

**Objetivo:** Reservar agenda do profissional que ministra a oficina.

**Funcionamento:**
- Ao cadastrar oficina com instrutor (Fase 2)
- Sistema identifica datas e horários da oficina
- Bloqueia automaticamente agenda do instrutor
- Impede agendamento de atendimentos para este profissional nos horários da oficina

**Funcionalidades:**
- Sincronização com cadastro de oficinas
- Atualização automática ao editar horários de oficina
- Liberação automática ao cancelar oficina
- Visualização na agenda do profissional

### 3.3 Visualização de Oficinas na Agenda

**Objetivo:** Exibir oficinas agendadas na agenda global e individual.

**Funcionalidades:**
- Oficinas aparecem na agenda global
- Diferenciação visual (cor diferente de atendimentos)
- Detalhes da oficina ao clicar
- Lista de participantes inscritos
- Status da oficina

---

## 4. Módulo de Gestão de Disponibilidade

**Descrição:** Sistema para cadastrar horários de trabalho, feriados e bloqueios personalizados dos profissionais.

### 4.1 Cadastro de Horário de Trabalho

**Objetivo:** Definir disponibilidade regular de cada profissional.

**Dados da Disponibilidade:**
- Profissional
- Dias da semana disponíveis
- Horário de início e fim por dia
- Intervalo para almoço/pausas
- Duração padrão de atendimentos

**Exemplo:**
- Segunda a Sexta: 8h às 12h e 14h às 18h
- Intervalo: 12h às 14h
- Duração de atendimento: 1 hora

**Funcionalidades:**
- Definir horários diferentes por dia da semana
- Criar exceções (ex: terças-feiras sai mais cedo)
- Ativar/desativar dias específicos
- Duplicar configuração para outros profissionais

### 4.2 Cadastro de Feriados

**Objetivo:** Bloquear agenda da Casa inteira em feriados.

**Dados do Feriado:**
- Nome do feriado
- Data
- Tipo (nacional, municipal, ponto facultativo)
- Se afeta todos os profissionais ou apenas alguns

**Funcionalidades:**
- Cadastrar feriados nacionais e municipais
- Importar lista de feriados do ano
- Bloquear agendamentos automaticamente
- Exibir feriados no calendário
- Editar/remover feriados

### 4.3 Bloqueios Personalizados

**Objetivo:** Permitir bloqueios específicos de agenda.

**Tipos de Bloqueio:**
- **Bloqueio por ausência:** Férias, licença médica, etc.
- **Bloqueio por evento:** Reunião, treinamento, etc.
- **Bloqueio de sala:** Manutenção, reforma, etc.
- **Bloqueio pontual:** Compromisso específico

**Dados do Bloqueio:**
- Tipo de bloqueio
- Profissional/Sala afetado
- Data e horário (início e fim)
- Motivo/Descrição
- Recorrência (se aplicável)

**Funcionalidades:**
- Criar bloqueios únicos ou recorrentes
- Editar e remover bloqueios
- Visualizar bloqueios na agenda
- Notificar equipe sobre bloqueios importantes

### 4.4 Gestão de Agenda Individual

**Objetivo:** Cada profissional visualiza e gerencia sua própria agenda.

**Funcionalidades:**
- Visualização de agenda pessoal
- Criar bloqueios pessoais
- Ver lista de atendimentos agendados
- Marcar atendimento como realizado
- Registrar observações pós-atendimento

---

## 5. Módulo de Agenda Global

**Descrição:** Visualização unificada de todos os agendamentos da Casa Mãe Paulistana.

### 5.1 Calendário Unificado

**Objetivo:** Fornecer visão geral de toda a operação da Casa.

**Visualizações:**
- **Visão Mensal:** Ocupação geral do mês
- **Visão Semanal:** Detalhamento da semana
- **Visão Diária:** Agenda completa do dia
- **Visão por Profissional:** Foco em um profissional
- **Visão por Sala:** Ocupação de salas

**Elementos Exibidos:**
- Triagens agendadas
- Atendimentos especializados
- Oficinas
- Bloqueios
- Feriados

**Diferenciação Visual:**
- Cores diferentes por tipo de agendamento
- Ícones indicativos
- Indicação de status (confirmado, pendente, realizado)

### 5.2 Filtros e Configurações

**Objetivo:** Permitir personalização da visualização da agenda.

**Filtros Disponíveis:**
- ☑️ Mostrar Triagens
- ☑️ Mostrar Atendimentos
  - ☑️ Advogado
  - ☑️ Psicólogo
  - ☑️ Assistente Social
- ☑️ Mostrar Oficinas
- ☑️ Mostrar Bloqueios
- ☑️ Mostrar Feriados

**Filtros Adicionais:**
- Por profissional específico
- Por sala
- Por responsável
- Por período
- Por status

**Funcionalidades:**
- Salvar configuração de filtros preferida
- Exportar agenda filtrada
- Imprimir agenda

### 5.3 Detalhes de Agendamento

**Objetivo:** Exibir informações completas ao clicar em um agendamento.

**Informações Exibidas:**
- Tipo de agendamento
- Responsável (nome, contato)
- Profissional
- Sala
- Horário (início e fim)
- Status
- Observações
- Histórico de alterações

**Ações Disponíveis:**
- Editar agendamento
- Reagendar
- Cancelar
- Marcar como realizado
- Adicionar observações
- Ver perfil do responsável

### 5.4 Dashboard de Ocupação

**Objetivo:** Fornecer indicadores de uso da agenda.

**Métricas Exibidas:**
- Taxa de ocupação geral
- Taxa de ocupação por profissional
- Taxa de ocupação por sala
- Agendamentos do dia/semana/mês
- Taxa de comparecimento
- Taxa de cancelamento
- Horários mais procurados
- Horários ociosos

**Visualizações:**
- Gráficos de ocupação
- Tabelas comparativas
- Indicadores coloridos (verde/amarelo/vermelho)
- Tendências ao longo do tempo

### 5.5 Exportações e Relatórios

**Objetivo:** Permitir análise e compartilhamento de dados.

**Relatórios Disponíveis:**
- Agenda completa (Excel/PDF)
- Agendamentos por profissional
- Agendamentos por responsável
- Ocupação de salas
- Faltas e cancelamentos
- Comparativo mensal

**Funcionalidades:**
- Exportar para Excel/CSV
- Exportar para PDF
- Enviar por email
- Filtrar antes de exportar

---

## ✅ Checklist de Implementação

### 1. Agendamento de Triagem

- [ ] **Agendamento pela Equipe**
  - [ ] Lista de aprovados aguardando triagem
  - [ ] Interface de agendamento
  - [ ] Visualização de horários disponíveis
  - [ ] Confirmação de agendamento

- [ ] **Interface de Agendamento**
  - [ ] Calendário/lista de horários disponíveis
  - [ ] Cálculo de disponibilidade em tempo real
  - [ ] Reserva temporária (timeout)
  - [ ] Confirmação de agendamento

- [ ] **Notificações Internas**
  - [ ] Notificação de agendamento criado
  - [ ] Dashboard de agendamentos próximos
  - [ ] Lista de triagens do dia

- [ ] **Bloqueio de Agenda**
  - [ ] Bloqueio automático ao confirmar
  - [ ] Liberação ao cancelar
  - [ ] Integração com agenda do profissional

### 2. Agendamento de Atendimentos

- [ ] **Formulário de Agendamento**
  - [ ] Seleção de responsável
  - [ ] Seleção de profissional por especialidade
  - [ ] Seleção de data e horário
  - [ ] Seleção de sala
  - [ ] Duração do atendimento

- [ ] **Validação de Conflitos**
  - [ ] Verificar disponibilidade do profissional
  - [ ] Verificar disponibilidade do responsável
  - [ ] Verificar disponibilidade da sala
  - [ ] Verificar feriados e bloqueios
  - [ ] Sugestão de horários alternativos

- [ ] **Gestão de Salas**
  - [ ] Cadastro de salas
  - [ ] Visualização de ocupação
  - [ ] Reserva de sala

- [ ] **Reagendamento**
  - [ ] Buscar agendamento existente
  - [ ] Selecionar novo horário
  - [ ] Revalidar conflitos
  - [ ] Notificação interna

- [ ] **Cancelamento**
  - [ ] Registrar motivo
  - [ ] Liberar horários
  - [ ] Notificação interna
  - [ ] Histórico de cancelamentos

- [ ] **Notificações**
  - [ ] Confirmação de agendamento
  - [ ] Alertas de agendamentos próximos
  - [ ] Notificação de alterações

### 3. Agendamento de Oficinas

- [ ] **Bloqueio para Responsáveis**
  - [ ] Identificar oficinas do responsável
  - [ ] Bloquear horários automaticamente
  - [ ] Validar ao agendar atendimento
  - [ ] Mensagem de conflito clara

- [ ] **Bloqueio para Instrutores**
  - [ ] Identificar instrutor da oficina
  - [ ] Bloquear agenda automaticamente
  - [ ] Sincronizar com edições de oficina
  - [ ] Liberar ao cancelar oficina

- [ ] **Visualização de Oficinas**
  - [ ] Exibir na agenda global
  - [ ] Diferenciação visual
  - [ ] Detalhes da oficina
  - [ ] Lista de participantes

### 4. Gestão de Disponibilidade

- [ ] **Horário de Trabalho**
  - [ ] Cadastro de disponibilidade regular
  - [ ] Configuração por dia da semana
  - [ ] Definir intervalos
  - [ ] Duração padrão de atendimentos

- [ ] **Cadastro de Feriados**
  - [ ] Formulário de feriado
  - [ ] Importação de lista anual
  - [ ] Bloqueio automático de agenda
  - [ ] Visualização no calendário

- [ ] **Bloqueios Personalizados**
  - [ ] Criar bloqueios únicos
  - [ ] Bloqueios recorrentes
  - [ ] Editar/remover bloqueios
  - [ ] Tipos de bloqueio (férias, reunião, etc.)

- [ ] **Agenda Individual do Profissional**
  - [ ] Visualização pessoal
  - [ ] Criar bloqueios pessoais
  - [ ] Lista de atendimentos
  - [ ] Marcar como realizado

### 5. Agenda Global

- [ ] **Calendário Unificado**
  - [ ] Visão mensal
  - [ ] Visão semanal
  - [ ] Visão diária
  - [ ] Visão por profissional
  - [ ] Visão por sala

- [ ] **Filtros**
  - [ ] Filtro por tipo de agendamento
  - [ ] Filtro por profissional
  - [ ] Filtro por sala
  - [ ] Filtro por responsável
  - [ ] Filtro por período
  - [ ] Salvar configuração de filtros

- [ ] **Detalhes de Agendamento**
  - [ ] Modal com informações completas
  - [ ] Ações rápidas (editar, cancelar, reagendar)
  - [ ] Ver perfil do responsável
  - [ ] Histórico de alterações

- [ ] **Dashboard de Ocupação**
  - [ ] Métricas de ocupação
  - [ ] Taxa de comparecimento
  - [ ] Gráficos de tendência
  - [ ] Indicadores visuais

- [ ] **Exportações**
  - [ ] Exportar para Excel/CSV
  - [ ] Exportar para PDF
  - [ ] Relatórios personalizados
  - [ ] Filtrar antes de exportar

### 6. Funcionalidades Transversais

- [ ] **Integração WhatsApp**
  - [ ] Configuração de API
  - [ ] Templates de mensagens
  - [ ] Log de envios
  - [ ] Tratamento de erros

- [ ] **Sistema de Notificações**
  - [ ] Agendador de notificações
  - [ ] Fila de processamento
  - [ ] Retry em caso de falha
  - [ ] Dashboard de monitoramento

- [ ] **Permissões**
  - [ ] Admin: acesso completo
  - [ ] Profissionais: sua agenda + criar agendamentos
  - [ ] Recepção: criar e gerenciar agendamentos
  - [ ] Coordenadores: visualização geral

- [ ] **UX/UI**
  - [ ] Design responsivo
  - [ ] Acessibilidade
  - [ ] Feedback visual claro
  - [ ] Confirmações para ações críticas

---

## 🔄 Fluxos Principais do Sistema

### Fluxo 1: Agendamento de Triagem pela Equipe

```
1. CADASTRO APROVADO (Fase 1)
   ↓
2. EQUIPE ACESSA SISTEMA
   ├─ Visualiza "Aprovados Aguardando Triagem"
   └─ Seleciona responsável para agendar
   ↓
3. SELEÇÃO DE HORÁRIO
   ├─ Sistema exibe horários disponíveis
   ├─ Equipe escolhe data e horário
   └─ Sistema valida disponibilidade
   ↓
4. BLOQUEIO DE AGENDA
   ├─ Sistema valida disponibilidade
   ├─ Bloqueia horário na agenda do profissional
   └─ Confirma agendamento
   ↓
5. NOTIFICAÇÃO INTERNA
   ├─ Dashboard atualizado
   ├─ Agendamento aparece na agenda global
   └─ Profissional visualiza em sua agenda
   ↓
6. TRIAGEM REALIZADA
   └─ Profissional marca como concluída
```

### Fluxo 2: Agendamento de Atendimento Especializado

```
1. RESPONSÁVEL TRIADO (Fase 2)
   ↓
2. EQUIPE AGENDA ATENDIMENTO
   ├─ Acessa sistema
   ├─ Busca responsável
   └─ Seleciona "Novo Agendamento"
   ↓
3. PREENCHIMENTO DO FORMULÁRIO
   ├─ Seleciona profissional (ex: Psicólogo)
   ├─ Escolhe data e horário
   ├─ Sistema exibe disponibilidade
   └─ Seleciona sala (se necessário)
   ↓
4. VALIDAÇÃO DE CONFLITOS
   ├─ ✓ Profissional disponível?
   ├─ ✓ Responsável disponível?
   ├─ ✓ Sala disponível?
   ├─ ✓ Não é feriado?
   └─ ✓ Dentro do horário de trabalho?
   ↓
5. CONFIRMAÇÃO
   ├─ Se OK: salva agendamento
   ├─ Se conflito: sugere alternativas
   └─ Bloqueia agenda automaticamente
   ↓
6. NOTIFICAÇÕES INTERNAS
   ├─ Sistema: notifica profissional
   └─ Dashboard atualizado
   ↓
7. ATENDIMENTO REALIZADO
   ├─ Profissional marca como concluído
   └─ Registra observações (Fase 2)
```

### Fluxo 3: Bloqueio Automático para Oficina

```
1. OFICINA CADASTRADA (Fase 2)
   ├─ Data: Terças-feiras
   ├─ Horário: 14h às 16h
   ├─ Instrutor: Profissional X
   └─ 15 inscritos
   ↓
2. BLOQUEIO AUTOMÁTICO
   ├─ Sistema identifica horários da oficina
   ├─ Bloqueia agenda de todos os 15 responsáveis
   └─ Bloqueia agenda do Profissional X
   ↓
3. TENTATIVA DE AGENDAMENTO
   ├─ Equipe tenta agendar atendimento
   ├─ Para um dos responsáveis inscritos
   └─ Terça às 14h30
   ↓
4. VALIDAÇÃO DE CONFLITO
   ├─ Sistema detecta: "Responsável tem oficina"
   ├─ Exibe mensagem clara
   └─ Sugere outros horários
   ↓
5. SINCRONIZAÇÃO CONTÍNUA
   ├─ Se oficina for editada: atualiza bloqueios
   ├─ Se oficina cancelada: libera bloqueios
   └─ Se responsável desinscrever: libera sua agenda
```

### Fluxo 4: Gestão de Disponibilidade do Profissional

```
1. CADASTRO DE HORÁRIO DE TRABALHO
   ├─ Admin acessa perfil do profissional
   ├─ Define horários por dia da semana
   ├─ Ex: Seg-Sex 8h-12h / 14h-18h
   └─ Duração de atendimento: 1h
   ↓
2. CADASTRO DE FERIADOS
   ├─ Admin cadastra feriado (ex: 25/12)
   └─ Sistema bloqueia dia para todos
   ↓
3. BLOQUEIO PERSONALIZADO
   ├─ Profissional solicita férias (01/02 a 15/02)
   ├─ Admin cria bloqueio
   └─ Agenda bloqueada no período
   ↓
4. CÁLCULO DE DISPONIBILIDADE
   ├─ Sistema considera:
   │   ├─ Horário de trabalho cadastrado
   │   ├─ Feriados
   │   ├─ Bloqueios personalizados
   │   ├─ Agendamentos existentes
   │   └─ Oficinas que ministra
   └─ Exibe apenas horários realmente disponíveis
   ↓
5. VISUALIZAÇÃO NA AGENDA
   └─ Todos os bloqueios aparecem na agenda global
```

### Fluxo 5: Visualização da Agenda Global

```
1. ACESSO À AGENDA GLOBAL
   ├─ Usuário acessa módulo
   └─ Visualização mensal padrão
   ↓
2. APLICAÇÃO DE FILTROS
   ├─ Habilita: Atendimentos, Oficinas
   ├─ Desabilita: Triagens
   ├─ Filtra: Apenas Psicólogo
   └─ Período: Esta semana
   ↓
3. VISUALIZAÇÃO CONSOLIDADA
   ├─ Cores diferentes por tipo
   ├─ Ícones indicativos
   └─ Informações resumidas
   ↓
4. DETALHAMENTO
   ├─ Clica em agendamento
   ├─ Abre modal com detalhes completos
   └─ Ações disponíveis (editar, cancelar)
   ↓
5. EXPORTAÇÃO
   ├─ Seleciona "Exportar"
   ├─ Escolhe formato (Excel/PDF)
   └─ Download do arquivo filtrado
```

---

## 📝 Notas Importantes

### Considerações Técnicas

**Integração com Sistema Existente:**
- Sincronização com dados das Fases 1 e 2
- Reutilização de componentes e infraestrutura
- Extensão do banco de dados existente

**Performance:**
- Cálculo de disponibilidade deve ser rápido
- Otimizar consultas ao buscar horários disponíveis
- Considerar cache para horários de trabalho e feriados
- Indexação adequada no banco de dados

**Validações Críticas:**
- Todos os conflitos devem ser validados no backend
- Não confiar apenas em validações do frontend
- Transações atômicas ao criar agendamentos
- Lock otimista para evitar double-booking

**Notificações:**
- Sistema de notificações internas
- Dashboard para visualizar agendamentos próximos
- Log de ações importantes

### Regras de Negócio

**Duração de Atendimentos:**
- Triagem: 1 hora
- Atendimento especializado: configurável por profissional (padrão 1h)
- Oficinas: duração definida no cadastro

**Horários Permitidos:**
- Intervalo mínimo entre atendimentos: 15 minutos (limpeza/preparação)
- Respeitar horário de almoço configurado
- Não permitir agendamentos fora do horário de trabalho

**Cancelamentos:**
- Permitir cancelamento com antecedência mínima
- Registrar motivo obrigatoriamente
- Notificar todas as partes envolvidas

**Reagendamentos:**
- Limites de reagendamentos configuráveis
- Histórico completo de alterações

### Permissões

**Administrador:**
- Acesso completo a todas as funcionalidades
- Criar, editar, cancelar qualquer agendamento
- Gerenciar disponibilidade de todos
- Visualizar agenda global sem restrições

**Profissionais:**
- Visualizar sua própria agenda
- Criar bloqueios pessoais
- Marcar atendimentos como realizados
- Adicionar observações pós-atendimento
- Visualizar detalhes de seus atendimentos

**Recepção:**
- Criar agendamentos de triagem e atendimentos
- Reagendar e cancelar
- Visualizar agenda global
- Não pode alterar disponibilidade de profissionais

**Coordenadores:**
- Visualização completa da agenda
- Dashboard com métricas
- Exportação de relatórios
- Não pode criar/editar agendamentos (apenas visualizar)

---

### Perguntas/Decisões Pendentes

- [ ] Sistema de fila de espera para horários concorridos?
- [ ] Permitir agendamento online pelo responsável ou apenas via equipe?
- [ ] Integração com Google Calendar dos profissionais?
- [ ] Sistema de avaliação pós-atendimento?
- [ ] Política de cancelamento e reagendamento (limites, prazos)?
- [ ] Notificações por email além do sistema interno?

---

## 🎯 Resumo de Funcionalidades

### Funcionalidades Principais

**1. Agendamento de Triagem**
- Agendamento pela equipe após aprovação
- Interface de seleção de horário
- Bloqueio automático de agenda
- Notificações internas

**2. Agendamento de Atendimentos**
- Formulário completo de agendamento
- Validação de conflitos múltiplos
- Gestão de salas
- Reagendamento e cancelamento
- Notificações internas

**3. Agendamento de Oficinas**
- Bloqueio automático para responsáveis inscritos
- Bloqueio automático para instrutores
- Sincronização com cadastro de oficinas (Fase 2)

**4. Gestão de Disponibilidade**
- Cadastro de horário de trabalho por profissional
- Cadastro de feriados
- Bloqueios personalizados (férias, reuniões)
- Agenda individual do profissional

**5. Agenda Global**
- Visualização unificada (mensal, semanal, diária)
- Filtros múltiplos e personalizáveis
- Dashboard de ocupação
- Exportações e relatórios
- Detalhamento completo de agendamentos

**6. Transversal**
- Sistema de notificações internas
- Controle de permissões
- Histórico de alterações
- Logs de ações importantes

---

## 🔗 Referências

- [Requisitos Fase 1 - Cadastro e Aprovação](../fase-1/fase-1-cadastro-e-aprovacao.md)
- [Requisitos Fase 2 - Triagem, Atendimentos e Oficinas](./fase-2-triagem-atendimentos-oficinas.md)
- [README Principal do Projeto](../../README.md)

---

*Documento sujeito a alterações conforme validação com stakeholders e equipe de desenvolvimento.*
