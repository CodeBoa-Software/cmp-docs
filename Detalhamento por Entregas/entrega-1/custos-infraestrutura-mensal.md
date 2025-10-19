# Custos de Infraestrutura Mensal - Entrega 1

**Projeto:** Casa Mãe Paulistana  
**Data:** Outubro 2025  
**Versão:** 1.0

---

## 📊 Volume Esperado

### Premissas de Uso
- **3.000 cadastros/mês** (volume estimado)
- **4 documentos obrigatórios** por cadastro
- **12.000 uploads/mês** total
- **Tamanho médio:** 3MB por arquivo
- **Volume mensal:** ~36GB de documentos

---

## 💰 Detalhamento de Custos (Google Cloud Platform)

### 1. Cloud Run - Frontend (React)

**Funcionalidade:** Formulário de pré-cadastro público

```yaml
Configuração:
  CPU: 1 vCPU
  RAM: 512MB
  Uptime: 24/7 (link público compartilhável)
  
Volume estimado:
  Page views: 100.000/mês
  Requests: 100.000/mês
  CPU-seconds: ~50.000/mês
  Memory-GB-seconds: ~25.000/mês

Custo mensal: $15-25
Custo médio: $20/mês
```

**Justificativa:** Link público precisa estar sempre disponível para compartilhamento em redes sociais e WhatsApp. Cold starts são aceitáveis para formulário público.

---

### 2. Cloud Run - Backend (.NET API)

**Funcionalidades:**
- Receber dados do formulário
- Validar uploads (formato, tamanho)
- Processar 12.000 uploads/mês
- Integração Google Drive API
- Gerar protocolo de confirmação

```yaml
Configuração:
  CPU: 1 vCPU
  RAM: 1GB
  Min instances: 1 (evitar cold starts em uploads)
  
Volume estimado:
  Uploads: 12.000/mês
  Tempo médio por upload: 2-5s
  CPU-seconds: ~36.000/mês
  API calls: ~27.000/mês
  
Custo mensal: $30-45
Custo médio: $37/mês
```

**Justificativa:** Min instance = 1 garante que uploads sejam processados rapidamente sem espera de cold start. Crítico para boa experiência do usuário.

---

### 3. Cloud SQL PostgreSQL

**Dados armazenados:**
- Informações pessoais (responsável + dependente)
- Metadata de documentos (4 por cadastro)
- Preferências de agendamento
- Protocolos de confirmação
- Audit logs (LGPD)

```yaml
Configuração:
  Tipo: db-custom-1-3840 (1 vCPU, 3.75GB RAM)
  Storage: 50GB SSD
  Uptime: 24/7
  Backups automáticos: habilitado
  
Volume estimado:
  Writes: ~15.000/mês (cadastros + documentos + logs)
  Reads: ~5.000/mês (consultas admin)
  
Schema:
  - beneficiarios: ~3k registros/mês
  - documentos: ~12k registros/mês
  - audit_logs: ~15k registros/mês
  
Custo mensal: $18-25
Custo médio: $20/mês
```

**Justificativa:** Cloud SQL oferece performance adequada para o volume inicial e é mais econômico. Backups automáticos garantem conformidade LGPD com audit trail completo.

---

### 4. Google Drive API (Storage Primário)

**Uso:**
- 12.000 uploads/mês
- Organização em pastas estruturadas
- Metadata vinculado ao PostgreSQL

```yaml
API Calls:
  Uploads: 12.000/mês
  Folder operations: ~1.000/mês
  Metadata reads: ~2.000/mês
  Total: ~15.000 calls/mês

Quota:
  Limite diário: 1 bilhão requests/dia
  Uso estimado: 500 requests/dia
  
Storage:
  Incluído no Google Workspace do cliente
  
Custo mensal: $0 ✅
```

**Justificativa:** Cliente já possui Google Workspace. Armazenamento primário no Drive mantém documentos acessíveis pela equipe sem custo adicional.

---

### 5. Cloud Storage (Backup Automático)

**Uso:** Backup de segurança de todos os uploads

```yaml
Armazenamento:
  Standard class: primeiros 30 dias
  Nearline class: após 30 dias (lifecycle policy)
  
Volume mensal:
  Novos uploads: 36GB/mês
  Após 3 meses: 108GB total
  
Custos (por mês):
  Storage Standard: 36GB × $0.020 = $0.72
  Write operations: 12.000 × $0.005/1000 = $0.06
  Read operations: 500 × $0.004/1000 = $0.002
  
Com Lifecycle (Nearline após 30 dias):
  Mês 1: 36GB Standard = $0.72
  Mês 2: 36GB Standard + 36GB Nearline = $0.72 + $0.36 = $1.08
  Mês 3+: 36GB Standard + 72GB Nearline = $0.72 + $0.72 = $1.44
  
Custo mensal: $0.80-1.50
Custo médio: $1.50/mês
```

**Justificativa:** Backup redundante garante recuperação em caso de problemas com Google Drive. Lifecycle policy otimiza custos automaticamente.

---

### 6. Cloud Monitoring & Logging

**Monitoramento necessário:**
- Logs de upload (sucesso/erro)
- Métricas de performance
- Audit trail (LGPD)
- Alertas de custo

```yaml
Volume:
  Application logs: ~200MB/mês
  Access logs: ~100MB/mês
  Metrics: basic tier
  Alertas: 5 regras
  
Componentes:
  Logs ingestion: 300MB/mês (dentro do free tier: 50GB)
  Metrics: basic (gratuito)
  Alertas: $0.10 cada = $0.50
  
Custo mensal: $5-10
Custo médio: $7/mês
```

**Justificativa:** Monitoramento essencial para detectar problemas rapidamente e garantir auditoria LGPD. Volume dentro do free tier mantém custos baixos.

---

## 📈 Resumo de Custos - Entrega 1

| Componente | Configuração | Custo USD/mês | Custo BRL/mês* |
|-----------|--------------|---------------|----------------|
| **Cloud Run (Frontend)** | 512MB, 1 vCPU, 24/7 | $20 | R$ 112 |
| **Cloud Run (Backend)** | 1GB, 1 vCPU, min-instances: 1 | $37 | R$ 207 |
| **Cloud SQL PostgreSQL** | 1 vCPU, 3.75GB RAM, 50GB | $20 | R$ 112 |
| **Google Drive API** | Workspace cliente | $0 | R$ 0 |
| **Cloud Storage (Backup)** | 36GB/mês + lifecycle | $1.50 | R$ 8 |
| **Monitoring & Logging** | Logs + alertas básicos | $7 | R$ 39 |
| **TOTAL MENSAL** | | **$85.50** | **R$ 479** |

*Taxa de câmbio: USD 1 = BRL 5,60 (outubro/2025)

### Custo Unitário
- **R$ 479 ÷ 3.000 cadastros = R$ 0,16 por cadastro** 💰

---

## 🎯 Cenários de Otimização

### Opção 1: Uptime Reduzido (Horário Comercial)

Se o formulário público for acessado principalmente em horário comercial (220h/mês ao invés de 720h/mês):

| Componente | Economia | Novo Custo USD | Novo Custo BRL |
|-----------|----------|----------------|----------------|
| Cloud Run (Frontend) | -60% | $8 | R$ 45 |
| Cloud Run (Backend) | -50% | $18 | R$ 101 |
| Cloud SQL | -50% | $10 | R$ 56 |
| Outros | 0% | $8.50 | R$ 48 |
| **TOTAL** | **-51%** | **$44.50** | **R$ 249** |

**Custo por cadastro:** R$ 0,08

**⚠️ Trade-offs:**
- Cold starts de 2-3s na primeira requisição
- Indisponível fora do horário comercial
- Impacto na experiência do usuário

**Recomendação:** Não recomendado para Entrega 1. Link público deve estar sempre disponível para compartilhamento.

---

### Opção 2: Instância Menor (db-f1-micro)

Usar instância compartilhada mais econômica:

```yaml
Cloud SQL PostgreSQL:
  Tipo: db-f1-micro
  CPU: 1 vCPU shared
  RAM: 0.6GB
  Storage: 10GB SSD
  
Custo mensal: $8-12
Economia: -$10/mês
```

| Componente | Custo USD | Custo BRL |
|-----------|-----------|-----------|
| Cloud Run (Frontend) 24/7 | $20 | R$ 112 |
| Cloud Run (Backend) min-1 | $37 | R$ 207 |
| **Cloud SQL** (db-f1-micro) | $10 | R$ 56 |
| Google Drive API | $0 | R$ 0 |
| Cloud Storage | $1.50 | R$ 8 |
| Monitoring | $7 | R$ 39 |
| **TOTAL** | **$75.50** | **R$ 423** |

**Custo por cadastro:** R$ 0,14

**⚠️ Trade-offs:**
- CPU compartilhada (performance variável)
- Menos memória (pode impactar queries complexas)
- Armazenamento reduzido

**Recomendação:** Considerar apenas se orçamento for muito limitado. A configuração padrão (1 vCPU dedicado) oferece melhor relação custo-benefício.

---

## 📊 Comparação: Estimativa ADR-002 vs Realidade Entrega 1

| Item | ADR-002 (Geral) | Entrega 1 (Real) | Variação |
|------|-----------------|------------------|----------|
| Frontend | $25-40 | $20 | -25% ✅ |
| Backend | $40-70 | $37 | -7% ✅ |
| Database | $120-180 | $20 (Cloud SQL) | -83% ✅ |
| Storage | $0.90 | $1.50 | +67% ⚠️ |
| Monitoring | $20-30 | $7 | -65% ✅ |
| **TOTAL** | $262 | $85.50 | **-67%** ✅ |

### Análise

**✅ Economias identificadas:**
- Formulário simples = menos recursos de frontend
- Backend focado = sem features complexas desnecessárias
- Monitoramento apenas essencial

**⚠️ Aumento em Storage:**
- ADR-003 foi muito conservador ($0.90)
- Volume real de 36GB/mês requer $1.50
- Ainda assim, extremamente barato (R$ 8/mês)

---

## ⚠️ Alertas e Monitoramento Recomendados

### Alertas de Custo

```yaml
Alertas de Budget:
  crítico:
    threshold: $200/mês
    action: Notificar equipe + investigar urgente
  
  atenção:
    threshold: $150/mês
    action: Revisar configurações
  
  info:
    schedule: semanal
    action: Relatório de custos por componente
```

### Alertas de Performance

```yaml
Alertas de SLA:
  upload_latency:
    threshold: > 10 segundos
    action: Verificar Google Drive API + Cloud Run
  
  error_rate:
    threshold: > 5% de uploads falhados
    action: Investigar logs + notificar dev
  
  database_cpu:
    threshold: > 80% uso
    action: Considerar upgrade ou otimização
  
  storage_quota:
    threshold: > 80% do esperado
    action: Validar não há spam/abuso
```

### Métricas de Negócio

```yaml
KPIs a monitorar:
  - Cadastros completados/dia
  - Taxa de abandono do formulário
  - Tempo médio de preenchimento
  - Documentos enviados com sucesso vs falhas
  - Dispositivos mais usados (mobile/desktop)
  - Horários de pico de acesso
```

---

## 📋 Checklist de Controle de Custos

### Antes do Deploy
- [ ] Configurar alertas de billing ($150 e $200)
- [ ] Definir budget mensal no GCP
- [ ] Revisar quotas do Google Drive API
- [ ] Configurar lifecycle policies no Cloud Storage
- [ ] Validar que free tiers estão sendo usados
- [ ] Documentar custos esperados por componente

### Primeiras 2 Semanas (Período Crítico)
- [ ] Monitorar custos **diários**
- [ ] Validar volume real de uploads vs estimado
- [ ] Verificar se há cold starts impactando UX
- [ ] Ajustar min-instances se necessário
- [ ] Revisar logs de erros (podem aumentar custos)
- [ ] Validar que lifecycle do Storage está funcionando

### Mensal (Rotina)
- [ ] Revisar dashboard de custos GCP
- [ ] Analisar picos de uso e sua causa
- [ ] Otimizar queries lentas do DB
- [ ] Limpar dados temporários/desnecessários
- [ ] Revisar se configurações ainda são adequadas
- [ ] Gerar relatório de custo/cadastro

### Trimestral (Otimização)
- [ ] Comparar custos reais vs estimados
- [ ] Avaliar upgrade de instância Cloud SQL (se necessário)
- [ ] Revisar política de retenção de backups
- [ ] Considerar reserved instances se volume for estável
- [ ] Validar se componentes estão dimensionados corretamente

---

## 💡 Dicas de Otimização de Custos

### 1. Cloud Run
```
✅ Usar min-instances apenas no backend (uploads críticos)
✅ Frontend pode ter min-instances: 0 (cold start aceitável)
✅ Configurar max-instances para evitar surpresas
✅ Ajustar CPU/RAM baseado em uso real (não estimado)
```

### 2. Database
```
✅ Usar Cloud SQL com instância adequada ao volume
✅ Configurar connection pooling
✅ Criar índices apenas necessários
✅ Monitorar performance de queries
✅ Ajustar tamanho da instância conforme necessidade
✅ Configurar backups automáticos
```

### 3. Storage
```
✅ Lifecycle policy automática (Standard → Nearline → Coldline)
✅ Comprimir uploads antes de armazenar
✅ Definir política de retenção (ex: 7 anos documentos, 2 anos logs)
✅ Deletar backups muito antigos
```

### 4. Monitoring
```
✅ Usar free tier ao máximo (50GB logs/mês)
✅ Configurar sampling de logs (não logar tudo)
✅ Alertas apenas no essencial (evitar custo de notificações)
✅ Usar Cloud Logging com retenção curta (30 dias)
```

---

## 🎯 Recomendação Final

### Para Início do Projeto (Entrega 1)

**Configuração Recomendada: "Cloud SQL Standard"**

```yaml
Investimento mensal: R$ 479 (~$85.50)

Componentes:
  - Cloud Run Frontend (24/7): R$ 112
  - Cloud Run Backend (min-1): R$ 207
  - Cloud SQL PostgreSQL: R$ 112
  - Cloud Storage (backup): R$ 8
  - Monitoring: R$ 39

```

**Justificativa:**
1. ✅ Custo acessível (~R$ 500/mês)
2. ✅ Performance adequada para 3k cadastros/mês
3. ✅ Disponibilidade 24/7 (link público)
4. ✅ Escalável conforme crescimento
5. ✅ ROI excelente (economia de R$ 24k/mês vs manual)

### Path de Evolução de Custos

```
Fase 1 (Entrega 1): R$ 479/mês
  └── 3.000 cadastros/mês
  └── Cloud SQL (1 vCPU, 3.75GB RAM)

Fase 2 (Crescimento): R$ 650/mês
  └── 5.000-8.000 cadastros/mês
  └── Upgrade Cloud SQL (2 vCPU, 7.5GB RAM)

Fase 3 (Escala): R$ 850/mês
  └── 10.000+ cadastros/mês
  └── Cloud SQL otimizado + Read replicas
  └── Features avançadas (Entrega 2 e 3)
```

---

## 📞 Contato para Dúvidas

**Questões sobre custos ou otimizações:**
- Documentação GCP: https://cloud.google.com/pricing
- Calculadora de custos: https://cloud.google.com/products/calculator
- Suporte CodeBoa Software: [contato]

---

**Última atualização:** Outubro 2025  
**Responsável:** CodeBoa Software  
**Revisão:** Trimestral ou quando volume crescer 50%
