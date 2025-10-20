# Precificação do Projeto - Fase 1

**Projeto:** Casa Mãe Paulistana  
**Entrega:** Cadastro e Aprovação (Fase 1)  
**Data:** Outubro 2025  
**Versão:** 2.0

### Funcionalidades Incluídas

#### ✅ Frontend (React + Lovable)
- Formulário público em formato chat (gerado via Lovable AI)
- Dados do responsável e dependente
- Upload de 4 documentos obrigatórios (mobile-friendly, preview, progresso)
- Sistema de bloqueio parametrizável (mensagem quando bloqueado)
- Validações client-side (CPF, email, telefone, arquivos)
- Interface responsiva mobile-first
- Tela de confirmação com protocolo não-sequencial
- **Tela de revisão de documentos pendentes**
- **Tela de aprovados aguardando triagem**
- **Tela de agendamento de triagem**

#### ✅ Backend (.NET)
- API REST completa (MediatR pattern)
- Validação de dados e documentos
- Processamento de uploads
- **Armazenamento temporário de documentos (Cloud Storage)**
- **Geração de protocolo não-sequencial (UUID v4)**
- **Sistema de emails automáticos (4 tipos: confirmação, aprovação, rejeição, agendamento)**
- **Sistema de bloqueio parametrizável (dois parâmetros configuráveis)**
- **API de aprovação/rejeição com workflows**
- **API de agendamento de triagem com preferências**
- **Exclusão automática de documentos após aprovação/rejeição**
- Armazenamento de metadata (PostgreSQL)
- Auditoria completa (LGPD)

#### ✅ Infraestrutura (GCP)
- Cloud Run (Frontend + Backend)
- Cloud SQL PostgreSQL
- Cloud Storage (temporário com lifecycle policies)
- **Serviço de email (SendGrid ou Gmail API)**
- Monitoring & Logging
- CI/CD básico (GitHub Actions)

#### ✅ Qualidade
- Testes unitários (cobertura 70%)
- Testes E2E (3 fluxos principais: cadastro, aprovação, agendamento)
- **Testes de sistema de emails (4 tipos)**
- **Testes em múltiplos dispositivos móveis**
- Code review
- Documentação técnica completa

---

## ⏱️ Estimativa de Horas de Desenvolvimento

### Resumo Executivo

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

### Principais Adições de Escopo

**+71h adicionais** (40% de aumento no escopo vs estimativa anterior):

1. **Sistema de Protocolo Não-Sequencial (UUID v4):** +1h
2. **Sistema de Emails (4 tipos):** +20h (backend + testes + infra)
3. **Sistema de Bloqueio Parametrizável:** +8h (backend + frontend + testes)
4. **Sistema de Aprovação/Rejeição:** +14h (backend + frontend + testes)
5. **Sistema de Agendamento:** +19h (backend + frontend + testes)
6. **Armazenamento Temporário de Documentos:** +4h (infra)
7. **Testes Expandidos (múltiplos dispositivos):** +4h
8. **Documentação Expandida:** +7h

> 📋 **Detalhamento completo:** Para ver o breakdown detalhado de horas por atividade, complexidades e justificativas, consulte [Estimativa de Horas - Fase 1](./estimativa-horas-fase-1.md)

---

## 💰 Modelos de Precificação

### Premissas

#### 👥 Perfis de Desenvolvedores Necessários

### Full-Stack Developer (React + .NET)
- Responsável por arquitetura e features críticas
- Sistema de emails e notificações
- Sistema de aprovação e agendamento
- Setup de infraestrutura GCP
- Code review
- Testes (unitários, integração, E2E)
- Documentação técnica
- Refinamentos e ajustes
- **100% do projeto = 259h (247h base + 12h margem)**
- **Taxa horária sugerida:** R$ 200/h

## 💵 Precificação final

### Estrutura em 2 Entregas

#### **Entrega 1: MVP Funcional (Formulário + Aprovação) - R$ 34.400**

**Prazo:** 4 semanas  
**Horas:** 172h (164h base + 8h margem)

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

**Objetivo:** Validar funcionalidade core com sistema de aprovação completo.

**Pagamento:**
- 50% no início (R$ 17.200)
- 50% na entrega (R$ 17.200)

---

#### **Entrega 2: Sistema de Agendamento + Refinamento - R$ 17.400**

**Prazo:** 2-3 semanas  
**Horas:** 87h (83h base + 4h margem)

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

**Objetivo:** Sistema de agendamento completo e produção.

**Pagamento:**
- 100% na entrega final (R$ 17.400)

---

### Total

```
Fase 1 (MVP + Aprovação):      R$ 34.400
Fase 2 (Agendamento + Polish):  R$ 17.400
────────────────────────────────────────
TOTAL:                 R$ 51.800
```

**Nota:** Este valor inclui a margem de contingência de 5% (+12h) distribuída proporcionalmente entre as duas entregas para cobrir imprevistos como:
- Ajustes de requisitos durante desenvolvimento
- Testes adicionais em múltiplos dispositivos
- Refinamentos de UX baseados em feedback
- Complexidades não previstas nos sistemas de email e agendamento

### Características

| Aspecto | Detalhes |
|---------|----------|
| **Valor total** | R$ 51.800 (fixo, com margem de 5%) |
| **Risco para cliente** | Médio (valida cedo, ajusta depois) |
| **Risco para fornecedor** | Baixo (margem incluída) |
| **Flexibilidade** | Média-Alta (ajustes entre fases) |
| **Transparência** | Alta (entregas incrementais) |
| **Pagamento** | Escalonado (33% + 33% + 34%) |

### Vantagens deste Planejamento

```
✅ Cliente valida formulário + aprovação em 4 semanas
✅ Sistema de aprovação funcional desde a Fase 1
✅ Feedback incorporado antes do agendamento
✅ Menor risco de retrabalho grande
✅ Pagamento escalonado (melhor cashflow)
✅ Possibilidade de ajustar prioridades entre fases
✅ Demonstra valor rapidamente
✅ Reduz ansiedade do cliente (vê resultado cedo)
```

### Cronograma de Pagamento

| Marco | Valor | % | Acumulado |
|-------|-------|-----------|-----------|
| **Assinatura do contrato** | R$ 17.200 | 33% | R$ 17.200 |
| **Entrega MVP + Aprovação (Fase 1)** | R$ 17.200 | 33% | R$ 34.400 |
| **Entrega Final (Fase 2)** | R$ 17.400 | 34% | R$ 51.800 |

---

## 🎯 Proposta Comercial Recomendada

### Pacote: Sistema de Cadastro e Aprovação CMP - Fase 1

```markdown
═══════════════════════════════════════════════════════
INVESTIMENTO: R$ 51.800 (com margem de 5% incluída)
═══════════════════════════════════════════════════════

FASE 1 - MVP FUNCIONAL + APROVAÇÃO (4 semanas)
├─ Investimento: R$ 34.400 (172h)
├─ Pagamento: 50% início + 50% entrega
└─ Entrega: Formulário Chat + Upload + Aprovação + Emails

FASE 2 - AGENDAMENTO + REFINAMENTO (2-3 semanas)
├─ Investimento: R$ 17.400 (87h)
├─ Pagamento: 100% na entrega final
└─ Entrega: Agendamento + UX polido + Testes + Ajustes

PRAZO TOTAL: 6-7 semanas
GARANTIA: 30 dias pós aprovação final

MARGEM DE CONTINGÊNCIA: +5% (12h) incluída para imprevistos
```

---

### 📦 O que está INCLUÍDO

#### ✅ Desenvolvimento Completo
- Frontend React (formulário chat + 3 telas admin + upload mobile-friendly)
- Backend .NET (API REST + validações + MediatR)
- Banco de dados PostgreSQL (schema + migrations)
- Sistema de emails automáticos (4 tipos)
- Armazenamento temporário de documentos (Cloud Storage)

#### ✅ Infraestrutura GCP
- Setup completo Cloud Run (Frontend + Backend)
- Configuração Cloud SQL PostgreSQL
- Cloud Storage com lifecycle policies (exclusão automática)
- Serviço de email (SendGrid ou Gmail API)
- Monitoring básico e alertas de custo
- CI/CD automatizado (GitHub Actions)

#### ✅ Qualidade Assegurada
- Testes unitários (cobertura 70%)
- Testes E2E (3 fluxos principais: cadastro, aprovação, agendamento)
- Testes de sistema de emails (4 tipos)
- Testes em múltiplos dispositivos móveis
- Code review completo
- Conformidade LGPD (audit trail + exclusão automática)
- Validações client + server

#### ✅ Documentação Técnica
- API documentation (OpenAPI/Swagger)
- README técnico completo
- Guias de deploy e operação
- Runbooks para troubleshooting
- Handover com equipe técnica (3h)

#### ✅ Suporte Pós-Deploy
- 30 dias de garantia
- Correção de bugs críticos
- Suporte via email (SLA 48h)
- 1 sessão de ajustes pós-produção

---

### ❌ O que NÃO está incluído

```
⚠️ Custos de infraestrutura GCP (~R$ 479-926/mês)
   Veja: custos-infraestrutura-mensal.md

⚠️ Custos do serviço de email (SendGrid ou Gmail API)
   - SendGrid: ~R$ 50-200/mês (dependendo do volume)
   - Gmail API: incluído no Google Workspace (se aplicável)

⚠️ Domínio customizado (ex: cadastro.casamaepaulistana.org.br)

⚠️ Certificado SSL customizado (se houver domínio próprio)

⚠️ Treinamento extensivo além do handover inicial (4h incluídas)

⚠️ Features fora do escopo da Fase 1
   - WhatsApp integration (Entrega 2)
   - Formulários de atendimento (Entrega 3)
   - Dashboards e relatórios (Entrega 2/3)

⚠️ Manutenção contínua pós-garantia
   (pode ser contratada separadamente)
```

---

## 💡 Opções de Desconto

### 1. Pagamento Antecipado (À Vista)

```
Valor normal: R$ 51.800
Desconto: -8%
──────────────────────────
Valor à vista: R$ 47.656

Economia: R$ 4.144
```

**Condições:**
- Pagamento 100% antecipado
- Melhora cashflow do fornecedor
- Reduz risco de inadimplência

---

### 2. Fechamento de Múltiplas Entregas

```
Fase 1 (Cadastro + Aprovação):      R$ 51.800
Entrega 2 (Triagem + WhatsApp):     R$ 38.000
Entrega 3 (Atendimentos + Dados):   R$ 45.000
───────────────────────────────────────────────
Total sem desconto:                R$ 134.800

Desconto (fechamento conjunto): -12%
───────────────────────────────────────────────
VALOR TOTAL COM DESCONTO:          R$ 118.624

Economia total: R$ 16.176
```

**Vantagens:**
- Continuidade garantida do projeto
- Redução significativa de custo
- Melhor planejamento de longo prazo
- Equipe dedicada ao projeto

---

## 🔍 Justificativa do Preço

### Por que R$ 51.800?

#### 1. Complexidade Técnica

```
✅ Sistema de emails automáticos (4 tipos diferentes)
✅ Sistema de aprovação/rejeição com workflows
✅ Sistema de agendamento com preferências
✅ Upload de arquivos mobile-friendly (tratamento robusto)
✅ Protocolo não-sequencial (UUID v4 customizado)
✅ Bloqueio parametrizável do formulário
✅ Exclusão automática de documentos
✅ Validações complexas (dados + documentos)
✅ Conformidade LGPD (audit trail + exclusão segura)
✅ Infraestrutura cloud-native (GCP)
✅ Responsividade mobile (múltiplos dispositivos)
✅ 3 telas administrativas (revisão, aprovação, agendamento)
```

#### 2. Qualidade Garantida

```
✅ Testes automatizados (70% cobertura)
✅ Testes de emails (4 tipos)
✅ Testes em múltiplos dispositivos móveis
✅ Testes E2E (3 fluxos principais)
✅ Code review por senior developer
✅ CI/CD para deploys seguros
✅ Documentação técnica completa
✅ 30 dias de garantia pós-deploy
```

#### 3. Stack Moderna e Escalável

```
✅ React + TypeScript + Lovable AI (manutenível)
✅ .NET + MediatR (performático e robusto)
✅ PostgreSQL (confiável)
✅ Cloud Storage (seguro e escalável)
✅ SendGrid/Gmail API (confiável)
✅ GCP (escalável e seguro)
✅ Arquitetura cloud-native
```

#### 4. Comparação de Mercado

| Solução | Custo Estimado | Trade-offs |
|---------|----------------|------------|
| **Freelancer "barato"** | R$ 20-35k | ⚠️ Sem garantia, código legado, sem testes, risco alto |
| **Software pronto (SaaS)** | R$ 500-1000/mês | ⚠️ Vendor lock-in, sem customização, compliance duvidoso |
| **Agência grande** | R$ 100-150k | ✅ Qualidade, ⚠️ Muito caro, overhead alto |
| **CodeBoa (Proposta)** | R$ 51.800 | ✅ Qualidade, ✅ Preço justo, ✅ Margem incluída ⭐ |

---

## 📋 Próximos Passos

### Para Fechar o Projeto

1. **Validar escopo** com stakeholders
   - Confirmar requisitos da Fase 1
   - Esclarecer dúvidas sobre funcionalidades (aprovação, agendamento, emails)
   
2. **Escolher modelo** de pagamento
   - Time & Material (259h × R$ 200/h = R$ 51.800)
   - Preço Fixo (R$ 51.800 com margem incluída)
   - **Híbrido - Recomendado** (R$ 51.800)
   
3. **Definir infraestrutura**
   - Cloud SQL PostgreSQL (R$ 479/mês)
   - Serviço de email (SendGrid ou Gmail API)
   
4. **Elaborar contrato** (SOW - Statement of Work)
   - Escopo detalhado
   - Cronograma de entregas (2 fases)
   - Termos de pagamento (3 parcelas)
   - Garantias e SLAs
   
5. **Kickoff meeting**
   - Alinhamento técnico
   - Definição de comunicação
   - Setup de ambientes
   - Configuração de serviço de email
   
6. **Início do desenvolvimento**
   - Sprint 0 (setup)
   - Sprints semanais
   - Demos quinzenais

---

## 📞 Contato

**Dúvidas sobre precificação ou proposta?**

CodeBoa Software  
Email: [contato]  
Telefone: [telefone]

---

## 📄 Anexos

### Documentos Relacionados

- [Requisitos Detalhados - Fase 1](./fase-1-cadastro-e-aprovacao.md)
- [Estimativa de Horas - Fase 1](./estimativa-horas-fase-1.md)
- [Custos de Infraestrutura Mensal](./custos-infraestrutura-mensal.md)

---

**Última atualização:** Outubro 2025  
**Responsável:** CodeBoa Software  
**Validade da proposta:** 30 dias
