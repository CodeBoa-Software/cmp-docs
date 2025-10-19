# Precificação do Projeto - Entrega 2

**Projeto:** Casa Mãe Paulistana  
**Entrega:** Sistema de Triagem + WhatsApp + Formulários de Especialistas  
**Data:** Outubro 2025  
**Versão:** 1.0

---

## 📦 Funcionalidades Incluídas

### ✅ Liberação para Triagem
- Painel administrativo (dashboard)
- Listagem de pré-cadastros pendentes
- Visualização de documentos enviados
- Sistema de aprovação/rejeição
- Logs de auditoria (quem aprovou/rejeitou)
- Notificações automáticas (email + WhatsApp)
- Filtros e busca avançada

### ✅ Formulário de Triagem
- Formulário interno para equipe
- Campos específicos de avaliação
- Validações de dados
- Integração com cadastro do beneficiário
- Histórico de triagens realizadas

### ✅ Análise de Documentos via WhatsApp
- Integração WhatsApp Business API
- Envio de solicitações de documentos
- Recebimento de documentos via WhatsApp
- Download e armazenamento de mídias
- Análise e validação de documentos
- Templates de mensagens padronizadas
- Histórico completo de conversas
- Vinculação automática com cadastros

### ✅ Formulários de Atendimento de Especialistas (3 formulários)
- **Formulário Psicólogo** (~20 campos)
- **Formulário Assistente Social** (~25 campos)
- **Formulário Terapeuta Ocupacional** (~18 campos)
- Validações específicas por especialidade
- Integração com sistema de triagem
- Histórico de atendimentos

### ✅ MVP Google Forms + Sheets (Setup Inicial)
- Configuração de formulários básicos
- Integração com Google Sheets
- Documentação de uso
- Plano de migração futura

### ✅ Infraestrutura (Incremental)
- Configuração WhatsApp Business API
- Webhooks para recebimento de mensagens
- Storage adicional para mídias WhatsApp
- Ajustes em secrets e variáveis de ambiente

### ✅ Qualidade
- Testes unitários (cobertura 70%)
- Testes de integração (WhatsApp + API)
- Testes E2E (fluxos administrativos)
- Code review
- Documentação técnica completa

---

## ⏱️ Estimativa de Horas de Desenvolvimento

### Resumo Executivo

| Disciplina | Horas | % do Total | Complexidade |
|-----------|-------|------------|--------------|
| **1. Análise e Planejamento** | 20h | 11% | Média |
| **2. Setup de Infraestrutura** | 10h | 5% | Baixa-Média |
| **3. Backend Development** | 68h | 36% | Alta |
| **4. Frontend Development** | 52h | 27% | Média-Alta |
| **5. Integração e Testes** | 26h | 14% | Alta |
| **6. Documentação e Deploy** | 14h | 7% | Baixa-Média |
| **TOTAL BASE** | **190h** | **100%** | |

### Margem de Contingência
```
Horas base: 190h
Margem para imprevistos (+15%): 28h
───────────────────────────────────
TOTAL COM MARGEM: 218h
```

> 📋 **Detalhamento completo:** Para ver o breakdown detalhado de horas por atividade, complexidades e justificativas, consulte [Estimativa de Horas - Entrega 2](./estimativa-horas-entrega-2.md)

---

## 💰 Modelos de Precificação

### Premissas

#### 👥 Perfis de Desenvolvedores Necessários

**Full-Stack Developer (React + .NET)**
- Desenvolvimento completo dos módulos
- Integração WhatsApp Business API
- Painel administrativo
- Formulários de triagem e especialistas
- Testes e documentação
- **100% do projeto = 190h**
- **Taxa horária:** R$ 200/h

#### 💡 Por que setup mais curto?

**Entrega 1 (Setup: 30h):**
- Setup completo Cloud Run (Frontend + Backend)
- Provisionamento AlloyDB/Cloud SQL
- Configuração inicial Google Drive API
- Setup Cloud Storage
- CI/CD do zero
- Configuração de secrets/env vars

**Entrega 2 (Setup: 10h):** ✅ -66% de redução
- ✅ Cloud Run já rodando
- ✅ Banco de dados já provisionado
- ✅ Drive API já configurado
- ✅ CI/CD já funcionando
- ➕ Apenas: WhatsApp API (novo) + ajustes incrementais

---

## 💵 Precificação Final

### Estrutura em 2 Fases

#### **Fase 1: Core Administrativo + WhatsApp - R$ 26.000**

**Prazo:** 3-4 semanas  
**Horas:** 130h

**Entregas:**
- ✅ Painel administrativo funcional
- ✅ Sistema de aprovação/rejeição de pré-cadastros
- ✅ Integração WhatsApp Business API completa
- ✅ Envio e recebimento de mensagens
- ✅ Download e análise de documentos via WhatsApp
- ✅ Formulário de triagem
- ✅ Sistema de notificações (email + WhatsApp)
- ✅ Deploy em produção
- ✅ Testes básicos de funcionamento

**Objetivo:** Automatizar fluxo de triagem e comunicação com beneficiários.

**Pagamento:**
- 50% no início (R$ 13.000)
- 50% na entrega (R$ 13.000)

---

#### **Fase 2: Formulários de Especialistas + Refinamento - R$ 12.000**

**Prazo:** 2-3 semanas  
**Horas:** 60h

**Entregas:**
- ✅ Formulário de atendimento - Psicólogo
- ✅ Formulário de atendimento - Assistente Social
- ✅ Formulário de atendimento - Terapeuta Ocupacional
- ✅ Validações específicas por especialidade
- ✅ Integração com sistema de triagem
- ✅ Testes E2E completos
- ✅ Documentação finalizada
- ✅ MVP Google Forms + Sheets (setup inicial)
- ✅ Handover com treinamento

**Objetivo:** Registro estruturado de atendimentos de especialistas.

**Pagamento:**
- 100% na entrega final (R$ 12.000)

---

### Total Entrega 2

```
Fase 1 (Core + WhatsApp):    R$ 26.000
Fase 2 (Especialistas):      R$ 12.000
──────────────────────────────────────
TOTAL ENTREGA 2:             R$ 38.000
```

### Características

| Aspecto | Detalhes |
|---------|----------|
| **Valor total** | R$ 38.000 (fixo) |
| **Horas estimadas** | 190h base + 28h margem = 218h |
| **Taxa horária média** | R$ 200/h |
| **Risco para cliente** | Médio (valida core antes de especialistas) |
| **Risco para fornecedor** | Médio (compartilhado) |
| **Flexibilidade** | Média-Alta (ajustes entre fases) |
| **Transparência** | Alta (entregas incrementais) |
| **Pagamento** | Escalonado (3 parcelas) |

### Vantagens deste Planejamento

```
✅ Infraestrutura já existe (menor custo de setup)
✅ Equipe familiarizada com codebase (mais produtividade)
✅ Validação do core administrativo antes dos formulários
✅ WhatsApp integrado desde Fase 1 (impacto rápido)
✅ Formulários de especialistas podem ser ajustados na Fase 2
✅ Pagamento escalonado (melhor cashflow)
✅ Redução de risco com entregas incrementais
```

### Cronograma de Pagamento

| Marco | Valor | % | Acumulado |
|-------|-------|---|-----------||
| **Assinatura do contrato** | R$ 13.000 | 34% | R$ 13.000 |
| **Entrega Fase 1 (Core + WhatsApp)** | R$ 13.000 | 34% | R$ 26.000 |
| **Entrega Final (Especialistas)** | R$ 12.000 | 32% | R$ 38.000 |

---

## 📊 Comparação: Entrega 1 vs Entrega 2

### Análise de Custos

| Métrica | Entrega 1 | Entrega 2 | Variação |
|---------|-----------|-----------|----------|
| **Horas Base** | 176h | 190h | +8% ⬆️ |
| **Preço Base** | R$ 35.200 | R$ 38.000 | +8% ⬆️ |
| **Setup Infra** | 30h | 10h | -66% ⬇️ |
| **Backend** | 49h | 68h | +39% ⬆️ |
| **Frontend** | 29h | 52h | +79% ⬆️ |
| **Prazo** | 5-8 sem | 5-7 sem | Similar |

### Por que +8% no preço?

**Redução de custo:**
- ➖ Setup de infraestrutura (-66%): economiza 20h × R$ 200 = -R$ 4.000

**Aumento de custo:**
- ➕ Integração WhatsApp Business API (complexa): +15h
- ➕ Painel administrativo completo: +12h
- ➕ 3 formulários de especialistas: +26h
- ➕ Sistema de aprovação/notificações: +8h
- **Total acréscimo:** +61h × R$ 200 = +R$ 12.200

**Resultado líquido:**
```
Redução:   -R$ 4.000 (setup)
Acréscimo: +R$ 12.200 (novas features)
──────────────────────────────────────
Variação:  +R$ 8.000 (+8%)
```

### Funcionalidades Adicionais na Entrega 2

| Funcionalidade | Complexidade | Horas | Valor |
|----------------|--------------|-------|-------|
| Integração WhatsApp API | Alta | 25h | R$ 5.000 |
| Painel Administrativo | Média-Alta | 20h | R$ 4.000 |
| Sistema Aprovação/Rejeição | Média | 14h | R$ 2.800 |
| 3 Formulários Especialistas | Média | 26h | R$ 5.200 |
| **TOTAL NOVO** | | **85h** | **R$ 17.000** |

**Justificativa:** Entrega 2 adiciona muito mais funcionalidades (painel admin + WhatsApp + 3 formulários) do que a Entrega 1 (apenas pré-cadastro público).

---

## 🎯 Proposta Comercial Recomendada

### Pacote: Sistema de Triagem + WhatsApp + Especialistas - Entrega 2

```markdown
═══════════════════════════════════════════════════════
INVESTIMENTO: R$ 38.000 (Planejamento em 2 Fases)
═══════════════════════════════════════════════════════

FASE 1 - CORE ADMINISTRATIVO + WHATSAPP (3-4 semanas)
├─ Investimento: R$ 26.000
├─ Pagamento: 50% início + 50% entrega
└─ Entrega: Painel Admin + WhatsApp + Triagem

FASE 2 - FORMULÁRIOS DE ESPECIALISTAS (2-3 semanas)
├─ Investimento: R$ 12.000
├─ Pagamento: 100% na entrega final
└─ Entrega: 3 Formulários + Testes + Documentação

PRAZO TOTAL: 5-7 semanas
GARANTIA: 30 dias pós aprovação final
```

---

### 📦 O que está INCLUÍDO

#### ✅ Desenvolvimento Completo

**Módulos Novos:**
- Painel administrativo (aprovação/rejeição)
- Sistema de notificações multicanal
- Integração WhatsApp Business API
- Formulário de triagem interno
- Interface de análise de documentos (WhatsApp)
- 3 formulários de atendimento de especialistas
- MVP Google Forms + Sheets (setup)

**Backend:**
- APIs REST completas (novos endpoints)
- Integração WhatsApp (webhooks + envio)
- Download e storage de mídias
- Sistema de aprovação com auditoria
- Templates de mensagens
- Validações específicas por especialidade

**Frontend:**
- Dashboard administrativo
- Interface de aprovação de cadastros
- Visualização de documentos
- Chat/histórico WhatsApp
- Formulários de triagem e especialistas
- Filtros e busca avançada

#### ✅ Infraestrutura (Incremental)

**Novas Configurações:**
- WhatsApp Business API (provedor + webhooks)
- Storage adicional para mídias WhatsApp
- Google Forms + Sheets (configuração inicial)
- Ajustes em secrets e env vars

**Já Existente (não cobrado novamente):**
- ✅ Cloud Run (Frontend + Backend)
- ✅ AlloyDB/Cloud SQL
- ✅ Google Drive API
- ✅ Cloud Storage
- ✅ CI/CD
- ✅ Monitoring básico

#### ✅ Qualidade Assegurada
- Testes unitários (cobertura 70%)
- Testes de integração (WhatsApp + API + DB)
- Testes E2E (fluxos administrativos completos)
- Code review completo
- Conformidade LGPD mantida

#### ✅ Documentação Técnica
- Documentação de novos endpoints API
- Guia de configuração WhatsApp
- Documentação dos formulários de especialistas
- Runbook de troubleshooting WhatsApp
- Guia de uso do MVP Google Forms
- Handover com equipe técnica (2h)

#### ✅ Suporte Pós-Deploy
- 30 dias de garantia
- Correção de bugs críticos
- Suporte via email (SLA 48h)
- 1 sessão de ajustes pós-produção

---

### ❌ O que NÃO está incluído

```
⚠️ Custos de infraestrutura GCP
   - Já cobertos pela Entrega 1 (~R$ 479-926/mês)
   - Pequeno acréscimo por WhatsApp webhooks e storage adicional

⚠️ Custos do provedor WhatsApp Business API
   - Twilio: ~US$ 0.005/msg + setup fee
   - MessageBird: similar
   - Meta Direct: variável
   - Estimativa: R$ 100-300/mês (dependendo do volume)

⚠️ Migração antecipada do Google Forms para sistema próprio
   - Se necessário antes da Entrega 3, seria projeto adicional

⚠️ Features fora do escopo da Entrega 2
   - Agendamento automático de consultas (Entrega 3)
   - Prontuário eletrônico completo (Entrega 3)
   - Relatórios e analytics avançados (Entrega 3)
   - Dashboard executivo (Entrega 3)

⚠️ Treinamento extensivo além do handover (2h incluídas)
   - Treinamento adicional pode ser contratado separadamente

⚠️ Manutenção contínua pós-garantia
   - Pode ser contratada separadamente
```

---

## 💡 Opções de Desconto

### 1. Fechamento Conjunto Entregas 1 + 2

```
Entrega 1 (Pré-cadastro):           R$ 35.200
Entrega 2 (Triagem + WhatsApp):     R$ 38.000
───────────────────────────────────────────────
Total sem desconto:                R$ 73.200

Desconto (fechamento conjunto): -10%
───────────────────────────────────────────────
VALOR TOTAL COM DESCONTO:          R$ 65.880

Economia total: R$ 7.320
```

**Vantagens:**
- Continuidade garantida do projeto
- Planejamento integrado desde o início
- Redução significativa de custo
- Equipe dedicada ao projeto completo

---

### 2. Fechamento de Todas as 3 Entregas

```
Entrega 1 (Pré-cadastro):           R$ 35.200
Entrega 2 (Triagem + WhatsApp):     R$ 38.000
Entrega 3 (Atendimentos + Dados):   R$ 45.000*
───────────────────────────────────────────────
Total sem desconto:                R$ 118.200

Desconto (fechamento total): -12%
───────────────────────────────────────────────
VALOR TOTAL COM DESCONTO:          R$ 104.016

Economia total: R$ 14.184
```

*Estimativa preliminar para Entrega 3

**Vantagens:**
- Maior economia percentual
- Visão completa do roadmap
- Priorização garantida
- Menor risco de descontinuidade

---

### 3. Pagamento Antecipado (À Vista) - Entrega 2

```
Valor normal: R$ 38.000
Desconto: -8%
──────────────────────────
Valor à vista: R$ 34.960

Economia: R$ 3.040
```

**Condições:**
- Pagamento 100% antecipado
- Melhora cashflow do fornecedor
- Reduz risco de inadimplência

---

## 🔍 Justificativa do Preço

### Por que R$ 38.000?

#### 1. Complexidade Técnica Adicional

```
✅ Integração WhatsApp Business API (webhooks, mídias, rate limiting)
✅ Painel administrativo completo (dashboard, filtros, aprovações)
✅ Sistema de notificações multicanal (email + WhatsApp)
✅ Análise de documentos via WhatsApp (download, storage, vinculação)
✅ 3 formulários de especialistas (~63 campos totais)
✅ Fluxo de aprovação com auditoria completa
✅ Sincronização entre múltiplos módulos
```

#### 2. Aproveitamento de Infraestrutura Existente

```
✅ Setup -66% mais curto (economiza R$ 4.000)
✅ Banco de dados já provisionado
✅ CI/CD já configurado
✅ Equipe familiarizada com codebase
✅ Padrões de código já estabelecidos
```

#### 3. Valor Entregue

**ROI Esperado:**
- ⏱️ Redução de ~70% no tempo de triagem (automatização)
- 📱 Comunicação instantânea via WhatsApp (beneficiários já usam)
- 📊 Registro estruturado de atendimentos de especialistas
- 🔍 Rastreabilidade completa (auditoria de aprovações)
- 🤖 Notificações automáticas (reduz trabalho manual)

#### 4. Comparação de Mercado

| Solução | Custo Estimado | Trade-offs |
|---------|----------------|------------|
| **Plataforma SaaS (ex: Zendesk)** | R$ 400-600/mês | ⚠️ Sem WhatsApp integrado, sem customização, vendor lock-in |
| **Integração WhatsApp apenas** | R$ 15-25k | ⚠️ Sem painel admin, sem formulários, apenas mensageria |
| **Sistema completo de agência** | R$ 60-90k | ✅ Qualidade, ⚠️ Muito caro, overhead alto |
| **CodeBoa (Proposta)** | R$ 38.000 | ✅ Completo, ✅ Preço justo, ✅ Integrado ⭐ |

---

## 🚀 Roadmap Completo (3 Entregas)

### Visão Geral

```
┌─────────────────────────────────────────────────────────┐
│  ENTREGA 1: PRÉ-CADASTRO PÚBLICO                        │
│  Status: ✅ Pronta para fechar                          │
│  Valor: R$ 35.200 | Prazo: 5-8 semanas                  │
└─────────────────────────────────────────────────────────┘
                         ↓
┌─────────────────────────────────────────────────────────┐
│  ENTREGA 2: TRIAGEM + WHATSAPP + ESPECIALISTAS          │
│  Status: 📋 Em precificação (este documento)            │
│  Valor: R$ 38.000 | Prazo: 5-7 semanas                  │
└─────────────────────────────────────────────────────────┘
                         ↓
┌─────────────────────────────────────────────────────────┐
│  ENTREGA 3: ATENDIMENTOS + ANALYTICS + PRONTUÁRIO       │
│  Status: 🔮 A definir                                    │
│  Valor: ~R$ 45.000* | Prazo: 6-8 semanas                │
└─────────────────────────────────────────────────────────┘

TOTAL ESTIMADO (3 entregas): ~R$ 118.200
COM DESCONTO (-12%):          R$ 104.016
```

*Estimativa preliminar

---

## 📋 Próximos Passos

### Para Fechar a Entrega 2

1. **Validar requisitos** específicos
   - ✅ Campos do formulário de triagem
   - ✅ Campos dos 3 formulários de especialistas
   - ✅ Critérios de aprovação/rejeição
   - ✅ Templates de mensagens WhatsApp
   
2. **Escolher provedor** WhatsApp Business API
   - Twilio (mais comum, bem documentado)
   - MessageBird (europeu, bom suporte)
   - Meta Direct (direto, mas mais burocrático)
   
3. **Confirmar modelo** de pagamento
   - Híbrido 2 Fases: R$ 38.000
   - À vista com desconto: R$ 34.960
   - Pacote com Entrega 1: R$ 65.880 (entregas 1+2)
   
4. **Definir infraestrutura** adicional
   - Custos mensais de WhatsApp API
   - Storage adicional para mídias
   
5. **Elaborar contrato** (SOW - Statement of Work)
   - Escopo detalhado
   - Cronograma de entregas
   - Termos de pagamento
   - Garantias e SLAs
   - Critérios de aceitação
   
6. **Kickoff meeting**
   - Alinhamento técnico
   - Definição de comunicação
   - Refinamento de requisitos
   - Setup de credenciais WhatsApp
   
7. **Início do desenvolvimento**
   - Sprint 0 (setup WhatsApp)
   - Sprints semanais
   - Demos quinzenais
   - Validações intermediárias

---

## 💰 Resumo Financeiro

### Investimento Recomendado

```
╔═══════════════════════════════════════════════════════╗
║  ENTREGA 2: TRIAGEM + WHATSAPP + ESPECIALISTAS        ║
║                                                        ║
║  Valor Total:        R$ 38.000                         ║
║  Horas Estimadas:    190h (base) + 28h (margem)       ║
║  Taxa Horária:       R$ 200/h                          ║
║  Prazo:              5-7 semanas                       ║
║  Garantia:           30 dias pós-deploy                ║
║                                                        ║
║  PARCELAMENTO:                                         ║
║  • Início:          R$ 13.000 (34%)                    ║
║  • Fase 1:          R$ 13.000 (34%)                    ║
║  • Fase 2:          R$ 12.000 (32%)                    ║
╚═══════════════════════════════════════════════════════╝
```

### Opções de Economia

| Opção | Valor Original | Desconto | Valor Final | Economia |
|-------|----------------|----------|-------------|----------|
| **Padrão (2 fases)** | R$ 38.000 | - | R$ 38.000 | - |
| **À vista** | R$ 38.000 | -8% | R$ 34.960 | R$ 3.040 |
| **Pacote E1+E2** | R$ 73.200 | -10% | R$ 65.880 | R$ 7.320 |
| **Pacote E1+E2+E3** | R$ 118.200 | -12% | R$ 104.016 | R$ 14.184 |

---

## 📞 Contato

**Dúvidas sobre precificação ou proposta?**

CodeBoa Software  
Email: [contato]  
Telefone: [telefone]

---

## 📄 Anexos

### Documentos Relacionados

**Entrega 2:**
- [Requisitos Detalhados - Entrega 2](./entrega-2-a-definir.md)
- [Estimativa de Horas - Entrega 2](./estimativa-horas-entrega-2.md)

**Entrega 1 (Referência):**
- [Requisitos - Entrega 1](../entrega-1/entrega-1-22-outubro.md)
- [Estimativa de Horas - Entrega 1](../entrega-1/estimativa-horas-entrega-1.md)
- [Precificação - Entrega 1](../entrega-1/precificacao-projeto.md)
- [Custos de Infraestrutura Mensal](../entrega-1/custos-infraestrutura-mensal.md)

**Arquitetura:**
- [ADR-002: Arquitetura Técnica](../../adrs/ADR-002-arquitetura-tecnica.md)
- [ADR-003: Armazenamento de Documentos](../../adrs/ADR-003-armazenamento-documentos.md)

---

**Última atualização:** Outubro 2025  
**Responsável:** CodeBoa Software  
**Validade da proposta:** 30 dias  
**Status:** ✅ Precificação Completa
