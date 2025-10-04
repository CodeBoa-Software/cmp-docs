# Análise Detalhada de Custos - Casa Mãe Paulistana

**Data:** 04/10/2025  
**Volume Esperado:** 3000 acessos/mês  
**Projeto:** Casa Mãe Paulistana  

---

## 📊 **Premissas de Cálculo**

### Volume de Dados
- **Acessos mensais:** 3.000 cadastros
- **Documentos por cadastro:** 4 obrigatórios (RG responsável, RG dependente, comprovante residência, laudo médico)
- **Total uploads/mês:** 12.000 arquivos
- **Limite por arquivo:** 10MB (otimizado para PDFs multipáginas e fotos)
- **Tamanho médio estimado:** 3MB por arquivo
- **Volume mensal:** ~36GB de novos documentos
- **Volume anual acumulado:** ~432GB

### Justificativa para Limite de 10MB
- **PDFs de documentos:** Laudos médicos podem ter múltiplas páginas (3-8MB típico)
- **Fotos de documentos:** RG fotografado em alta resolução (2-5MB)
- **Comprovantes:** Faturas digitalizadas podem ser extensas (1-4MB)
- **Margem de segurança:** 10MB acomoda casos extremos sem frustar usuários

---

## 💰 **Estimativa de Custos Mensais (USD)**

### Google Cloud Run - Frontend (React)
```
Cálculo base:
• ~100.000 page views/mês (3k usuários × ~33 pages/session)
• 2 vCPU, 2GB RAM por instância
• Tempo médio por request: 200ms

Custo estimado: $25-40/mês
```

### Google Cloud Run - Backend (.NET API)
```
Cálculo base:
• 12.000 uploads + 36.000 API calls (read/write)
• 2 vCPU, 4GB RAM por instância  
• Processamento de upload: 2-5s por arquivo
• Validações e database operations

Custo estimado: $40-70/mês
```

### AlloyDB PostgreSQL
```
Configuração recomendada:
• 2 vCPUs, 8GB RAM
• 100GB storage SSD
• ~3.000 transações complexas/mês
• Backup automático (7 dias)

Custo estimado: $120-180/mês
```

### Google Cloud Storage (Backup)
```
Cálculo mensal:
• Storage Standard: 36GB × $0.020 = $0.72
• Write operations: 12.000 × $0.005/1000 = $0.06
• Read operations (backup): 1.000 × $0.004/1000 = $0.004
• Egress occasional: 1GB × $0.12 = $0.12

Custo estimado: $0.90/mês

Com lifecycle (Nearline após 90 dias):
• Storage mix: 24GB Standard + 12GB Nearline
• Custo otimizado: $0.60/mês
```

### Google Drive API
```
Uso dentro das quotas gratuitas:
• 18.000 API calls/mês vs 1 bilhão/dia limit
• Storage incluído no Google Workspace existente

Custo: $0/mês
```

### Cloud Monitoring e Logging
```
• Application metrics e custom dashboards
• Audit logs para conformidade LGPD  
• Alertas proativos
• ~500MB logs/mês

Custo estimado: $20-30/mês
```

---

## 📈 **Resumo de Custos**

| Cenário | Frontend | Backend | AlloyDB | Storage | Monitoring | **Total USD** | **Total BRL** |
|---------|----------|---------|---------|---------|------------|---------------|---------------|
| **Padrão** | $32 | $55 | $150 | $0.90 | $25 | **$262.90** | **~R$ 1.470** |
| **Otimizado** | $32 | $55 | $150 | $0.60 | $25 | **$262.60** | **~R$ 1.468** |
| **Conservador** | $40 | $70 | $180 | $1.20 | $30 | **$321.20** | **~R$ 1.795** |

### **Custo por Cadastro Realizado**
- **Cenário Padrão:** R$ 1.470 ÷ 3.000 = **R$ 0,49 por cadastro**
- **Cenário Otimizado:** R$ 1.468 ÷ 3.000 = **R$ 0,49 por cadastro**  
- **Cenário Conservador:** R$ 1.795 ÷ 3.000 = **R$ 0,60 por cadastro**

---

## 🔄 **Estratégias de Otimização de Custos**

### 1. **Compressão Inteligente de Arquivos**
```csharp
// Exemplo de implementação
public async Task<byte[]> OptimizeFile(IFormFile file)
{
    if (file.ContentType.StartsWith("image/"))
    {
        // Compressão com qualidade 85% mantendo legibilidade
        return await CompressImage(file, quality: 85);
    }
    
    if (file.ContentType == "application/pdf")
    {
        // Otimização de PDF (remover metadata, comprimir imagens internas)
        return await OptimizePdf(file);
    }
    
    return await file.GetBytes();
}
```

**Economia esperada:** 30-40% no volume de storage

### 2. **Lifecycle Policies Automáticas**
```yaml
# Cloud Storage Lifecycle
rules:
  - condition:
      age: 90
    action:
      type: SetStorageClass
      storageClass: NEARLINE  # $0.010/GB (50% economia)
  
  - condition:  
      age: 365
    action:
      type: SetStorageClass  
      storageClass: COLDLINE  # $0.004/GB (80% economia)
```

**Economia esperada:** 40-60% nos custos de storage após 1 ano

### 3. **Cache Inteligente**
```csharp
// Cache metadata no Redis/MemoryCache
[ResponseCache(Duration = 3600)] // 1 hora
public async Task<DocumentoMetadata> GetDocumentoMetadata(string fileId)
{
    return await _cache.GetOrSetAsync($"doc_{fileId}", 
        () => _documentoService.GetMetadata(fileId));
}
```

**Economia esperada:** 20-30% nas chamadas de API

---

## 📊 **Comparação com Alternativas**

| Solução | Custo Mensal | Prós | Contras |
|---------|--------------|------|---------|
| **Nossa Proposta** | **R$ 1.470** | Integração Drive, LGPD completa, escalável | Setup inicial complexo |
| **AWS S3 + EC2** | R$ 2.200-3.500 | Ecossistema maduro | Mais caro, sem integração Drive |
| **Azure Blob + VM** | R$ 1.800-2.800 | Integração .NET | Sem Google Workspace |
| **Dropbox Business** | R$ 1.200 + dev | Simples | Limitações API, sem customização |
| **Servidor Dedicado** | R$ 800-1.200 | Controle total | Manutenção, backup manual, sem SLA |

---

## 🎯 **Projeções de Crescimento**

### Cenário: Dobrar para 6.000 cadastros/mês

| Componente | Custo Atual | Custo 6k/mês | Diferença |
|------------|-------------|---------------|-----------|
| **Cloud Run (Frontend)** | $32 | $50 | +$18 |
| **Cloud Run (Backend)** | $55 | $95 | +$40 |
| **AlloyDB** | $150 | $220 | +$70 |
| **Storage** | $0.90 | $1.80 | +$0.90 |
| **Monitoring** | $25 | $35 | +$10 |
| **TOTAL** | **$262.90** | **$401.80** | **+$138.90** |

**Custo por cadastro:** R$ 1.795 ÷ 6.000 = **R$ 0,30 por cadastro** (economia de escala)

---

## ⚠️ **Alertas de Monitoramento Recomendados**

### Custos
- 🚨 **Crítico:** Gastos > R$ 2.000/mês
- ⚠️ **Atenção:** Gastos > R$ 1.800/mês  
- 📊 **Info:** Relatório semanal de custos

### Performance  
- 🚨 **Crítico:** Latência upload > 10s
- ⚠️ **Atenção:** Taxa erro > 5%
- 📊 **Info:** Dashboard tempo real

### Volume
- 🚨 **Crítico:** Storage > 100GB/mês  
- ⚠️ **Atenção:** Uploads > 15k/mês
- 📊 **Info:** Tendência de crescimento

---

## ✅ **Recomendações Finais**

### Implementação Faseada
1. **MVP (Mês 1-2):** Implementar versão básica com custos mínimos
2. **Otimização (Mês 3-4):** Adicionar compressão e lifecycle policies  
3. **Monitoramento (Mês 5+):** Refinamento baseado em dados reais

### Contingência Orçamentária
- **Orçamento base:** R$ 1.500/mês
- **Margem de segurança:** +20% = R$ 1.800/mês
- **Cenário pessimista:** R$ 2.000/mês (ainda viável)

### ROI Estimado
- **Custo de processar cadastro manualmente:** ~R$ 15-25 por pessoa
- **Custo automatizado:** R$ 0,49 por cadastro
- **ROI:** 3000 × (R$ 20 - R$ 0,49) = **R$ 58.530/mês de economia**
- **Payback:** Infrastructure costs pagam-se em 1 dia de operação

**A solução proposta é altamente viável economicamente! 🎯**