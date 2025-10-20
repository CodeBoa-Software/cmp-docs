# Estimativa de Horas - Fase 1

**Projeto:** Casa Mãe Paulistana  
**Entrega:** Cadastro e Aprovação (Fase 1)  
**Data de Entrega:** 10/11/2025  
**Data da Estimativa:** Outubro 2025  
**Versão:** 2.0

---

## 📊 Resumo Executivo

| Disciplina | Horas | % do Total | Complexidade |
|-----------|-------|------------|--------------|
| **1. Análise e Planejamento** | 25h | 10% | Média |
| **2. Setup de Infraestrutura** | 23h | 9% | Alta |
| **3. Backend Development** | 66h | 27% | Alta |
| **4. Frontend Development** | 63h | 26% | Média-Alta |
| **5. Integração e Testes** | 43h | 17% | Alta |
| **6. Documentação e Deploy** | 27h | 11% | Baixa-Média |
| **TOTAL BASE** | **247h** | **100%** | |

### Margem de Contingência
```
Horas base: 247h
Margem para imprevistos (+5%): 12h
───────────────────────────────────
TOTAL COM MARGEM: 259h
```

**Justificativa da margem:**
- Sistema de emails automáticos requer testes extensivos
- Integrações com serviços de email podem ter desafios
- Sistema de bloqueio parametrizável precisa de validação rigorosa
- Requisitos podem ser refinados durante desenvolvimento
- Testes em múltiplos dispositivos (mobile) requerem tempo adicional
- Ajustes de UX baseados em feedback
- Sistema de agendamento com preferências adiciona complexidade

---

## ⏱️ Detalhamento por Disciplina

### 1. Análise e Planejamento

| Atividade | Horas | Complexidade |
|-----------|-------|--------------|
| Refinamento de requisitos (3 sistemas) | 6h | Média |
| Modelagem de dados (schema DB completo) | 3h | Média |
| Desenho de arquitetura (multi-módulos) | 3h | Média-Alta |
| Definição de APIs (contratos para 3 subsistemas) | 3h | Média |
| Design do sistema de emails (templates + lógica) | 4h | Média |
| Planejamento de testes (3 fluxos principais) | 4h | Média |
| Documentação técnica inicial | 2h | Baixa |

**Subtotal:** 25h

**Justificativa:** Escopo expandido para 3 subsistemas principais (Formulário Público, Revisão/Aprovação, Agendamento) requer planejamento mais detalhado.

---

### 2. Setup de Infraestrutura

| Atividade | Horas | Complexidade |
|-----------|-------|--------------|
| Configuração GCP (projeto, billing, IAM) | 4h | Média |
| Setup Cloud Run (Frontend) | 1h | Média |
| Setup Cloud Run (Backend) | 1h | Média |
| Provisionamento Cloud SQL | 3h | Alta |
| Setup Cloud Storage (temporário para documentos) | 4h | Média |
| Configuração de serviço de email (SendGrid/Gmail API) | 4h | Alta |
| Configuração de secrets/env vars | 3h | Baixa |
| CI/CD básico (GitHub Actions) | 3h | Média-Alta |

**Subtotal:** 23h

**Justificativa da complexidade:** 
- Serviço de email requer configuração de autenticação, templates, e testes
- Políticas de exclusão automática de documentos requerem configuração de lifecycle policies
- Sistema de storage temporário com segurança LGPD

---

### 3. Backend Development (.NET)

| Atividade | Horas | Complexidade |
|-----------|-------|--------------||
| Setup projeto .NET (estrutura, DI, config) | 2h | Baixa |
| Mapeamento do Domínio (Models, DTOs, mappings) | 3h | Média |
| Configuração EntityFramework | 3h | Média |
| **Gerador de Protocolo Não-Sequencial (UUID)** | 1h | Média |
| **Sistema de Contadores Parametrizáveis** | 2h | Média |
| **Lógica de Bloqueio do Formulário** | 2h | Média |
| Serviço de validação (dados + arquivos) | 6h | Média-Alta |
| Upload e armazenamento temporário de documentos | 6h | Alta |
| **Serviço de Email (4 templates + lógica de envio)** | 10h | **Alta** |
| **API de Aprovação/Rejeição com workflows** | 6h | Alta |
| **API de Agendamento de Triagem** | 5h | Média-Alta |
| **Sistema de Preferências e Busca de Horários** | 4h | Média-Alta |
| Controllers e endpoints (CRUD completo) | 4h | Média |
| Middleware de erros e logging | 4h | Média |
| Testes automatizados | 8h | Média |

**Subtotal:** 66h

**Justificativa da complexidade:**
- **Sistema de Protocolo:** Geração UUID v4 com formato customizado (CMP-YYYY-XXXX-XXXX), garantia de unicidade
- **Sistema de Emails:** 4 tipos diferentes de emails (confirmação, aprovação, rejeição, agendamento) com templates HTML, lógica de envio assíncrona, tratamento de erros
- **Bloqueio Parametrizável:** Dois parâmetros configuráveis, lógica de verificação em tempo real, mensagens contextuais
- **Exclusão de Documentos:** Implementação segura de exclusão permanente após aprovação/rejeição, audit trail
- **Sistema de Aprovação:** Workflows complexos com estados, validações, notificações, histórico
- **Agendamento:** Busca inteligente de horários baseada em preferências, validação de disponibilidade
- Conformidade LGPD requer audit trail detalhado
- MediatR pattern: Commands/Queries com handlers dedicados

---

### 4. Frontend Development (React + Lovable)

| Atividade | Horas | Complexidade |
|-----------|-------|--------------|
| **Lovable AI - Formulário Público em Chat** | 12h | Média |
| **Migração/Ajustes do código Lovable para API** | 8h | Média |
| Upload de arquivos (mobile-friendly, preview, progresso) | 6h | Alta |
| **Sistema de Bloqueio (mensagem quando bloqueado)** | 2h | Baixa |
| **Tela: Revisão de Documentos Pendentes** | 4h | Média |
| **Tela: Aprovados Aguardando Triagem** | 3h | Baixa-Média |
| **Tela: Agendamento de Triagem** | 4h | Média |
| Validações client-side | 4h | Baixa |
| Tratamento de erros e loading states | 4h | Média |
| Responsividade e otimização mobile | 6h | Média |
| Testes E2E (Playwright - 3 fluxos principais) | 10h | Média-Alta |

**Subtotal:** 63h

**Justificativa da complexidade:**
- **Lovable AI:** Uso do Lovable para gerar formulário em formato de chat, economia de tempo no desenvolvimento inicial
- **3 Telas Administrativas:** Sistema interno completo (revisão, aprovação, agendamento)
- **Upload Mobile-Friendly:** Captura de câmera, galeria, drag-n-drop, preview de PDFs/imagens, validação de tamanho
- **Sistema de Bloqueio:** Interface responsiva que mostra mensagem clara quando bloqueado
- **Testes E2E:** 3 fluxos completos (cadastro público, aprovação/rejeição, agendamento)

---

### 5. Integração e Testes

| Atividade | Horas | Complexidade |
|-----------|-------|--------------|
| Testes de integração (API + DB) | 8h | Média |
| **Testes de sistema de emails (4 tipos)** | 6h | Alta |
| **Testes de bloqueio parametrizável** | 4h | Média |
| Testes de upload e exclusão de documentos | 6h | Alta |
| **Testes de workflow de aprovação/rejeição** | 4h | Média-Alta |
| **Testes de agendamento e preferências** | 3h | Média |
| Testes em múltiplos dispositivos móveis | 4h | Alta |
| Correção de bugs encontrados | 8h | Variável |

**Subtotal:** 43h

**Justificativa:** 
- Sistema de emails requer testes extensivos (envio correto, templates, erros)
- Upload e exclusão de documentos em diferentes cenários
- Testes em Android, iOS, Desktop com diferentes navegadores
- Validação de workflows complexos de aprovação/rejeição
- Sistema de bloqueio precisa ser testado em diversos estados

---

### 6. Documentação e Deploy

| Atividade | Horas | Complexidade |
|-----------|-------|--------------|
| Documentação de API (OpenAPI/Swagger) | 5h | Baixa-Média |
| **Documentação de templates de email** | 2h | Baixa |
| **Documentação de parâmetros configuráveis** | 2h | Baixa |
| README e guias de setup | 3h | Baixa |
| Documentação de deploy e runbooks | 4h | Média |
| Deploy em ambiente de produção | 4h | Média |
| Configuração de monitoring e alertas | 3h | Média |
| Handover e treinamento básico da equipe | 4h | Média |

**Subtotal:** 27h

**Justificativa:** Sistema mais complexo com 3 subsistemas requer documentação mais detalhada e treinamento mais extenso.

---

## 👥 Perfis de Desenvolvedores Necessários

### Full-Stack Developer (React + .NET)
- Responsável por arquitetura e features críticas
- Sistema de emails e notificações
- Setup de infraestrutura GCP
- Sistema de aprovação e agendamento
- Code review
- Testes (unitários, integração, E2E)
- Documentação técnica
- Refinamentos e ajustes
- **100% do projeto = 247h**
- **Taxa horária sugerida:** R$ 200/h

---

## 🎯 Distribuição de Horas por Fase

### Fase 1: MVP Funcional (Formulário + Aprovação)

**Prazo:** 4 semanas

| Disciplina | Horas |
|-----------|-------|
| Análise e Planejamento | 18h |
| Setup de Infraestrutura | 18h |
| Backend Development | 42h |
| Frontend Development (Lovable + ajustes) | 40h |
| Integração e Testes | 28h |
| Documentação e Deploy | 18h |
| **TOTAL FASE 1** | **164h** |

**Entregas:**
- ✅ Formulário público funcional (formato chat via Lovable)
- ✅ Sistema de protocolo não-sequencial
- ✅ Upload de 4 documentos obrigatórios (mobile-friendly)
- ✅ Sistema de bloqueio parametrizável
- ✅ Emails automáticos (confirmação + aprovação + rejeição)
- ✅ Tela de revisão e aprovação de documentos
- ✅ Exclusão automática de documentos
- ✅ Backend completo (APIs + validações)
- ✅ Deploy em ambiente de produção
- ✅ Testes básicos de funcionamento

---

### Fase 2: Sistema de Agendamento + Refinamento

**Prazo:** 2-3 semanas

| Disciplina | Horas |
|-----------|-------|
| Análise e Planejamento (agendamento) | 7h |
| Setup de Infraestrutura (ajustes) | 5h |
| Backend Development (agendamento + refinamentos) | 24h |
| Frontend Development (telas de agendamento + polimento) | 23h |
| Integração e Testes (completos) | 15h |
| Documentação e Deploy | 9h |
| **TOTAL FASE 2** | **83h** |

**Entregas:**
- ✅ Tela: Aprovados Aguardando Triagem
- ✅ Tela: Agendamento de Triagem
- ✅ Sistema de preferências e busca de horários
- ✅ Email de confirmação de agendamento
- ✅ UX/UI polido (Shadcn/UI completo)
- ✅ Validações completas (client + server)
- ✅ Responsividade mobile perfeita
- ✅ Testes automatizados completos (E2E + unitários)
- ✅ Monitoring e alertas configurados
- ✅ Documentação completa
- ✅ Handover com treinamento

---

## 💡 Considerações e Premissas

### Stack Tecnológica Definida
- **Frontend:** React + Vite + TypeScript + Shadcn/UI + Tailwind CSS (gerado via Lovable AI)
- **Backend:** .NET (ASP.NET Core) + Entity Framework + MediatR
- **Banco de Dados:** PostgreSQL (Cloud SQL)
- **Storage:** Cloud Storage (temporário, com lifecycle policies)
- **Email:** SendGrid ou Gmail API
- **Cloud:** Google Cloud Platform (GCP)
- **CI/CD:** GitHub Actions

### Premissas
- Equipe dedicada com experiência em React e .NET
- Acesso às credenciais GCP e serviço de email
- Lovable AI disponível para geração do formulário inicial
- Requisitos estáveis durante desenvolvimento
- Feedback do cliente disponível entre fases
- Ambiente de desenvolvimento configurado

### Riscos que Podem Impactar Horas
- **Sistema de Emails:** Configuração e testes podem aumentar em 10-20% se houver problemas de deliverability
- **Upload de arquivos em mobile:** Testes em múltiplos dispositivos podem adicionar 5-10h
- **Sistema de bloqueio:** Edge cases não previstos podem adicionar 5-8h
- **Mudanças de requisitos:** Cada mudança significativa pode adicionar 10-30h
- **Complexidade LGPD não prevista:** Auditoria adicional pode adicionar 5-15h
- **Performance com alto volume:** Otimizações podem adicionar 10-20h
- **Integração Lovable:** Ajustes no código gerado podem adicionar 5-10h

---

## 📅 Cronograma Estimado

### Timeline Total: 6-7 semanas

```
Semana 1: Análise + Setup (36h)
├─ Refinamento requisitos e arquitetura (18h)
├─ Infraestrutura GCP completa (18h)
└─ Setup projeto (Backend + Frontend)

Semana 2-3: Desenvolvimento Core (82h)
├─ Backend APIs e integrações (42h)
├─ Frontend formulário chat (Lovable) (40h)
├─ Sistema de protocolo e emails
└─ Upload de arquivos

Semana 4: Aprovação + Testes + Deploy (46h)
├─ Sistema de aprovação/rejeição (28h)
├─ Testes integração
└─ Deploy em PRODUÇÃO (18h)

──────────────────────────────────────────
FASE 1 COMPLETA - MVP EM PRODUÇÃO (4 semanas = 164h)

Semanas 5-7: Agendamento + Refinamento (83h)
├─ Sistema de agendamento completo (7h + 24h)
├─ Telas administrativas finais (23h)
├─ Testes E2E extensivos (15h)
└─ Documentação completa e handover (9h + 5h infra)

──────────────────────────────────────────
FASE 2 COMPLETA (2-3 semanas após MVP = 83h)
```

---

## 📊 Comparação: Estimativa vs Realidade

### Checklist de Validação

Ao final do projeto, validar:

- [ ] Horas reais vs estimadas por disciplina
- [ ] Principais desvios e causas
- [ ] Precisão do uso de Lovable AI
- [ ] Performance do sistema de emails
- [ ] Testes em dispositivos móveis
- [ ] Aprendizados para próximas entregas
- [ ] Ajustes na precificação

### Meta de Precisão

```
Desvio aceitável: ±5% (247h ± 12h)
Faixa esperada: 235h - 259h
Com margem incluída: até 259h
```

---

## 🆕 Novos Componentes vs Estimativa Anterior

### Comparação de Escopo

| Componente | Horas Anteriores | Horas Atuais | Delta |
|-----------|------------------|--------------|-------|
| **Análise e Planejamento** | 24h | 25h | +1h |
| **Setup de Infraestrutura** | 30h | 23h | -7h |
| **Backend Development** | 49h | 66h | +17h |
| **Frontend Development** | 29h | 63h | +34h |
| **Integração e Testes** | 24h | 43h | +19h |
| **Documentação e Deploy** | 20h | 27h | +7h |
| **TOTAL** | **176h** | **247h** | **+71h** |

### Principais Adições de Escopo (71h adicionais)

1. **Sistema de Protocolo Não-Sequencial:** +1h
2. **Sistema de Emails (4 tipos):** +10h (backend) + 6h (testes) + 4h (infra) = 20h
3. **Sistema de Bloqueio Parametrizável:** +2h (backend) + 2h (frontend) + 4h (testes) = 8h
4. **Sistema de Aprovação/Rejeição:** +6h (backend) + 4h (frontend) + 4h (testes) = 14h
5. **Sistema de Agendamento:** +9h (backend) + 7h (frontend) + 3h (testes) = 19h
6. **Armazenamento Temporário de Documentos:** +4h (infra)
7. **Validações Expandidas:** +2h (frontend)
8. **Testes Adicionais em Múltiplos Dispositivos:** +4h
9. **Documentação Expandida:** +7h

**Total de horas adicionais:** 71h (40% de aumento no escopo)

---

## 🔗 Referências

- [Precificação do Projeto](./precificacao-projeto.md)
- [Requisitos Detalhados - Fase 1](./fase-1-cadastro-e-aprovacao.md)
- [Custos de Infraestrutura Mensal](./custos-infraestrutura-mensal.md)

---

**Última atualização:** Outubro 2025  
**Responsável:** CodeBoa Software  
**Status:** ✅ Estimativa Completa - Fase 1 (Cadastro e Aprovação)

