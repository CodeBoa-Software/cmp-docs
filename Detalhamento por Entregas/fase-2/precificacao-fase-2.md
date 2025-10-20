# Precificação do Projeto - Fase 2

**Projeto:** Casa Mãe Paulistana  
**Entrega:** Triagem, Atendimentos e Oficinas (Fase 2)  
**Data:** Outubro 2025  
**Versão:** 1.0

### Funcionalidades Incluídas

#### ✅ Módulo de Triagem

##### Frontend (React + Lovable)
- Formulário de Triagem completo (responsável + dependentes)
- Tela de Lista de Responsáveis (busca e filtros)
- Tela de Detalhes do Responsável (histórico completo)
- Validações client-side
- Interface responsiva

##### Backend (.NET)
- Models e DTOs (Responsável)
- Serviço de Triagem (salvamento, validações)
- API de Responsáveis (listagem, busca, filtros)
- Criação de entidade completa no sistema

---

#### ✅ Módulo de Atendimentos Especializados

##### Frontend (React + Lovable)
- CRUD de Profissionais
- Formulário de Registro de Atendimento
- Tela de Histórico de Atendimentos (com filtros)

##### Backend (.NET)
- Models e DTOs (Profissional, Atendimento)
- CRUD de Profissionais
- Serviço de Atendimentos (com permissões)
- API de Atendimentos (registro, histórico)
- Sistema de privacidade (apenas profissional/admin visualizam)

---

#### ✅ Módulo de Oficinas

##### Frontend (React + Lovable)
- CRUD de Oficinas
- Tela de Lista de Oficinas (busca e filtros)
- Tela de Inscrição em Oficinas (validações)
- Tela de Gestão de Inscritos
- Tela de Controle de Presença

##### Backend (.NET)
- Models e DTOs (Oficina, Inscrição, Presença)
- CRUD de Oficinas
- Serviço de Inscrições (validações de vagas)
- API de Presença (controle por encontro)
- Estatísticas de frequência

---

#### ✅ Funcionalidades Transversais

##### Frontend (React + Lovable)
- Dashboard Administrativo com métricas
- Busca Global de Responsáveis
- Exportações (Excel/CSV) em todas as telas

##### Backend (.NET)
- Sistema de permissões e autorização (4 perfis)
- Serviço de exportação (Excel/CSV)
- Busca global de responsáveis
- Middleware de logging e auditoria
- Testes automatizados completos

---

#### ✅ Infraestrutura (GCP)
- Extensão do banco de dados (novas entidades)
- Configuração de permissões e roles
- Setup de bibliotecas de exportação (Excel/CSV)
- Ajustes em CI/CD para novos módulos
- **Reutilização da infraestrutura existente da Fase 1**

#### ✅ Qualidade
- Testes unitários (backend)
- Testes de integração (API + DB) - 3 módulos
- Testes de permissões e autorização
- Testes de validações de negócio (vagas, inscrições)
- Testes de exportações (Excel/CSV)
- Testes E2E (3 fluxos completos)
- Code review
- Documentação técnica incremental

---

## ⏱️ Estimativa de Horas de Desenvolvimento

### Resumo Executivo

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

### Principais Economias em Relação à Fase 1

**Economia de 82h (-33%) comparado à Fase 1:**

1. **Infraestrutura (-18h):** GCP, Cloud Run, Cloud SQL, Storage já configurados
2. **Análise e Planejamento (-7h):** Arquitetura já definida na Fase 1
3. **Backend (-15h):** Reutilização de estrutura (MediatR, EntityFramework, padrões)
4. **Frontend (-9h):** App Admin, componentes e layout já existentes
5. **Integração e Testes (-19h):** Infraestrutura de testes já validada
6. **Documentação e Deploy (-17h):** Pipeline CI/CD e documentação já existentes

**Apesar de mais funcionalidades** (3 módulos, 6 formulários, 8+ telas), a Fase 2 é mais eficiente devido à reutilização da infraestrutura da Fase 1.

> 📋 **Detalhamento completo:** Para ver o breakdown detalhado de horas por atividade, complexidades e justificativas, consulte [Estimativa de Horas - Fase 2](./estimativa-horas-fase-2.md)

---

## 💰 Modelos de Precificação

### Premissas

#### 👥 Perfis de Desenvolvedores Necessários

### Full-Stack Developer (React + .NET)
- Responsável por desenvolvimento dos 3 módulos
- Sistema de permissões e autorização
- Exportações e relatórios
- Integração com sistema existente da Fase 1
- Code review
- Testes (unitários, integração, E2E)
- Documentação técnica
- **100% do projeto = 182h (165h base + 17h margem)**
- **Taxa horária sugerida:** R$ 200/h

---

## 💵 Precificação Final

### Estrutura em 4 Subfases

#### **Subfase 1: Módulo de Triagem - R$ 8.140**

**Prazo:** 1-2 semanas  
**Horas:** 37h (incluídas na margem proporcional)

**Entregas:**
- ✅ Formulário de Triagem funcional (responsável + dependentes)
- ✅ Criação de entidade Responsável e Dependentes
- ✅ Lista de Responsáveis com busca e filtros
- ✅ Visualização de detalhes completos
- ✅ Edição de informações cadastrais
- ✅ Exportação de dados (Excel/CSV)

**Objetivo:** Permitir registro completo de dados coletados na triagem presencial.

**Pagamento:**
- 50% no início da Fase 2 (R$ 4.070)
- 50% na entrega da subfase (R$ 4.070)

---

#### **Subfase 2: Módulo de Atendimentos - R$ 8.140**

**Prazo:** 1-2 semanas  
**Horas:** 37h (incluídas na margem proporcional)

**Entregas:**
- ✅ CRUD de Profissionais (advogados, psicólogos, assistentes sociais)
- ✅ Formulário de Registro de Atendimento
- ✅ Sistema de privacidade (apenas profissional e admin visualizam)
- ✅ Histórico de Atendimentos por Responsável
- ✅ Filtros (data, especialidade, profissional)
- ✅ Estatísticas básicas
- ✅ Exportação de dados

**Objetivo:** Registrar atendimentos especializados realizados.

**Pagamento:**
- 100% na entrega da subfase (R$ 8.140)

---

#### **Subfase 3: Módulo de Oficinas - R$ 9.900**

**Prazo:** 2-3 semanas  
**Horas:** 45h (incluídas na margem proporcional)

**Entregas:**
- ✅ CRUD de Oficinas (cadastro, edição, duplicação)
- ✅ Sistema de Inscrições com controle de vagas
- ✅ Validações (vagas disponíveis, inscrições duplicadas)
- ✅ Lista de Inscritos por Oficina
- ✅ Controle de Presença por encontro
- ✅ Estatísticas de frequência
- ✅ Exportações (listas de inscritos, relatórios de presença)

**Objetivo:** Gestão completa de oficinas oferecidas, desde inscrição até controle de frequência.

**Pagamento:**
- 100% na entrega da subfase (R$ 9.900)

---

#### **Subfase 4: Integração Final e Dashboard - R$ 10.120**

**Prazo:** 1 semana  
**Horas:** 46h (incluídas na margem proporcional)

**Entregas:**
- ✅ Sistema de permissões completo (4 perfis: admin, profissional, coordenador, recepção)
- ✅ Dashboard Administrativo com métricas gerais
- ✅ Busca Global de Responsáveis (nome, CPF, protocolo)
- ✅ Exportações em todos os módulos funcionando
- ✅ Testes E2E completos (3 módulos integrados)
- ✅ Documentação técnica completa
- ✅ Deploy em produção
- ✅ Handover com treinamento da equipe

**Objetivo:** Sistema completo, integrado, testado e em produção.

**Pagamento:**
- 100% na entrega final (R$ 10.120)

---

### Total

```
Subfase 1 (Triagem):                R$ 8.140
Subfase 2 (Atendimentos):           R$ 8.140
Subfase 3 (Oficinas):               R$ 9.900
Subfase 4 (Integração + Dashboard): R$ 10.120
──────────────────────────────────────────
TOTAL FASE 2:                       R$ 36.300
```

**Nota:** Este valor inclui a margem de contingência de 10% (+17h) distribuída proporcionalmente entre as quatro subfases para cobrir imprevistos como:
- Complexidades não previstas no sistema de permissões
- Ajustes de requisitos durante desenvolvimento
- Edge cases nas validações de negócio
- Formatações complexas nas exportações
- Integração com dados da Fase 1
- Refinamentos de UX baseados em feedback

---

### Características

| Aspecto | Detalhes |
|---------|----------|
| **Valor total** | R$ 36.300 (fixo, com margem de 10%) |
| **Risco para cliente** | Baixo (entregas incrementais, validação contínua) |
| **Risco para fornecedor** | Baixo (margem incluída, infraestrutura já existente) |
| **Flexibilidade** | Alta (4 subfases independentes) |
| **Transparência** | Alta (entregas semanais) |
| **Pagamento** | Escalonado (11% + 22% + 27% + 28% = 88% após início) |

### Vantagens deste Planejamento

```
✅ Cliente valida cada módulo progressivamente (1-2 semanas cada)
✅ Menor risco de retrabalho (feedback contínuo)
✅ Pagamento escalonado (melhor cashflow para ambos)
✅ Possibilidade de priorizar módulos conforme necessidade
✅ Demonstra valor rapidamente
✅ Integração gradual reduz complexidade
✅ Reduz ansiedade do cliente (vê progresso semanal)
✅ Economia de 33% comparado à Fase 1 (mesma taxa, menos horas)
```

### Cronograma de Pagamento

| Marco | Valor | % | Acumulado |
|-------|-------|-----------|-----------|
| **Início da Fase 2 (50% Subfase 1)** | R$ 4.070 | 11% | R$ 4.070 |
| **Entrega Subfase 1 (Triagem)** | R$ 4.070 | 11% | R$ 8.140 |
| **Entrega Subfase 2 (Atendimentos)** | R$ 8.140 | 22% | R$ 16.280 |
| **Entrega Subfase 3 (Oficinas)** | R$ 9.900 | 27% | R$ 26.180 |
| **Entrega Final (Dashboard + Integração)** | R$ 10.120 | 28% | R$ 36.300 |

---

## 🎯 Proposta Comercial Recomendada

### Pacote: Sistema de Gestão Interna CMP - Fase 2

```markdown
═══════════════════════════════════════════════════════
INVESTIMENTO: R$ 36.300 (com margem de 10% incluída)
═══════════════════════════════════════════════════════

SUBFASE 1 - MÓDULO DE TRIAGEM (1-2 semanas)
├─ Investimento: R$ 8.140 (37h)
├─ Pagamento: 50% início + 50% entrega
└─ Entrega: Formulário + Lista + Detalhes + Exportação

SUBFASE 2 - MÓDULO DE ATENDIMENTOS (1-2 semanas)
├─ Investimento: R$ 8.140 (37h)
├─ Pagamento: 100% na entrega
└─ Entrega: Profissionais + Registro + Histórico + Privacidade

SUBFASE 3 - MÓDULO DE OFICINAS (2-3 semanas)
├─ Investimento: R$ 9.900 (45h)
├─ Pagamento: 100% na entrega
└─ Entrega: Oficinas + Inscrições + Presença + Estatísticas

SUBFASE 4 - INTEGRAÇÃO + DASHBOARD (1 semana)
├─ Investimento: R$ 10.120 (46h)
├─ Pagamento: 100% na entrega final
└─ Entrega: Permissões + Dashboard + Busca + Testes E2E

PRAZO TOTAL: 5-8 semanas
GARANTIA: 30 dias pós entrega final

MARGEM DE CONTINGÊNCIA: +10% (17h) incluída para imprevistos
```

---

### 📦 O que está INCLUÍDO

#### ✅ Desenvolvimento Completo de 3 Módulos

**Módulo de Triagem:**
- Formulário completo (responsável + dependentes)
- Lista com busca e filtros
- Visualização de detalhes e histórico
- Edição de informações
- Exportação Excel/CSV

**Módulo de Atendimentos:**
- CRUD de Profissionais (3 especialidades)
- Registro de Atendimentos
- Sistema de privacidade
- Histórico completo com filtros
- Estatísticas básicas
- Exportação Excel/CSV

**Módulo de Oficinas:**
- CRUD de Oficinas
- Sistema de Inscrições (controle de vagas)
- Gestão de Inscritos
- Controle de Presença por encontro
- Estatísticas de frequência
- Exportações múltiplas

**Funcionalidades Transversais:**
- Dashboard Administrativo com métricas
- Busca Global de Responsáveis
- Sistema de Permissões (4 perfis)
- Exportações em todos os módulos

#### ✅ Reutilização da Infraestrutura da Fase 1
- Cloud Run (Frontend + Backend) - **já existente**
- Cloud SQL PostgreSQL - **já existente**
- CI/CD automatizado - **já existente**
- Monitoring e alertas - **já existente**
- Sistema de autenticação - **já existente**

#### ✅ Extensões de Infraestrutura
- Novas entidades no banco de dados (7 entidades)
- Configuração de permissões e roles
- Bibliotecas de exportação (Excel/CSV)
- Ajustes no CI/CD para novos módulos

#### ✅ Qualidade Assegurada
- Testes unitários (backend)
- Testes de integração (3 módulos)
- Testes de permissões e autorização
- Testes de validações de negócio
- Testes de exportações
- Testes E2E (fluxos completos)
- Code review completo
- Conformidade LGPD (audit trail)

#### ✅ Documentação Técnica
- API documentation (OpenAPI/Swagger) - novos endpoints
- Documentação de permissões e perfis
- README e guias de uso dos novos módulos
- Deploy incremental
- Handover com equipe técnica (1h)

#### ✅ Suporte Pós-Deploy
- 30 dias de garantia
- Correção de bugs críticos
- Suporte via email (SLA 48h)
- 1 sessão de ajustes pós-produção

---

### ❌ O que NÃO está incluído

```
⚠️ Custos de infraestrutura GCP (~R$ 479-926/mês)
   Mesmo valor da Fase 1 - infraestrutura já existente
   Veja: ../fase-1/custos-infraestrutura-mensal.md

⚠️ Não há custos adicionais de email (não necessário na Fase 2)

⚠️ Treinamento extensivo além do handover inicial (1h incluída)
   - Treinamento adicional pode ser contratado: R$ 200/h

⚠️ Features fora do escopo da Fase 2:
   - Sistema de agendamentos (será Fase 3)
   - Upload de documentos/imagens (foi Fase 1)
   - Dashboards avançados com gráficos (será Fase 3)
   - Relatórios customizados complexos

⚠️ Manutenção contínua pós-garantia
   (pode ser contratada separadamente)

⚠️ Integração com sistemas externos (ex: WhatsApp Business API)
   (será avaliado em fases futuras)
```

---

## 💡 Opções de Desconto

### 1. Pagamento Antecipado (À Vista)

```
Valor normal: R$ 36.300
Desconto: -8%
──────────────────────────
Valor à vista: R$ 33.396

Economia: R$ 2.904
```

**Condições:**
- Pagamento 100% antecipado
- Melhora cashflow do fornecedor
- Reduz risco de inadimplência

---

### 2. Combo Fase 1 + Fase 2

```
Fase 1 (Cadastro + Aprovação):         R$ 51.800
Fase 2 (Triagem + Atendimentos + Oficinas): R$ 36.300
───────────────────────────────────────────────────
Total sem desconto:                    R$ 88.100

Desconto (fechamento conjunto): -10%
───────────────────────────────────────────────────
VALOR TOTAL COM DESCONTO:              R$ 79.290

Economia total: R$ 8.810
```

**Vantagens:**
- Continuidade garantida do projeto
- Redução significativa de custo
- Melhor planejamento de longo prazo
- Equipe dedicada e já familiarizada com o projeto
- Não há ramp-up entre fases

---

### 3. Fechamento de Múltiplas Entregas (Roadmap Completo)

```
Fase 1 (Cadastro + Aprovação):              R$ 51.800
Fase 2 (Triagem + Atendimentos + Oficinas): R$ 36.300
Fase 3 (Agendamentos + Dashboards - estimativa): R$ 42.000
───────────────────────────────────────────────────────────
Total sem desconto:                         R$ 130.100

Desconto (roadmap completo): -15%
───────────────────────────────────────────────────────────
VALOR TOTAL COM DESCONTO:                   R$ 110.585

Economia total: R$ 19.515
```

**Vantagens:**
- Sistema completo garantido
- Máxima economia (15% de desconto)
- Planejamento de longo prazo
- Equipe dedicada por 4-6 meses
- Evolução contínua do sistema

---

## 🔍 Justificativa do Preço

### Por que R$ 36.300?

#### 1. Complexidade Técnica

```
✅ 3 módulos distintos mas integrados (Triagem, Atendimentos, Oficinas)
✅ Sistema de permissões granular (4 perfis diferentes)
✅ 6 formulários principais (complexos e médios)
✅ 8+ telas de visualização (listas, detalhes, históricos)
✅ Controle de vagas em oficinas (validações complexas)
✅ Sistema de presença por encontro
✅ Estatísticas de frequência
✅ Exportações em múltiplos formatos (Excel/CSV)
✅ Dashboard com métricas agregadas
✅ Busca global unificada
✅ Privacidade de atendimentos (apenas profissional/admin)
✅ Validações de negócio específicas
✅ Conformidade LGPD (audit trail completo)
✅ Interface responsiva (mobile e desktop)
```

#### 2. Economia com Reutilização

```
✅ Infraestrutura GCP já configurada (-18h)
✅ App Admin já existente (-9h)
✅ Padrões e arquitetura definidos (-7h)
✅ Backend estruturado (MediatR, EF) (-15h)
✅ CI/CD funcional (-3h)
✅ Sistema de autenticação pronto (-8h)
✅ Infraestrutura de testes (-19h)
✅ Documentação base (-17h)

Total economizado: 96h (que seriam ~R$ 19.200)
```

**Sem a Fase 1, esta Fase 2 custaria ~R$ 55.500**  
**Com reutilização: R$ 36.300 (economia de 35%)**

#### 3. Qualidade Garantida

```
✅ Testes automatizados (unitários + integração + E2E)
✅ Testes de permissões extensivos
✅ Testes de exportações
✅ Code review por senior developer
✅ CI/CD para deploys seguros
✅ Documentação técnica incremental
✅ 30 dias de garantia pós-deploy
✅ Sistema integrado com Fase 1
```

#### 4. Comparação Fase 1 vs Fase 2

| Métrica | Fase 1 | Fase 2 | Diferença |
|---------|--------|--------|-----------|
| **Horas Base** | 247h | 165h | -82h (-33%) |
| **Horas com Margem** | 259h | 182h | -77h (-30%) |
| **Preço** | R$ 51.800 | R$ 36.300 | -R$ 15.500 (-30%) |
| **Formulários** | 1 | 6 | +5 |
| **Telas Admin** | 3 | 8+ | +5+ |
| **Módulos** | 1 | 3 | +2 |
| **Custo por Hora** | R$ 200 | R$ 200 | Igual |

**Conclusão:** Fase 2 entrega 3x mais módulos por 30% menos investimento, graças à reutilização da infraestrutura da Fase 1.

#### 5. Comparação de Mercado

| Solução | Custo Estimado | Trade-offs |
|---------|----------------|------------|
| **Freelancer "barato"** | R$ 18-25k | ⚠️ Sem integração com Fase 1, risco alto de incompatibilidade |
| **Software pronto (SaaS)** | R$ 800-1500/mês | ⚠️ Vendor lock-in, sem customização para este workflow |
| **Agência grande** | R$ 80-120k | ✅ Qualidade, ⚠️ Muito caro, overhead alto |
| **CodeBoa (Proposta)** | R$ 36.300 | ✅ Qualidade, ✅ Integração garantida, ✅ Preço justo ⭐ |

---

## 📋 Próximos Passos

### Para Fechar a Fase 2

1. **Validar conclusão da Fase 1**
   - Sistema de cadastro e aprovação em produção
   - Infraestrutura GCP estável
   - Dados de cadastros aprovados disponíveis
   
2. **Validar escopo da Fase 2** com stakeholders
   - Confirmar requisitos dos 3 módulos
   - Esclarecer dúvidas sobre funcionalidades
   - Definir prioridade entre subfases (se necessário)
   
3. **Escolher modelo de pagamento**
   - Preço Fixo em 4 Subfases - **Recomendado** (R$ 36.300)
   - À Vista com Desconto (R$ 33.396)
   - Combo Fase 1 + Fase 2 com Desconto (R$ 79.290)
   
4. **Definir perfis de usuários**
   - Administrador (acesso completo)
   - Profissionais (registro e visualização de atendimentos)
   - Coordenadores (visualização e estatísticas)
   - Recepção (funções operacionais)
   
5. **Elaborar contrato** (SOW - Statement of Work)
   - Escopo detalhado (3 módulos)
   - Cronograma de entregas (4 subfases)
   - Termos de pagamento (5 marcos)
   - Garantias e SLAs
   - Dependência da Fase 1
   
6. **Kickoff meeting**
   - Alinhamento técnico
   - Revisão da arquitetura existente
   - Definição de comunicação
   - Planejamento das subfases
   
7. **Início do desenvolvimento**
   - Sprint 0 (análise e planejamento)
   - Sprints semanais por subfase
   - Demos ao final de cada subfase

---

## 📊 Resumo Executivo

### Investimento vs Valor Entregue

```markdown
INVESTIMENTO TOTAL: R$ 36.300

VALOR ENTREGUE:
├─ 3 Módulos Completos
│  ├─ Triagem (1 formulário + 2 telas)
│  ├─ Atendimentos (2 formulários + 1 tela)
│  └─ Oficinas (1 formulário + 4 telas)
│
├─ 7 Novas Entidades de Dados
│  (Responsável, Dependente, Profissional, Atendimento,
│   Oficina, Inscrição, Presença)
│
├─ Sistema de Permissões (4 perfis)
├─ Dashboard com Métricas
├─ Busca Global
├─ Exportações Excel/CSV (todas as telas)
├─ Testes Completos (unitários + integração + E2E)
├─ Documentação Técnica
└─ 30 dias de Garantia

ECONOMIA COMPARADA À FASE 1: -30%
(Mesma taxa/hora, 30% menos horas devido à reutilização)

ROI ESTIMADO: Alto
(Sistema completo de gestão interna operacional)
```

---

## 📞 Contato

**Dúvidas sobre precificação ou proposta?**

CodeBoa Software  
Email: [contato]  
Telefone: [telefone]

---

## 📄 Anexos

### Documentos Relacionados

- [Requisitos Detalhados - Fase 2](./fase-2-triagem-atendimentos-oficinas.md)
- [Estimativa de Horas - Fase 2](./estimativa-horas-fase-2.md)
- [Precificação - Fase 1](../fase-1/precificacao-projeto.md)
- [Custos de Infraestrutura Mensal](../fase-1/custos-infraestrutura-mensal.md)

---

**Última atualização:** Outubro 2025  
**Responsável:** CodeBoa Software  
**Validade da proposta:** 30 dias  
**Pré-requisito:** Fase 1 concluída e em produção
