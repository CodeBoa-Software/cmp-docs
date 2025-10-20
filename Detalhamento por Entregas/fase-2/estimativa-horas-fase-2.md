# Estimativa de Horas - Fase 2

**Projeto:** Casa Mãe Paulistana  
**Entrega:** Triagem, Atendimentos e Oficinas (Fase 2)  
**Data de Entrega:** A definir  
**Data da Estimativa:** Outubro 2025  
**Versão:** 1.0

---

## 📊 Resumo Executivo

| Disciplina | Horas | % do Total | Complexidade |
|-----------|-------|------------|--------------|
| **1. Análise e Planejamento** | 21h | 13% | Média-Alta |
| **2. Setup de Infraestrutura** | 5h | 3% | Baixa |
| **3. Backend Development** | 51h | 31% | Alta |
| **4. Frontend Development** | 54h | 33% | Média |
| **5. Integração e Testes** | 24h | 14% | Média |
| **6. Documentação e Deploy** | 10h | 6% | Baixa |
| **TOTAL BASE** | **165h** | **100%** | |

### Margem de Contingência
```
Horas base: 165h
Margem para imprevistos (+10%): 17h
───────────────────────────────────
TOTAL COM MARGEM: 182h
```

**Justificativa da margem:**
- Múltiplos módulos interdependentes (Triagem, Atendimentos, Oficinas)
- Sistema de permissões complexo (profissionais vs admin)
- Validações de negócio específicas (controle de vagas, inscrições)
- Exportações em múltiplos formatos (Excel/CSV)
- Integração com dados da Fase 1
- Testes de fluxos completos envolvendo 3 módulos

---

## ⏱️ Detalhamento por Disciplina

### 1. Análise e Planejamento

| Atividade | Horas | Complexidade |
|-----------|-------|--------------|
| Refinamento de requisitos (3 módulos principais) | 8h | Média-Alta |
| Modelagem de dados (5 novas entidades + relacionamentos) | 1h | Média-Alta |
| Definição de APIs (contratos para 3 módulos) | 2h | Média |
| Design do sistema de permissões | 4h | Média-Alta |
| Planejamento de exportações e relatórios | 4h | Média |
| Planejamento de testes (3 fluxos principais) | 2h | Média |

**Subtotal:** 21h 

**Justificativa:** 
- Escopo com 3 módulos distintos mas interdependentes
- Sistema de permissões granular (admin, profissional, coordenador, recepção)
- Modelagem de dados complexa com múltiplos relacionamentos
- Integração com dados existentes da Fase 1

**Novas Entidades:**
- Responsável (entidade completa)
- Dependente
- Profissional
- Atendimento
- Oficina
- Inscrição
- Presença

---

### 2. Setup de Infraestrutura

| Atividade | Horas | Complexidade |
|-----------|-------|--------------|
| Configuração de permissões e roles | 2h | Baixa-Média |
| Setup de bibliotecas de exportação (Excel/CSV) | 2h | Baixa |
| Ajustes em CI/CD para novos módulos | 1h | Baixa |

**Subtotal:** 5h 

**Justificativa da redução:** 
- ✅ **Infraestrutura GCP já existente** (Cloud Run, Cloud SQL, Storage)
- ✅ **Ambiente de produção configurado**
- ✅ **CI/CD já funcional**
- Apenas extensões do banco e configurações adicionais necessárias

---

### 3. Backend Development (.NET)

| Atividade | Horas | Complexidade |
|-----------|-------|--------------|
| **MÓDULO DE TRIAGEM** | | |
| Models e DTOs (Responsável) | 1h | Média |
| Serviço de Triagem (salvamento, validações) | 2h | Média |
| API de Responsáveis (listagem, busca, filtros) | 3h | Média |
| **MÓDULO DE ATENDIMENTOS** | | |
| Models e DTOs (Profissional, Atendimento) | 2h | Média |
| CRUD de Profissionais | 1h | Baixa-Média |
| Serviço de Atendimentos (com permissões) | 3h | Média-Alta |
| API de Atendimentos (registro, histórico) | 3h | Média |
| Sistema de privacidade (apenas profissional/admin) | 2h | Média-Alta |
| **MÓDULO DE OFICINAS** | | |
| Models e DTOs (Oficina, Inscrição, Presença) | 2h | Média |
| CRUD de Oficinas | 2h | Média |
| Serviço de Inscrições (validações de vagas) | 3h | Alta |
| API de Presença (controle por encontro) | 2h | Média-Alta |
| **FUNCIONALIDADES TRANSVERSAIS** | | |
| Sistema de permissões e autorização | 6h | Alta |
| Serviço de exportação (Excel/CSV) | 5h | Média-Alta |
| Busca global de responsáveis | 2h | Baixa-Média |
| Middleware de logging e auditoria | 2h | Baixa-Média |
| Testes automatizados (backend) | 10h | Média |

**Subtotal:** 51h 

**Justificativa da complexidade:**
- **Sistema de Permissões:** Controle granular por perfil (admin, profissional, coordenador, recepção)
- **Validações de Negócio:** Controle de vagas, inscrições duplicadas, privacidade de atendimentos
- **Exportações:** Geração de Excel/CSV com formatação adequada para múltiplas entidades
- **Estatísticas:** Cálculos de frequência, métricas de atendimentos, indicadores do dashboard
- **Relacionamentos Complexos:** Responsável → Dependentes, Atendimentos, Inscrições → Oficinas → Presenças
- ✅ **Reutilização da estrutura existente:** MediatR, EntityFramework, padrões já estabelecidos na Fase 1

---

### 4. Frontend Development (React + Lovable)

| Atividade | Horas | Complexidade |
|-----------|-------|--------------|
| **LOVABLE AI - Geração de Telas** | 14h | Média |
| **Migração/Ajustes do código Lovable para API** | 10h | Média |
| **MÓDULO DE TRIAGEM** | | |
| Formulário de Triagem (responsável + dependentes) | 3h | Média |
| Tela: Lista de Responsáveis (busca, filtros) | 2h | Baixa-Média |
| Tela: Detalhes do Responsável (histórico completo) | 2h | Média |
| **MÓDULO DE ATENDIMENTOS** | | |
| CRUD de Profissionais | 2h | Baixa |
| Formulário de Registro de Atendimento | 3h | Média |
| Tela: Histórico de Atendimentos (filtros) | 2h | Baixa-Média |
| **MÓDULO DE OFICINAS** | | |
| CRUD de Oficinas | 3h | Média |
| Tela: Lista de Oficinas (busca, filtros) | 2h | Baixa-Média |
| Tela: Inscrição em Oficinas (validações) | 2h | Média |
| Tela: Gestão de Inscritos | 2h | Baixa-Média |
| Tela: Controle de Presença | 2h | Média |
| **FUNCIONALIDADES TRANSVERSAIS** | | |
| Dashboard Administrativo com métricas | 3h | Média |
| Busca Global | 1h | Baixa |
| Exportações (Excel/CSV) | 1h | Baixa |

**Subtotal:** 54h

**Justificativa da complexidade:**
- **Lovable AI:** Geração automática das telas principais, reduzindo tempo de desenvolvimento
- ✅ **App Admin já existente:** Reutilização da estrutura, componentes e layout da Fase 1
- ✅ **Shadcn/UI configurado:** Biblioteca de componentes já disponível
- **6 formulários principais:** Triagem, Edição Responsável, Profissional, Atendimento, Oficina, Presença
- **8 telas de visualização:** Listas, detalhes, históricos, dashboard
- **Validações client-side:** Controle de vagas, campos obrigatórios, formatos
- **Responsividade:** Mobile e desktop (já estabelecida na Fase 1)

---

### 5. Integração e Testes

| Atividade | Horas | Complexidade |
|-----------|-------|--------------|
| Testes de integração (API + DB) - 3 módulos | 8h | Média |
| Testes de permissões e autorização | 4h | Média-Alta |
| Testes de validações de negócio (vagas, inscrições) | 4h | Média |
| Testes de exportações (Excel/CSV) | 2h | Baixa-Média |
| Testes de fluxos completos (E2E - 3 módulos) | 4h | Média |
| Correção de bugs encontrados | 2h | Variável |

**Subtotal:** 24h

**Justificativa:** 
- 3 módulos independentes mas conectados (Triagem → Atendimentos → Oficinas)
- Sistema de permissões requer testes extensivos por perfil
- Validações de negócio críticas (controle de vagas, privacidade)
- ✅ **Infraestrutura de testes já existente** da Fase 1
- Menos testes de infraestrutura (GCP, emails, storage) já validados

---

### 6. Documentação e Deploy

| Atividade | Horas | Complexidade |
|-----------|-------|--------------|
| Documentação de API (OpenAPI/Swagger) - novos endpoints | 3h | Baixa-Média |
| Documentação de permissões e perfis | 2h | Baixa |
| README e guias de uso dos novos módulos | 2h | Baixa |
| Deploy em ambiente de produção (incremental) | 2h | Baixa-Média |
| Handover e treinamento da equipe | 1h | Baixa |

**Subtotal:** 10h

**Justificativa da redução:** 
- ✅ **Estrutura de documentação já existente**
- ✅ **Pipeline de deploy configurado**
- ✅ **Equipe já familiarizada com o sistema**
- Apenas documentação incremental dos novos módulos

---

## 👥 Perfis de Desenvolvedores Necessários

### Full-Stack Developer (React + .NET)
- Responsável por desenvolvimento dos 3 módulos
- Sistema de permissões e autorização
- Exportações e relatórios
- Integração com sistema existente da Fase 1
- Code review
- Testes (unitários, integração, E2E)
- Documentação técnica
- **100% do projeto = 165h**
- **Taxa horária sugerida:** R$ 200/h

---

## 🎯 Distribuição de Horas por Subfase

### Subfase 1: Módulo de Triagem

**Prazo:** 1-2 semanas

| Disciplina | Horas |
|-----------|-------|
| Análise e Planejamento | 7h |
| Setup de Infraestrutura | 2h |
| Backend Development | 6h |
| Frontend Development (Lovable + ajustes) | 11h |
| Integração e Testes | 8h |
| Documentação | 3h |
| **TOTAL SUBFASE 1** | **37h** |

**Entregas:**
- ✅ Formulário de Triagem funcional
- ✅ Criação de entidade Responsável e Dependentes
- ✅ Lista de Responsáveis com busca e filtros
- ✅ Visualização de detalhes completos
- ✅ Edição de informações cadastrais
- ✅ Exportação de dados (Excel/CSV)

---

### Subfase 2: Módulo de Atendimentos

**Prazo:** 1-2 semanas

| Disciplina | Horas |
|-----------|-------|
| Análise e Planejamento | 6h |
| Setup de Infraestrutura | 1h |
| Backend Development | 11h |
| Frontend Development (Lovable + ajustes) | 11h |
| Integração e Testes | 6h |
| Documentação | 2h |
| **TOTAL SUBFASE 2** | **37h** |

**Entregas:**
- ✅ CRUD de Profissionais
- ✅ Formulário de Registro de Atendimento
- ✅ Sistema de privacidade (profissional + admin)
- ✅ Histórico de Atendimentos por Responsável
- ✅ Filtros (data, especialidade, profissional)
- ✅ Estatísticas básicas
- ✅ Exportação de dados

---

### Subfase 3: Módulo de Oficinas

**Prazo:** 2-3 semanas

| Disciplina | Horas |
|-----------|-------|
| Análise e Planejamento | 8h |
| Setup de Infraestrutura | 2h |
| Backend Development | 13h |
| Frontend Development (Lovable + ajustes) | 14h |
| Integração e Testes | 6h |
| Documentação | 2h |
| **TOTAL SUBFASE 3** | **45h** |

**Entregas:**
- ✅ CRUD de Oficinas
- ✅ Sistema de Inscrições com controle de vagas
- ✅ Validações (vagas disponíveis, inscrições duplicadas)
- ✅ Lista de Inscritos por Oficina
- ✅ Controle de Presença por encontro
- ✅ Estatísticas de frequência
- ✅ Exportações (listas, relatórios de presença)

---

### Subfase 4: Integração Final e Dashboard

**Prazo:** 1 semana

| Disciplina | Horas |
|-----------|-------|
| Backend Development (permissões, dashboard, busca) | 21h |
| Frontend Development (dashboard, busca, ajustes) | 18h |
| Integração e Testes (E2E completo) | 4h |
| Documentação e Deploy | 3h |
| **TOTAL SUBFASE 4** | **46h** |

**Entregas:**
- ✅ Sistema de permissões completo
- ✅ Dashboard Administrativo com métricas
- ✅ Busca Global de Responsáveis
- ✅ Exportações em todos os módulos
- ✅ Testes E2E completos (3 módulos integrados)
- ✅ Documentação completa
- ✅ Deploy em produção

---

## 📅 Cronograma Estimado

### Timeline Total: 5-8 semanas

```
Semanas 1-2: Módulo de Triagem (37h)
├─ Análise e planejamento detalhado (7h)
├─ Extensão do banco de dados (2h)
├─ Backend: Triagem completa (6h)
├─ Frontend: Formulário + Listas (Lovable) (11h)
├─ Testes e ajustes (8h)
└─ Documentação inicial (3h)

Semanas 3-4: Módulo de Atendimentos (37h)
├─ Análise e planejamento (6h)
├─ Backend: Profissionais + Atendimentos (11h)
├─ Frontend: CRUD + Histórico (Lovable) (11h)
├─ Sistema de privacidade (incluído)
├─ Testes (6h)
└─ Documentação (2h)

Semanas 5-7: Módulo de Oficinas (45h)
├─ Análise e planejamento (8h)
├─ Backend: Oficinas + Inscrições + Presença (13h)
├─ Frontend: 5 telas principais (Lovable) (14h)
├─ Validações de vagas
├─ Testes (6h)
└─ Documentação (2h)

Semana 8: Integração Final e Dashboard (46h)
├─ Sistema de permissões completo (6h)
├─ Dashboard e métricas (7h)
├─ Busca global (3h)
├─ Exportações finais (5h)
├─ Testes E2E (4h)
├─ Ajustes finais (18h)
└─ Deploy e handover (3h)

──────────────────────────────────────────
FASE 2 COMPLETA (5-8 semanas = 165h)
```

---

## 💡 Considerações e Premissas

### Stack Tecnológica (Reutilizada da Fase 1)
- **Frontend:** React + Vite + TypeScript + Shadcn/UI + Tailwind CSS (gerado via Lovable AI)
- **Backend:** .NET (ASP.NET Core) + Entity Framework + MediatR
- **Banco de Dados:** PostgreSQL (Cloud SQL) - **já existente**
- **Cloud:** Google Cloud Platform (GCP) - **infraestrutura já configurada**
- **CI/CD:** GitHub Actions - **pipeline já funcional**

### Premissas
- ✅ Fase 1 concluída e em produção
- ✅ Infraestrutura GCP totalmente funcional
- ✅ App Admin interno já existente (Fase 1)
- ✅ Sistema de backend operacional
- ✅ Banco de dados PostgreSQL configurado
- ✅ CI/CD configurado
- ✅ Equipe familiarizada com a stack tecnológica
- Lovable AI disponível para geração de telas
- Requisitos estáveis durante desenvolvimento
- Feedback do cliente disponível entre subfases

### Economias em Relação à Fase 1
- **Infraestrutura:** ~15h economizadas (já configurada)
- **Setup de Projeto:** ~5h economizadas (estrutura já existente)
- **CI/CD:** ~3h economizadas (pipeline já funcional)
- **App Admin:** ~10h economizadas (layout e componentes reutilizados)
- **Sistema de autenticação:** ~8h economizadas (já implementado)
- **Serviço de email:** 0h (não necessário nesta fase)
- **Total economizado:** ~41h

### Riscos que Podem Impactar Horas
- **Sistema de Permissões:** Complexidade não prevista pode adicionar 5-10h
- **Exportações:** Formatações complexas podem adicionar 5-8h
- **Validações de Negócio:** Edge cases podem adicionar 5-10h
- **Integração com Fase 1:** Conflitos de dados podem adicionar 5-10h
- **Mudanças de requisitos:** Cada mudança significativa pode adicionar 10-20h
- **Performance com múltiplos módulos:** Otimizações podem adicionar 10-15h
- **Integração Lovable:** Ajustes no código gerado podem adicionar 5-10h

---

## 📊 Comparação: Fase 2 vs Fase 1

### Resumo Comparativo

| Métrica | Fase 1 | Fase 2 | Delta |
|---------|--------|--------|-------|
| **Horas Base** | 247h | 165h | -82h (-33%) |
| **Horas com Margem** | 259h | 182h | -77h (-30%) |
| **Disciplinas** | 6 | 6 | - |
| **Formulários Principais** | 1 | 6 | +5 |
| **Telas Administrativas** | 3 | 8+ | +5+ |
| **Módulos** | 1 | 3 | +2 |
| **Entidades de Dados** | 3 | 7 | +4 |
| **Complexidade Backend** | Alta | Alta | = |
| **Complexidade Frontend** | Média-Alta | Média | -1 |

### Justificativa da Redução de Horas

**Economia de 82h (-33%) em relação à Fase 1:**

1. **Infraestrutura (-18h):**
   - Fase 1: 23h (setup completo GCP, Cloud Run, Cloud SQL, Storage, Email)
   - Fase 2: 5h (apenas configurações adicionais)
   - **Economia: 18h**

2. **Análise e Planejamento (-7h):**
   - Fase 1: 28h (planejamento completo de infraestrutura e arquitetura)
   - Fase 2: 21h (foco em módulos, arquitetura já definida)
   - **Economia: 7h**

3. **Backend (-15h):**
   - Fase 1: 66h (setup completo, protocolo, emails, aprovação, agendamento, infraestrutura)
   - Fase 2: 51h (3 módulos, permissões, exportações, sem setup inicial)
   - **Economia: 15h** (reutilização de estrutura)

4. **Frontend (-9h em termos relativos):**
   - Fase 1: 63h (1 formulário + 3 telas + responsividade completa + app do zero)
   - Fase 2: 54h (6 formulários + 8 telas, mas com componentes reutilizados)
   - **Economia relativa: ~9h** (ganho de eficiência)

5. **Integração e Testes (-19h):**
   - Fase 1: 43h (testes de infraestrutura, emails, upload, workflows)
   - Fase 2: 24h (foco em lógica de negócio, infraestrutura já validada)
   - **Economia: 19h**

6. **Documentação e Deploy (-17h):**
   - Fase 1: 27h (documentação completa, setup de monitoring, handover extenso)
   - Fase 2: 10h (documentação incremental, deploy já automatizado)
   - **Economia: 17h**

**Total de Economia Líquida: 82h (-33%)**

---

## 📈 Análise de Complexidade por Módulo

### Módulo de Triagem
- **Complexidade:** Média-Alta
- **Horas:** ~37h
- **Justificativa:** Formulário complexo com múltiplas seções, criação de entidades relacionadas

### Módulo de Atendimentos
- **Complexidade:** Média
- **Horas:** ~37h
- **Justificativa:** Sistema de permissões e privacidade, CRUD relativamente simples

### Módulo de Oficinas
- **Complexidade:** Alta
- **Horas:** ~45h
- **Justificativa:** Controle de vagas, inscrições, presença por encontro, estatísticas

### Integrações e Dashboard
- **Complexidade:** Média-Alta
- **Horas:** ~46h
- **Justificativa:** Permissões granulares, métricas agregadas, busca global, exportações

---

## ✅ Checklist de Validação

### Ao final do projeto, validar:

- [ ] Horas reais vs estimadas por disciplina
- [ ] Principais desvios e causas
- [ ] Precisão do uso de Lovable AI
- [ ] Economia real com reutilização da Fase 1
- [ ] Performance do sistema de permissões
- [ ] Qualidade das exportações
- [ ] Testes em múltiplos perfis de usuário
- [ ] Aprendizados para próximas entregas
- [ ] Ajustes na precificação

### Meta de Precisão

```
Desvio aceitável: ±10% (165h ± 17h)
Faixa esperada: 148h - 182h
Com margem incluída: até 182h
```

---

## 🔗 Referências

- [Requisitos Detalhados - Fase 2](./fase-2-triagem-atendimentos-oficinas.md)
- [Estimativa de Horas - Fase 1](../fase-1/estimativa-horas-fase-1.md)
- [Precificação da Fase 2](./precificacao-fase-2.md)
- [Custos de Infraestrutura Mensal](../fase-1/custos-infraestrutura-mensal.md)

---

**Última atualização:** Outubro 2025  
**Responsável:** CodeBoa Software  
**Status:** ✅ Estimativa Completa - Fase 2 (Triagem, Atendimentos e Oficinas)
