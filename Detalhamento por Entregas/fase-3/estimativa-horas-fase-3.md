# Estimativa de Horas - Fase 3

**Projeto:** Casa Mãe Paulistana  
**Entrega:** Sistema de Agendamentos (Fase 3)  
**Data de Entrega:** A definir  
**Data da Estimativa:** Outubro 2025  
**Versão:** 1.0

---

## 📊 Resumo Executivo

| Disciplina | Horas | % do Total | Complexidade |
|-----------|-------|------------|--------------|
| **1. Análise e Planejamento** | 24h | 13% | Alta |
| **2. Setup de Infraestrutura** | 3h | 2% | Baixa |
| **3. Backend Development** | 73h | 40% | Muito Alta |
| **4. Frontend Development** | 57h | 31% | Alta |
| **5. Integração e Testes** | 21h | 11% | Alta |
| **6. Documentação e Deploy** | 7h | 4% | Baixa |
| **TOTAL BASE** | **185h** | **100%** | |

### Margem de Contingência
```
Horas base: 185h
Margem para imprevistos (+15%): 28h
───────────────────────────────────
TOTAL COM MARGEM: 213h
```

**Justificativa da margem:**
- Sistema de agendamentos é altamente complexo (conflitos, validações múltiplas)
- Sistema de notificações internas com alertas
- Cálculo de disponibilidade em tempo real é crítico
- Sincronização entre múltiplos módulos (Triagem, Atendimentos, Oficinas)
- Agenda global requer otimizações de performance
- Edge cases e validações de negócio não previstos

---

## ⏱️ Detalhamento por Disciplina

### 1. Análise e Planejamento

| Atividade | Horas | Complexidade |
|-----------|-------|--------------|
| Refinamento de requisitos (4 módulos de agendamento) | 9h | Alta |
| Modelagem de dados (agendamentos, disponibilidade, bloqueios) | 4h | Alta |
| Design do sistema de conflitos e validações | 5h | Muito Alta |
| Arquitetura de notificações internas | 2h | Média |
| Design do calendário global e filtros | 3h | Média-Alta |
| Planejamento de testes (múltiplos cenários) | 1h | Alta |

**Subtotal:** 24h

**Justificativa:** 
- **Complexidade Muito Alta:** Sistema de agendamentos é o mais complexo do projeto
- **4 módulos interdependentes:** Triagem, Atendimentos, Oficinas, Disponibilidade, Agenda Global
- **Validações Críticas:** Profissional, Responsável, Sala, Feriados, Bloqueios, Oficinas
- **Notificações Internas:** Sistema simplificado sem integrações externas
- **Performance:** Cálculo de disponibilidade em tempo real para múltiplos profissionais

**Novas Entidades/Conceitos:**
- Agendamento (unificado para Triagem e Atendimentos)
- Disponibilidade do Profissional
- Feriado
- Bloqueio Personalizado
- Sala
- Notificação Interna

---

### 2. Setup de Infraestrutura

| Atividade | Horas | Complexidade |
|-----------|-------|--------------|
| Configuração de sistema de notificações internas | 2h | Baixa-Média |
| Configuração de logs e monitoring | 1h | Baixa |

**Subtotal:** 3h

**Justificativa:** 
- **Notificações Internas:** Sistema simplificado sem APIs externas
- **Sem WhatsApp:** Economia de 9h (API, Queue, Scheduler)
- ✅ **Infraestrutura GCP já existente:** Cloud Run, Cloud SQL já configurados
- Apenas extensões mínimas para suportar sistema de agendamentos

---

### 3. Backend Development (.NET)

| Atividade | Horas | Complexidade |
|-----------|-------|--------------|
| **MÓDULO 1: AGENDAMENTO DE TRIAGEM** | | |
| Models e DTOs (Agendamento, Notificação) | 2h | Média |
| API de disponibilidade para triagem | 4h | Alta |
| Sistema de reserva temporária (timeout) | 3h | Alta |
| Notificações internas básicas | 2h | Média |
| **MÓDULO 2: AGENDAMENTO DE ATENDIMENTOS** | | |
| Serviço de Agendamentos (CRUD completo) | 6h | Alta |
| Motor de validação de conflitos | 10h | Muito Alta |
| Sugestão de horários alternativos | 5h | Alta |
| Reagendamento com validações | 4h | Alta |
| Cancelamento com histórico | 3h | Média |
| **MÓDULO 3: GESTÃO DE SALAS** | | |
| CRUD de Salas | 2h | Baixa |
| Validação de ocupação de sala | 3h | Média-Alta |
| **MÓDULO 4: BLOQUEIO AUTOMÁTICO DE OFICINAS** | | |
| Sincronização com cadastro de oficinas (Fase 2) | 4h | Alta |
| Bloqueio automático de responsáveis inscritos | 4h | Alta |
| Bloqueio automático de instrutores | 3h | Média-Alta |
| Validação ao agendar (responsável em oficina) | 3h | Média-Alta |
| **MÓDULO 5: GESTÃO DE DISPONIBILIDADE** | | |
| CRUD de Horário de Trabalho | 4h | Média |
| CRUD de Feriados | 2h | Baixa-Média |
| CRUD de Bloqueios Personalizados | 4h | Média |
| Cálculo de disponibilidade agregada | 6h | Muito Alta |
| **MÓDULO 6: AGENDA GLOBAL** | | |
| API de consulta unificada (todos os tipos) | 5h | Alta |
| Sistema de filtros múltiplos | 4h | Média-Alta |
| Dashboard de ocupação (métricas) | 4h | Média-Alta |
| Exportações (Excel/PDF) para agenda | 3h | Média |
| **FUNCIONALIDADES TRANSVERSAIS** | | |
| Middleware de auditoria para agendamentos | 2h | Baixa-Média |
| Testes automatizados (backend) | 8h | Alta |

**Subtotal:** 73h

**Justificativa da complexidade:**

**Muito Alta Complexidade:**
1. **Motor de Validação de Conflitos (10h):**
   - ✓ Profissional disponível (horário de trabalho + bloqueios + agendamentos)
   - ✓ Responsável disponível (agendamentos + oficinas inscritas)
   - ✓ Sala disponível (agendamentos existentes)
   - ✓ Não é feriado
   - ✓ Dentro do horário de expediente
   - ✓ Respeitar duração mínima entre atendimentos
   - Lógica complexa com múltiplas queries e validações em tempo real

2. **Cálculo de Disponibilidade Agregada (6h):**
   - Considerar: horário de trabalho + feriados + bloqueios + agendamentos + oficinas
   - Performance otimizada (cache, indexação)
   - Retornar slots disponíveis por profissional/sala
   - Sugestão inteligente de horários

**Alta Complexidade:**
- **Sugestão de Horários Alternativos (5h):** Algoritmo para encontrar próximos slots disponíveis
- **Bloqueios Automáticos (11h total):** Sincronização com oficinas da Fase 2
- **Reagendamento (4h):** Liberar horário antigo + validar novo + notificar

**Redução vs estimativa com WhatsApp:**
- Serviço de WhatsApp: -8h
- Sistema de lembretes automáticos: -5h
- Sistema de notificações (queue + retry): -6h
- Testes de WhatsApp: -2h
- **Total economizado: -21h**

✅ **Reutilização:** MediatR, EntityFramework, padrões da Fase 1 e 2

---

### 4. Frontend Development (React + Lovable)

| Atividade | Horas | Complexidade |
|-----------|-------|--------------|
| **LOVABLE AI - Geração de Telas** | 11h | Média |
| **Migração/Ajustes do código Lovable para API** | 7h | Média |
| **MÓDULO 1: AGENDAMENTO DE TRIAGEM** | | |
| Interface de agendamento (calendário) | 4h | Média-Alta |
| Tela de confirmação e detalhes | 1h | Baixa |
| **MÓDULO 2: AGENDAMENTO DE ATENDIMENTOS** | | |
| Formulário completo de agendamento | 5h | Alta |
| Visualização de disponibilidade (calendário) | 4h | Alta |
| Modal de reagendamento | 2h | Média |
| Modal de cancelamento | 1h | Baixa-Média |
| **MÓDULO 3: GESTÃO DE SALAS** | | |
| CRUD de Salas | 2h | Baixa |
| **MÓDULO 4: GESTÃO DE DISPONIBILIDADE** | | |
| Formulário de Horário de Trabalho | 3h | Média |
| Calendário de Feriados | 2h | Baixa-Média |
| Formulário de Bloqueios Personalizados | 2h | Média |
| Agenda Individual do Profissional | 3h | Média |
| **MÓDULO 5: AGENDA GLOBAL** | | |
| Calendário Unificado (mensal/semanal/diária) | 8h | Muito Alta |
| Sistema de Filtros Múltiplos | 3h | Média |
| Modal de Detalhes de Agendamento | 2h | Baixa-Média |
| Dashboard de Ocupação (gráficos) | 3h | Média |
| Exportações (Excel/PDF) | 1h | Baixa |
| **FUNCIONALIDADES TRANSVERSAIS** | | |
| Validações client-side (disponibilidade) | 2h | Média |
| Tratamento de erros e loading states | 2h | Média |

**Subtotal:** 57h

**Justificativa da complexidade:**

**Muito Alta Complexidade:**
- **Calendário Unificado (8h):** 
  - Múltiplas visualizações (mensal, semanal, diária)
  - Diferentes tipos de eventos (triagem, atendimentos, oficinas, bloqueios)
  - Cores e ícones diferenciados
  - Performance com muitos eventos
  - Drag and drop (opcional)

**Alta Complexidade:**
- **Formulário de Agendamento (5h):** Seleção de profissional, responsável, sala, data/hora, validações em tempo real
- **Visualização de Disponibilidade (4h):** Calendário interativo mostrando slots disponíveis/ocupados

**Redução vs estimativa com WhatsApp:**
- Interface específica para WhatsApp: -1h (Lovable)
- Ajustes de integração: -1h
- Telas de configuração de templates: -3h
- **Total economizado: -5h**

✅ **Reutilização:**
- App Admin já existente (Fases 1 e 2)
- Componentes Shadcn/UI configurados
- Layout e navegação estabelecidos
- Biblioteca de calendário (react-big-calendar ou similar)

---

### 5. Integração e Testes

| Atividade | Horas | Complexidade |
|-----------|-------|--------------|
| Testes de integração (API + DB) - 4 módulos | 8h | Alta |
| Testes de validação de conflitos (múltiplos cenários) | 6h | Muito Alta |
| Testes de notificações internas | 2h | Média |
| Testes de bloqueios automáticos (oficinas) | 2h | Média |
| Testes de fluxos completos (E2E) | 3h | Média-Alta |

**Subtotal:** 21h

**Justificativa:** 
- **Validação de Conflitos (6h):** Múltiplos cenários a testar
  - Profissional com múltiplos agendamentos
  - Responsável em oficina tentando agendar
  - Sala ocupada no mesmo horário
  - Feriados e bloqueios
  - Horário fora do expediente
  
- **Notificações Internas (2h):** Sistema simplificado, sem APIs externas
- ✅ **Infraestrutura de testes já existente** das Fases 1 e 2

**Redução vs estimativa com WhatsApp:**
- Testes de integração WhatsApp: -4h
- Testes de lembretes automáticos: -3h
- **Total economizado: -7h**

---

### 6. Documentação e Deploy

| Atividade | Horas | Complexidade |
|-----------|-------|--------------|
| Documentação de API (novos endpoints) | 2h | Baixa-Média |
| Documentação de uso do sistema de agendamentos | 3h | Baixa-Média |
| Deploy em ambiente de produção (incremental) | 1h | Baixa |
| Handover e treinamento da equipe | 1h | Baixa |

**Subtotal:** 7h

**Justificativa da redução:** 
- ✅ **Estrutura de documentação já existente**
- ✅ **Pipeline de deploy configurado**
- ✅ **Equipe já familiarizada com o sistema**
- Apenas documentação incremental do sistema de agendamentos
- **Sem WhatsApp:** -2h de documentação de integração e templates

---

## 👥 Perfis de Desenvolvedores Necessários

### Full-Stack Developer Sênior (React + .NET)
- Responsável por arquitetura do sistema de agendamentos
- Motor de validação de conflitos
- Sistema de notificações internas
- Calendário global
- Code review
- Testes (unitários, integração, E2E)
- **100% do projeto = 185h**
- **Taxa horária sugerida:** R$ 200/h

**Justificativa do perfil Sênior:**
- Complexidade muito alta do motor de validações
- Performance do cálculo de disponibilidade
- Sistema de agendamentos é crítico para operação
- Experiência com calendários e agendamentos

---

## 🎯 Distribuição de Horas por Submódulo

### Submódulo 1: Agendamento de Triagem

**Prazo:** 1 semana

| Disciplina | Horas |
|-----------|-------|
| Análise e Planejamento | 6h |
| Setup de Infraestrutura (notificações internas) | 2h |
| Backend Development | 11h |
| Frontend Development (Lovable + ajustes) | 10h |
| Integração e Testes | 4h |
| Documentação | 2h |
| **TOTAL SUBMÓDULO 1** | **35h** |

**Entregas:**
- ✅ Interface de agendamento pela equipe
- ✅ Lista de aprovados aguardando triagem
- ✅ Visualização de horários disponíveis
- ✅ Sistema de reserva temporária
- ✅ Bloqueio automático de agenda
- ✅ Notificações internas básicas

---

### Submódulo 2: Agendamento de Atendimentos + Gestão de Salas

**Prazo:** 2-3 semanas

| Disciplina | Horas |
|-----------|-------|
| Análise e Planejamento | 8h |
| Setup de Infraestrutura | 0h |
| Backend Development | 33h |
| Frontend Development (Lovable + ajustes) | 14h |
| Integração e Testes | 8h |
| Documentação | 1h |
| **TOTAL SUBMÓDULO 2** | **64h** |

**Entregas:**
- ✅ Formulário completo de agendamento
- ✅ Motor de validação de conflitos (6 validações)
- ✅ CRUD de Salas
- ✅ Sugestão de horários alternativos
- ✅ Reagendamento com validações
- ✅ Cancelamento com motivo e histórico
- ✅ Notificações de confirmação e alterações
- ✅ Visualização de disponibilidade

---

### Submódulo 3: Bloqueio Automático de Oficinas

**Prazo:** 1 semana

| Disciplina | Horas |
|-----------|-------|
| Análise e Planejamento | 3h |
| Backend Development | 14h |
| Frontend Development (ajustes) | 2h |
| Integração e Testes | 2h |
| Documentação | 1h |
| **TOTAL SUBMÓDULO 3** | **22h** |

**Entregas:**
- ✅ Sincronização com cadastro de oficinas (Fase 2)
- ✅ Bloqueio automático de responsáveis inscritos
- ✅ Bloqueio automático de instrutores
- ✅ Validação ao tentar agendar durante oficina
- ✅ Mensagens claras de conflito
- ✅ Visualização de oficinas na agenda

---

### Submódulo 4: Gestão de Disponibilidade

**Prazo:** 1-2 semanas

| Disciplina | Horas |
|-----------|-------|
| Análise e Planejamento | 4h |
| Backend Development | 16h |
| Frontend Development (Lovable + ajustes) | 10h |
| Integração e Testes | 3h |
| Documentação | 1h |
| **TOTAL SUBMÓDULO 4** | **34h** |

**Entregas:**
- ✅ Cadastro de Horário de Trabalho por profissional
- ✅ Cadastro de Feriados
- ✅ CRUD de Bloqueios Personalizados
- ✅ Cálculo de disponibilidade agregada
- ✅ Agenda Individual do Profissional
- ✅ Visualização de bloqueios no calendário

---

### Submódulo 5: Agenda Global + Dashboard

**Prazo:** 2 semanas

| Disciplina | Horas |
|-----------|-------|
| Análise e Planejamento | 3h |
| Setup de Infraestrutura | 1h |
| Backend Development | 11h |
| Frontend Development (Lovable + ajustes) | 17h |
| Integração e Testes | 6h |
| Documentação | 1h |
| **TOTAL SUBMÓDULO 5** | **39h** |

**Entregas:**
- ✅ Calendário Unificado (mensal/semanal/diária)
- ✅ Visualização por profissional/sala
- ✅ Sistema de filtros múltiplos
- ✅ Detalhes completos de agendamento
- ✅ Dashboard de ocupação (métricas + gráficos)
- ✅ Exportações (Excel/PDF)
- ✅ Ações rápidas (editar, cancelar, reagendar)

---

## 📅 Cronograma Estimado

### Timeline Total: 5-7 semanas

```
Semana 1: Agendamento de Triagem (35h)
├─ Análise detalhada do sistema de agendamentos (6h)
├─ Setup notificações internas (2h)
├─ Backend: Disponibilidade + Notificações (11h)
├─ Frontend: Interface de agendamento (Lovable) (10h)
├─ Testes (4h)
└─ Documentação (2h)

Semanas 2-3: Agendamento de Atendimentos + Salas (64h)
├─ Análise de validações e conflitos (8h)
├─ Backend: Motor de validações (muito complexo) (33h)
│   ├─ Serviço de Agendamentos (6h)
│   ├─ Motor de conflitos (10h)
│   ├─ Sugestão de horários (5h)
│   ├─ Reagendamento (4h)
│   ├─ Cancelamento (3h)
│   └─ Salas (5h)
├─ Frontend: Formulário + Calendário (Lovable) (14h)
├─ Testes de validações (8h)
└─ Documentação (1h)

Semana 4: Bloqueio Automático de Oficinas (22h)
├─ Análise de sincronização (3h)
├─ Backend: Bloqueios automáticos (14h)
├─ Frontend: Ajustes (2h)
├─ Testes (2h)
└─ Documentação (1h)

Semanas 4-5: Gestão de Disponibilidade (34h)
├─ Análise de cálculo agregado (4h)
├─ Backend: Horários + Feriados + Bloqueios (16h)
├─ Frontend: Telas de configuração (Lovable) (10h)
├─ Testes (3h)
└─ Documentação (1h)

Semanas 6-7: Agenda Global + Dashboard (39h)
├─ Análise de performance (3h)
├─ Setup de cache e otimizações (1h)
├─ Backend: API unificada + Dashboard (11h)
├─ Frontend: Calendário + Filtros (Lovable) (17h)
├─ Testes E2E completos (6h)
└─ Deploy e handover (1h)

──────────────────────────────────────────
FASE 3 COMPLETA (5-7 semanas = 185h)
```

---

## 💡 Considerações e Premissas

### Stack Tecnológica (Reutilizada das Fases 1 e 2)
- **Frontend:** React + Vite + TypeScript + Shadcn/UI + Tailwind CSS (gerado via Lovable AI)
- **Backend:** .NET (ASP.NET Core) + Entity Framework + MediatR
- **Banco de Dados:** PostgreSQL (Cloud SQL) - **já existente**
- **Cloud:** Google Cloud Platform (GCP) - **infraestrutura já configurada**
- **Notificações:** Sistema interno (dashboard e alertas)
- **CI/CD:** GitHub Actions - **pipeline já funcional**

### Bibliotecas Adicionais
- **Frontend:** react-big-calendar ou FullCalendar (calendário)
- **Backend:** Hangfire (agendamento de tarefas) ou cron jobs
- **Excel:** EPPlus ou ClosedXML
- **PDF:** iTextSharp ou PuppeteerSharp

### Premissas
- ✅ Fase 1 e Fase 2 concluídas e em produção
- ✅ Infraestrutura GCP totalmente funcional
- ✅ App Admin interno já existente
- ✅ Sistema de backend operacional
- ✅ Banco de dados PostgreSQL configurado
- ✅ CI/CD configurado
- ✅ Equipe familiarizada com a stack tecnológica
- Lovable AI disponível para geração de telas
- Requisitos de agendamento estáveis
- Feedback do cliente disponível entre submódulos

### Economias em Relação às Fases Anteriores
- **Infraestrutura:** ~15h economizadas (GCP já configurado)
- **Setup de Projeto:** ~5h economizadas (estrutura já existente)
- **CI/CD:** ~3h economizadas (pipeline já funcional)
- **App Admin:** ~15h economizadas (layout e componentes reutilizados)
- **Sistema de autenticação:** ~8h economizadas (já implementado)
- **Permissões:** ~5h economizadas (sistema já existente, apenas extensões)
- **Exportações:** ~3h economizadas (biblioteca já configurada)
- **Total economizado:** ~54h

### Riscos que Podem Impactar Horas

**Alto Risco (+15-30h):**
- **Motor de Validação de Conflitos:** Edge cases complexos não previstos
- **Performance:** Cálculo de disponibilidade lento com muitos profissionais/agendamentos
- **Sincronização com Oficinas:** Complexidade não prevista ao integrar com Fase 2

**Médio Risco (+8-15h):**
- **Calendário Global:** Performance com muitos eventos, UX/UI complexa
- **Testes:** Cenários de conflito são numerosos e complexos

**Baixo Risco (+3-8h):**
- **Mudanças de requisitos:** Validações adicionais não previstas
- **Integração Lovable:** Ajustes no código gerado

---

## 📊 Comparação: Fase 3 vs Fases Anteriores

### Resumo Comparativo

| Métrica | Fase 1 | Fase 2 | Fase 3 | Tendência |
|---------|--------|--------|--------|-----------|
| **Horas Base** | 247h | 165h | 185h | ↗️ |
| **Horas com Margem** | 259h | 182h | 213h | ↗️ |
| **Margem de Contingência** | 5% | 10% | 15% | ↗️ |
| **Formulários Principais** | 1 | 6 | 7 | ↗️ |
| **Telas de Visualização** | 3 | 8+ | 6+ | → |
| **Módulos** | 1 | 3 | 4 | ↗️ |
| **Entidades de Dados** | 3 | 7 | 13 (+6) | ↗️ |
| **Complexidade Backend** | Alta | Alta | Muito Alta | ↗️ |
| **Complexidade Frontend** | Média-Alta | Média | Alta | ↗️ |
| **Integrações Externas** | 2 (Email, Storage) | 0 | 0 | → |

### Justificativa do Aumento de Horas vs Fase 2

**Aumento de 20h (+12%) em relação à Fase 2:**

1. **Análise e Planejamento (+3h):**
   - Fase 2: 21h
   - Fase 3: 24h
   - **Aumento: 3h** (complexidade muito alta do sistema de agendamentos)

2. **Setup de Infraestrutura (-2h):**
   - Fase 2: 5h
   - Fase 3: 3h
   - **Redução: 2h** (sem WhatsApp API, Queue, Scheduler)

3. **Backend Development (+22h):**
   - Fase 2: 51h (3 módulos relativamente independentes)
   - Fase 3: 73h (4 módulos altamente interdependentes + validações complexas)
   - **Aumento: 22h** (motor de conflitos muito complexo)

4. **Frontend Development (+3h):**
   - Fase 2: 54h (6 formulários + 8 telas)
   - Fase 3: 57h (7 formulários/interfaces + calendário complexo)
   - **Aumento: 3h** (calendário global é muito complexo)

5. **Integração e Testes (-3h):**
   - Fase 2: 24h
   - Fase 3: 21h
   - **Redução: 3h** (sem testes de WhatsApp e lembretes)

6. **Documentação e Deploy (-3h):**
   - Fase 2: 10h
   - Fase 3: 7h
   - **Redução: 3h** (sem documentação de WhatsApp)

**Total de Aumento: +20h (+12%)**

**Economia por não ter WhatsApp nesta fase: -49h**
- Planejamento arquitetura WhatsApp: -2h
- Infraestrutura (WhatsApp API + Queue + Scheduler): -9h
- Backend (serviço WhatsApp + lembretes + queue): -19h
- Frontend (interfaces específicas): -5h
- Testes (WhatsApp + lembretes): -7h
- Setup cache/scheduler avançado: -2h
- Testes E2E WhatsApp: -2h
- Backend testes adicionais: -2h
- Documentação WhatsApp: -1h

### Principais Drivers de Complexidade

**Por que Fase 3 ainda é complexa mesmo sem WhatsApp?**

1. **Motor de Validação de Conflitos (10h):**
   - Fase 2: Não tinha sistema de agendamentos
   - Fase 3: Valida 6+ condições diferentes em tempo real

2. **Cálculo de Disponibilidade (6h):**
   - Fase 2: Não existia
   - Fase 3: Algoritmo complexo considerando múltiplos fatores

3. **Calendário Global (8h):**
   - Fase 2: Listas e tabelas simples
   - Fase 3: Visualização complexa com múltiplos tipos de eventos

4. **Sincronização entre Módulos (14h):**
   - Fase 2: Módulos independentes
   - Fase 3: Agendamentos dependem de Triagem, Atendimentos, Oficinas, Disponibilidade

5. **Sugestão de Horários Alternativos (5h):**
   - Fase 2: Não existia
   - Fase 3: Algoritmo de busca inteligente

---

## 📈 Análise de Complexidade por Submódulo

### 1. Agendamento de Triagem
- **Complexidade:** Alta
- **Horas:** 35h (19% do total)
- **Justificativa:** Interface de agendamento pela equipe, notificações internas
- **Riscos:** Integração com dados da Fase 1

### 2. Agendamento de Atendimentos + Salas
- **Complexidade:** Muito Alta
- **Horas:** 64h (35% do total)
- **Justificativa:** Motor de validações complexo, múltiplas entidades, reagendamentos
- **Riscos:** Performance, edge cases não previstos

### 3. Bloqueio Automático de Oficinas
- **Complexidade:** Alta
- **Horas:** 22h (12% do total)
- **Justificativa:** Sincronização com sistema existente (Fase 2)
- **Riscos:** Integração com código legado

### 4. Gestão de Disponibilidade
- **Complexidade:** Alta
- **Horas:** 34h (18% do total)
- **Justificativa:** Cálculo agregado complexo, múltiplos tipos de bloqueios
- **Riscos:** Performance do cálculo

### 5. Agenda Global + Dashboard
- **Complexidade:** Muito Alta
- **Horas:** 39h (21% do total)
- **Justificativa:** Calendário complexo, múltiplos filtros, performance
- **Riscos:** UX/UI, performance com muitos eventos
- **Horas:** 34h (15% do total)
- **Justificativa:** Cálculo agregado complexo, múltiplos tipos de bloqueios
- **Riscos:** Performance do cálculo

### 5. Agenda Global + Dashboard
- **Complexidade:** Muito Alta
- **Horas:** 49h (21% do total)
- **Justificativa:** Calendário complexo, múltiplos filtros, performance
- **Riscos:** UX/UI, performance com muitos eventos

---

## ✅ Checklist de Validação

### Ao final do projeto, validar:

- [ ] Horas reais vs estimadas por disciplina
- [ ] Principais desvios e causas
- [ ] Precisão do uso de Lovable AI
- [ ] Performance do motor de validações
- [ ] Performance do calendário global
- [ ] Cálculo de disponibilidade em tempo real
- [ ] Testes em múltiplos cenários de conflito
- [ ] Aprendizados para futuras entregas
- [ ] Ajustes na precificação

### Meta de Precisão

```
Desvio aceitável: ±15% (185h ± 28h)
Faixa esperada: 157h - 213h
Com margem incluída: até 213h
```

### KPIs de Sucesso

**Performance:**
- Cálculo de disponibilidade < 2 segundos
- Resposta da agenda global < 3 segundos
- Calendário carrega em < 2 segundos

**Notificações Internas:**
- Dashboard atualizado em tempo real
- Alertas aparecem corretamente

**Validações:**
- 0% de conflitos não detectados
- Sugestões de horários em < 3 segundos

---

## 🔗 Referências

- [Requisitos Detalhados - Fase 3](./fase-3-sistema-agendamentos.md)
- [Estimativa de Horas - Fase 1](../fase-1/estimativa-horas-fase-1.md)
- [Estimativa de Horas - Fase 2](../fase-2/estimativa-horas-fase-2.md)
- [Precificação da Fase 3](./precificacao-fase-3.md) *(a criar)*
- [Custos de Infraestrutura Mensal](../fase-1/custos-infraestrutura-mensal.md)

---

**Última atualização:** Outubro 2025  
**Responsável:** CodeBoa Software  
**Status:** ✅ Estimativa Completa - Fase 3 (Sistema de Agendamentos)
