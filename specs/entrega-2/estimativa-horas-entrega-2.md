# Estimativa de Horas - Entrega 2

**Projeto:** Casa Mãe Paulistana  
**Entrega:** Sistema de Triagem + WhatsApp + Formulários de Especialistas  
**Data:** Outubro 2025  
**Versão:** 1.0

---

## 📊 Resumo Executivo

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

**Justificativa da margem:**
- Integração WhatsApp Business API tem complexidade imprevisível
- Múltiplos formulários de especialistas podem ter requisitos específicos
- Fluxos de aprovação e notificações podem exigir refinamentos
- Sincronização entre diferentes módulos requer atenção especial

---

## ⏱️ Detalhamento por Disciplina

### 1. Análise e Planejamento

| Atividade | Horas | Complexidade |
|-----------|-------|--------------|
| Refinamento de requisitos (triagem + WhatsApp) | 5h | Média |
| Modelagem de dados (novos schemas) | 4h | Média |
| Definição de fluxos de aprovação | 3h | Média |
| Desenho da integração WhatsApp | 4h | Média-Alta |
| Definição de APIs (contratos) | 3h | Baixa |
| Planejamento de testes | 1h | Baixa |

**Subtotal:** 20h

**Justificativa:** Setup reduzido pois arquitetura já está definida na Entrega 1. Foco em novos módulos e integrações.

---

### 2. Setup de Infraestrutura

| Atividade | Horas | Complexidade |
|-----------|-------|--------------|
| Configuração WhatsApp Business API (provedor) | 4h | Média-Alta |
| Setup de webhooks para WhatsApp | 2h | Média |
| Configuração de storage adicional (mídias WhatsApp) | 2h | Baixa |
| Ajustes em Cloud Run (variáveis, secrets) | 1h | Baixa |
| Configuração Google Forms + Sheets | 1h | Baixa |

**Subtotal:** 10h

**Justificativa:** Infraestrutura base (Cloud Run, DB, Storage) já existe. Apenas configurações incrementais e integração WhatsApp.

---

### 3. Backend Development (.NET)

| Atividade | Horas | Complexidade |
|-----------|-------|--------------|
| **Módulo de Liberação para Triagem** | | |
| - Models e DTOs (aprovação/rejeição) | 3h | Baixa |
| - Endpoints de aprovação/rejeição | 4h | Média |
| - Sistema de notificações (email + WhatsApp) | 5h | Média-Alta |
| - Logs de auditoria (quem aprovou/rejeitou) | 2h | Baixa |
| **Formulário de Triagem** | | |
| - Models e DTOs para triagem | 3h | Baixa |
| - Endpoints CRUD de triagem | 4h | Média |
| - Validações e regras de negócio | 3h | Média |
| **Integração WhatsApp Business API** | | |
| - Setup cliente WhatsApp (SDK/REST) | 4h | Alta |
| - Webhook handler (recebimento mensagens) | 5h | Alta |
| - Serviço de envio de mensagens | 3h | Média |
| - Download e storage de mídias recebidas | 4h | Média-Alta |
| - Sistema de templates de mensagens | 3h | Média |
| - Vinculação de conversas com cadastros | 4h | Média-Alta |
| **Formulários de Especialistas (3 formulários)** | | |
| - Models e schemas (3 formulários × 2h) | 6h | Baixa-Média |
| - Endpoints CRUD (3 formulários × 3h) | 9h | Média |
| - Validações específicas por especialidade | 4h | Média |
| **Testes Unitários** | | |
| - Cobertura 70% dos novos módulos | 12h | Média |

**Subtotal:** 68h

**Justificativa da complexidade:**
- **WhatsApp API:** Webhook handling, processamento assíncrono, download de mídias, rate limiting
- **Notificações:** Múltiplos canais (email + WhatsApp), templates, filas
- **Formulários especialistas:** Campos dinâmicos por especialidade, validações específicas
- **Aprovação/Rejeição:** Fluxo de estados, auditoria completa, notificações em cascata

---

### 4. Frontend Development (React)

| Atividade | Horas | Complexidade |
|-----------|-------|--------------|
| **Painel Administrativo** | | |
| - Dashboard de pré-cadastros pendentes | 6h | Média |
| - Visualização de documentos enviados | 4h | Média |
| - Botões de aprovar/rejeitar com confirmação | 3h | Baixa-Média |
| - Filtros e busca | 4h | Média |
| - Sistema de notificações in-app | 3h | Média |
| **Formulário de Triagem** | | |
| - Interface do formulário | 5h | Média |
| - Validações client-side | 2h | Baixa |
| - Integração com API | 2h | Baixa |
| **Interface de Análise WhatsApp** | | |
| - Listagem de conversas | 4h | Média |
| - Visualização de histórico de mensagens | 4h | Média |
| - Interface para análise de documentos recebidos | 4h | Média |
| - Preview de mídias (fotos/PDFs) | 3h | Média |
| **Formulários de Especialistas (3 formulários)** | | |
| - Interfaces dos formulários (3 × 2h) | 6h | Média |
| - Validações e lógica (3 × 1h) | 3h | Baixa-Média |
| **Integração e Polimento** | | |
| - Responsividade mobile | 3h | Média |
| - Tratamento de erros e loading states | 2h | Baixa |

**Subtotal:** 52h

**Justificativa da complexidade:**
- **Painel Admin:** Múltiplas funcionalidades integradas, visualização de documentos, filtros avançados
- **WhatsApp UI:** Histórico de conversas, preview de mídias, interface tipo chat
- **Formulários especialistas:** Campos específicos por especialidade, validações customizadas

---

### 5. Integração e Testes

| Atividade | Horas | Complexidade |
|-----------|-------|--------------|
| Testes de integração (API + DB) | 6h | Média |
| Testes de integração WhatsApp (envio/recebimento) | 8h | Alta |
| Testes de fluxo completo (aprovação → notificação) | 4h | Média-Alta |
| Testes E2E (principais fluxos administrativos) | 6h | Média |
| Correção de bugs encontrados | 2h | Variável |

**Subtotal:** 26h

**Justificativa:** Integração WhatsApp requer testes extensivos de webhooks, processamento assíncrono e diferentes cenários de falha.

---

### 6. Documentação e Deploy

| Atividade | Horas | Complexidade |
|-----------|-------|--------------|
| Documentação de API (novos endpoints) | 3h | Baixa |
| Guia de configuração WhatsApp | 3h | Média |
| Documentação dos formulários de especialistas | 2h | Baixa |
| Runbook de troubleshooting WhatsApp | 2h | Média |
| Deploy em produção | 2h | Baixa-Média |
| Handover e treinamento da equipe | 2h | Baixa |

**Subtotal:** 14h

---

## 👥 Perfis de Desenvolvedores Necessários

### Full-Stack Developer (React + .NET)
- Desenvolvimento completo dos módulos
- Integração WhatsApp Business API
- Painel administrativo
- Formulários de triagem e especialistas
- Testes e documentação
- **100% do projeto = 190h**
- **Taxa horária:** R$ 200/h

---

## 🎯 Distribuição de Horas por Fase

### Fase 1: Core Administrativo + WhatsApp

**Prazo:** 3-4 semanas

| Disciplina | Horas |
|-----------|-------|
| Análise e Planejamento | 15h |
| Setup de Infraestrutura | 10h |
| Backend Development | 45h |
| Frontend Development | 35h |
| Integração e Testes | 18h |
| Documentação e Deploy | 7h |
| **TOTAL FASE 1** | **130h** |

**Entregas:**
- ✅ Painel administrativo funcional
- ✅ Sistema de aprovação/rejeição
- ✅ Integração WhatsApp (envio + recebimento)
- ✅ Formulário de triagem
- ✅ Análise de documentos via WhatsApp
- ✅ Sistema de notificações

---

### Fase 2: Formulários de Especialistas + Refinamento

**Prazo:** 2-3 semanas

| Disciplina | Horas |
|-----------|-------|
| Análise e Planejamento | 5h |
| Backend Development | 23h |
| Frontend Development | 17h |
| Integração e Testes | 8h |
| Documentação e Deploy | 7h |
| **TOTAL FASE 2** | **60h** |

**Entregas:**
- ✅ 3 formulários de especialistas completos
- ✅ Validações específicas por especialidade
- ✅ Integração com sistema de triagem
- ✅ Testes E2E completos
- ✅ Documentação finalizada
- ✅ MVP Google Forms + Sheets (se necessário)

---

## 💡 Considerações e Premissas

### Stack Tecnológica (Mantida da Entrega 1)
- **Frontend:** React + Vite + TypeScript + Shadcn/UI + Tailwind CSS
- **Backend:** .NET (ASP.NET Core) + Entity Framework + MediatR
- **Banco de Dados:** PostgreSQL (AlloyDB ou Cloud SQL)
- **Storage:** Google Drive API + Cloud Storage
- **Cloud:** Google Cloud Platform (GCP)
- **CI/CD:** GitHub Actions
- **Novo:** WhatsApp Business API (provedor a definir: Twilio, MessageBird, Meta)

### Premissas
- ✅ Infraestrutura da Entrega 1 já está rodando em produção
- ✅ Stack tecnológica validada e estável
- ✅ Equipe familiarizada com codebase
- Provedor WhatsApp Business API será contratado
- Requisitos dos formulários de especialistas serão definidos no início
- Equipe cliente disponível para validações intermediárias

### Novidades vs Entrega 1
- **Redução em Setup:** -66% (30h → 10h)
  - Infraestrutura base já existe
  - CI/CD já configurado
  - Apenas configurações incrementais
  
- **Aumento em Backend:** +39% (49h → 68h)
  - Integração WhatsApp (complexa)
  - 3 novos formulários de especialistas
  - Sistema de aprovação/rejeição
  - Múltiplas notificações

- **Aumento em Frontend:** +79% (29h → 52h)
  - Painel administrativo completo
  - Interface de análise WhatsApp
  - 3 formulários adicionais
  - Dashboard de gestão

### Riscos que Podem Impactar Horas
- **WhatsApp Business API:** Limitações de sandbox, rate limiting, webhooks instáveis (+15-20h)
- **Requisitos dos formulários de especialistas não finalizados:** Cada mudança pode adicionar 3-8h por formulário
- **Complexidade do fluxo de aprovação:** Regras de negócio não previstas (+5-10h)
- **Volume de notificações:** Performance e filas podem precisar otimização (+8-15h)
- **Integração com Google Forms:** Se migração for necessária antes do previsto (+10-20h)

---

## 📅 Cronograma Estimado

### Timeline Total: 5-7 semanas

```
Semana 1: Análise + Setup WhatsApp (25h)
├─ Refinamento requisitos (15h)
├─ Configuração WhatsApp API (10h)
└─ Setup webhooks e storage

Semana 2-3: Desenvolvimento Core (70h)
├─ Backend: Aprovação/Rejeição + WhatsApp (35h)
├─ Frontend: Painel Admin + WhatsApp UI (30h)
└─ Integração básica (5h)

Semana 4: Formulário de Triagem + Testes (35h)
├─ Backend + Frontend triagem (15h)
├─ Testes integração WhatsApp (10h)
└─ Correções e ajustes (10h)

──────────────────────────────────────────
FASE 1 COMPLETA - CORE FUNCIONAL (4 semanas = 130h)

Semana 5-6: Formulários de Especialistas (40h)
├─ Backend: 3 formulários (19h)
├─ Frontend: 3 formulários (12h)
└─ Validações específicas (9h)

Semana 7: Finalização + Deploy (20h)
├─ Testes E2E completos (8h)
├─ Documentação (7h)
├─ Deploy e handover (5h)

──────────────────────────────────────────
FASE 2 COMPLETA (3 semanas após Fase 1 = 60h)
```

---

## 📊 Comparação com Entrega 1

| Métrica | Entrega 1 | Entrega 2 | Variação |
|---------|-----------|-----------|----------|
| **Horas Base** | 176h | 190h | +8% |
| **Setup Infraestrutura** | 30h | 10h | -66% ⬇️ |
| **Backend** | 49h | 68h | +39% ⬆️ |
| **Frontend** | 29h | 52h | +79% ⬆️ |
| **Análise** | 24h | 20h | -17% ⬇️ |
| **Testes** | 24h | 26h | +8% ⬆️ |
| **Documentação** | 20h | 14h | -30% ⬇️ |

### Análise da Variação

**Por que +8% de horas totais?**
- ➕ Integração WhatsApp (complexa e nova)
- ➕ 3 formulários adicionais de especialistas
- ➕ Painel administrativo completo
- ➕ Sistema de aprovação/notificações
- ➖ Setup reduzido (infra já existe)
- ➖ Menos documentação de arquitetura
- ➖ Equipe já familiarizada com stack

**Conclusão:** Apesar de setup reduzido, complexidade funcional aumenta ligeiramente o total.

---

## 🔍 Detalhamento: Formulários de Especialistas

### Premissa: 3 Formulários

Cada formulário de especialista segue padrão similar mas com campos específicos:

| Especialista | Campos Estimados | Validações Específicas |
|--------------|-----------------|------------------------|
| **Psicólogo** | ~20 campos | Avaliação psicológica, histórico |
| **Assistente Social** | ~25 campos | Situação socioeconômica, família |
| **Terapeuta Ocupacional** | ~18 campos | Habilidades funcionais, autonomia |

**Total estimado:** ~63 campos distribuídos

### Breakdown de Horas por Formulário

| Atividade | Horas por Form | Total (3 forms) |
|-----------|----------------|-----------------|
| Análise de requisitos | 1h | 3h |
| Backend (Models + API) | 3h | 9h |
| Frontend (Interface) | 2h | 6h |
| Validações | 1.5h | 4.5h |
| Testes | 1h | 3h |
| **TOTAL** | **8.5h** | **25.5h** |

**Arredondado:** ~26h para os 3 formulários

**Justificativa:** Campos seguem padrão similar (text, select, textarea, date). Após primeiro formulário, os demais são mais rápidos (reuso de componentes).

---

## 📋 Checklist de Validação

Ao final do projeto, validar:

- [ ] Horas reais vs estimadas por disciplina
- [ ] Principais desvios e causas
- [ ] Complexidade WhatsApp API vs estimativa
- [ ] Tempo de desenvolvimento dos formulários
- [ ] Aprendizados para Entrega 3

### Meta de Precisão

```
Desvio aceitável: ±15% (190h ± 28h)
Faixa esperada: 162h - 218h
Com margem incluída: até 218h
```

---

## 🔗 Referências

- [Precificação da Entrega 2](./precificacao-entrega-2.md)
- [Requisitos Detalhados - Entrega 2](./entrega-2-a-definir.md)
- [Estimativa de Horas - Entrega 1](../entrega-1/estimativa-horas-entrega-1.md)
- [Precificação - Entrega 1](../entrega-1/precificacao-projeto.md)
- [ADR-002: Arquitetura Técnica](../../adrs/ADR-002-arquitetura-tecnica.md)

---

**Última atualização:** Outubro 2025  
**Responsável:** CodeBoa Software  
**Status:** ✅ Estimativa Completa
