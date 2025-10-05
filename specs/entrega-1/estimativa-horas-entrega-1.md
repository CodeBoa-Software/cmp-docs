# Estimativa de Horas - Entrega 1

**Projeto:** Casa Mãe Paulistana  
**Entrega:** Sistema de Pré-Cadastro   
**Data:** Outubro 2025  
**Versão:** 1.0

---

## 📊 Resumo Executivo

| Disciplina | Horas | % do Total | Complexidade |
|-----------|-------|------------|--------------|
| **1. Análise e Planejamento** | 24h | 14% | Média |
| **2. Setup de Infraestrutura** | 30h | 17% | Alta |
| **3. Backend Development** | 49h | 28% | Alta |
| **4. Frontend Development** | 29h | 16% | Média-Alta |
| **5. Integração e Testes** | 24h | 14% | Média-Alta |
| **6. Documentação e Deploy** | 20h | 11% | Baixa-Média |
| **TOTAL BASE** | **176h** | **100%** | |

### Margem de Contingência
```
Horas base: 176h
Margem para imprevistos (+15%): 26h
───────────────────────────────────
TOTAL COM MARGEM: 202h
```

**Justificativa da margem:**
- Integrações externas podem ter desafios não previstos
- Requisitos podem ser refinados durante desenvolvimento
- Testes podem descobrir edge cases
- Ajustes de UX baseados em feedback

---

## ⏱️ Detalhamento por Disciplina

### 1. Análise e Planejamento

| Atividade | Horas | Complexidade |
|-----------|-------|--------------|
| Refinamento de requisitos | 4h | Baixa |
| Modelagem de dados (schema DB) | 4h | Média |
| Desenho de arquitetura | 4h | Média |
| Definição de APIs (contratos) | 4h | Média |
| Planejamento de testes | 4h | Baixa |
| Documentação técnica inicial | 4h | Baixa |

**Subtotal:** 24h

---

### 2. Setup de Infraestrutura

| Atividade | Horas | Complexidade |
|-----------|-------|--------------|
| Configuração GCP (projeto, billing, IAM) | 4h | Média |
| Setup Cloud Run (Frontend) | 4h | Média |
| Setup Cloud Run (Backend) | 4h | Média |
| Provisionamento AlloyDB/Cloud SQL | 4h | Alta |
| Configuração Google Drive API | 4h | Alta |
| Setup Cloud Storage (backup + lifecycle) | 2h | Baixa |
| Configuração de secrets/env vars | 3h | Baixa |
| CI/CD básico (GitHub Actions) | 5h | Média-Alta |

**Subtotal:** 30h

**Justificativa da complexidade:** Infraestrutura GCP específica requer conhecimento especializado. Integração Google Drive API pode ter desafios de autenticação e permissões.

---

### 3. Backend Development (.NET)

| Atividade | Horas | Complexidade |
|-----------|-------|--------------||
| Setup projeto .NET (estrutura, DI, config) | 4h | Baixa |
| Mapeamento do Domínio (Models, DTOs, mappings) | 4h | Baixa |
| Configuração EntityFramework | 4h | Média |
| Definição dos fluxos principais (MediatR) | 4h | Média |
| Serviço de validação (dados + arquivos) | 6h | Média-Alta |
| Integração Google Drive API | 8h | **Alta** |
| Controller de cadastro + endpoints | 3h | Baixa |
| Middleware de erros e logging | 4h | Média |
| Testes unitários (cobertura 70%) | 12h | Média |

**Subtotal:** 49h

**Justificativa da complexidade:**
- Google Drive API: autenticação OAuth2, upload de arquivos grandes, organização em pastas, tratamento de erros
- Validações complexas: múltiplos formatos de arquivo, tamanhos, tipos, dados pessoais
- Conformidade LGPD requer audit trail detalhado
- MediatR pattern: Commands/Queries com handlers dedicados, pipeline behaviors para cross-cutting concerns

---

### 4. Frontend Development (React)

| Atividade | Horas | Complexidade |
|-----------|-------|--------------|
| Setup React + Vite + TypeScript | | |
| Formulário em forma de chat | | |
| Upload de arquivos (drag-n-drop, preview, progresso) | | |
| Validações client-side | | |
| Lovable | 10h | Média |
| Migração de DB direto para API | 6h | Média |
| Tratamento de erros e loading states | 4h | Média |
| Responsividade e otimização mobile | 6h | Média |
| Testes E2E (Playwright - fluxos principais) | 8h | Média |

**Subtotal:** 29h

**Justificativa da complexidade:**
- Upload de arquivos: drag-n-drop, preview de PDFs/imagens, barra de progresso, validação de tamanho antes de enviar, tratamento de erros de rede
- Multi-step form: navegação entre passos, validação por etapa, persistência de dados, UX fluida
- Mobile: testes em diversos dispositivos, captura de câmera, seleção de galeria

---

### 5. Integração e Testes

| Atividade | Horas | Complexidade |
|-----------|-------|--------------|
| Testes de integração (API + DB) | 8h | Média |
| Testes de upload (Drive + Storage + DB) | 6h | Alta |
| Testes de validação end-to-end | 4h | Média |
| Correção de bugs encontrados | 6h | Variável |

**Subtotal:** 24h

**Justificativa:** Integração com Google Drive e uploads de arquivos grandes requerem testes extensivos em diferentes cenários (conexão lenta, arquivos corrompidos, etc).

---

### 6. Documentação e Deploy

| Atividade | Horas | Complexidade |
|-----------|-------|--------------|
| Documentação de API (OpenAPI/Swagger) | 4h | Baixa |
| README e guias de setup | 3h | Baixa |
| Documentação de deploy e runbooks | 3h | Média |
| Deploy em ambiente de produção | 4h | Média |
| Configuração de monitoring e alertas | 3h | Média |
| Handover e treinamento básico da equipe | 3h | Baixa |

**Subtotal:** 20h

---

## 👥 Perfis de Desenvolvedores Necessários

### Full-Stack Developer (React + .NET)
- Responsável por arquitetura e features críticas
- Integração Google Drive API
- Setup de infraestrutura GCP
- Code review
- Testes (unitários, integração, E2E)
- Documentação técnica
- Refinamentos e ajustes
- **100% do projeto = 176h**
- **Taxa horária sugerida:** R$ 200/h

---

## 🎯 Distribuição de Horas por Fase

### Fase 1: MVP Funcional

**Prazo:** 3 semanas

| Disciplina | Horas |
|-----------|-------|
| Análise e Planejamento | 18h |
| Setup de Infraestrutura | 25h |
| Backend Development | 32h |
| Frontend Development | 20h |
| Integração e Testes | 15h |
| Documentação e Deploy | 10h |
| **TOTAL FASE 1** | **120h** |

**Entregas:**
- ✅ Formulário funcional (sem polimento visual excessivo)
- ✅ Upload avançado (drag-n-drop, preview, progresso)
- ✅ Integração Drive + PostgreSQL
- ✅ Backend completo (APIs + validações)
- ✅ Deploy em ambiente de produção
- ✅ Testes básicos de funcionamento

---

### Fase 2: Refinamento e Produção

**Prazo:** 2-5 semanas

| Disciplina | Horas |
|-----------|-------|
| Análise e Planejamento (ajustes) | 6h |
| Setup de Infraestrutura (ajustes) | 5h |
| Backend Development (refinamentos) | 17h |
| Frontend Development (polimento) | 9h |
| Integração e Testes (completos) | 9h |
| Documentação e Deploy | 10h |
| **TOTAL FASE 2** | **56h** |

**Entregas:**
- ✅ UX/UI polido (Shadcn/UI completo)
- ✅ Validações completas (client + server)
- ✅ Responsividade mobile perfeita
- ✅ Testes automatizados (E2E + unitários)
- ✅ Monitoring e alertas configurados
- ✅ Documentação completa
- ✅ Handover com treinamento

---

## 💡 Considerações e Premissas

### Stack Tecnológica Definida
- **Frontend:** React + Vite + TypeScript + Shadcn/UI + Tailwind CSS (gerado via Lovable AI)
- **Backend:** .NET (ASP.NET Core) + Entity Framework + MediatR
- **Banco de Dados:** PostgreSQL (AlloyDB ou Cloud SQL)
- **Storage:** Google Drive API + Cloud Storage (backup)
- **Cloud:** Google Cloud Platform (GCP)
- **CI/CD:** GitHub Actions

### Premissas
- Equipe dedicada com experiência em React e .NET
- Acesso às credenciais GCP e Google Drive API
- Requisitos estáveis durante desenvolvimento
- Feedback do cliente disponível entre fases
- Ambiente de desenvolvimento configurado

### Riscos que Podem Impactar Horas
- **Integração Google Drive API:** Complexidade de autenticação OAuth2 pode aumentar em 10-20%
- **Upload de arquivos grandes:** Performance e tratamento de erros podem adicionar 5-10h
- **Mudanças de requisitos:** Cada mudança significativa pode adicionar 10-30h
- **Complexidade LGPD não prevista:** Auditoria adicional pode adicionar 5-15h
- **Performance com alto volume:** Otimizações podem adicionar 10-20h

---

## 📅 Cronograma Estimado

### Timeline Total: 5-8 semanas

```
Semana 1: Análise + Setup (43h)
├─ Refinamento requisitos e arquitetura (18h)
├─ Infraestrutura GCP completa (25h)
└─ Setup projeto (Backend + Frontend)

Semana 2: Desenvolvimento Core (52h)
├─ Backend APIs e integrações (32h)
├─ Frontend formulário chat (20h)
└─ Upload de arquivos

Semana 3: Finalização MVP + Deploy Produção (25h)
├─ Testes integração (15h)
├─ Correções críticas
└─ Deploy em PRODUÇÃO (10h)

──────────────────────────────────────────
FASE 1 COMPLETA - MVP EM PRODUÇÃO (3 semanas = 120h)

Semanas 4-8: Refinamento e Melhorias (56h)
├─ Ajustes baseados em feedback (6h Análise + 5h Infra)
├─ Refinamentos backend (17h)
├─ Polimento frontend (9h)
├─ Testes E2E extensivos (9h)
└─ Documentação completa e handover (10h)

──────────────────────────────────────────
FASE 2 COMPLETA (2-5 semanas após MVP = 56h)
```

---

## 📊 Comparação: Estimativa vs Realidade

### Checklist de Validação

Ao final do projeto, validar:

- [ ] Horas reais vs estimadas por disciplina
- [ ] Principais desvios e causas
- [ ] Aprendizados para próximas entregas
- [ ] Ajustes na precificação

### Meta de Precisão

```
Desvio aceitável: ±15% (176h ± 26h)
Faixa esperada: 150h - 202h
Com margem incluída: até 202h
```

---

## 🔗 Referências

- [Precificação do Projeto](./precificacao-projeto.md)
- [Requisitos Detalhados - Entrega 1](./entrega-1-22-outubro.md)
- [Custos de Infraestrutura Mensal](./custos-infraestrutura-mensal.md)
- [ADR-002: Arquitetura Técnica](../../adrs/ADR-002-arquitetura-tecnica.md)
- [ADR-003: Armazenamento de Documentos](../../adrs/ADR-003-armazenamento-documentos.md)

---

**Última atualização:** Outubro 2025  
**Responsável:** CodeBoa Software  
**Status:** ✅ Estimativa Completa
