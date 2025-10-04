# Requisitos para Entrega 2

**Data da Entrega:** A definir  
**Projeto:** Casa Mãe Paulistana  
**Responsável:** CodeBoa Software

---

## 📋 Escopo da Entrega

### 1. Liberação para Triagem

**Descrição:** Sistema para equipe administrativa liberar/aprovar pré-cadastros para triagem.

#### 1.1 Funcionalidades
- Painel administrativo para visualizar pré-cadastros
- Revisão de documentos enviados
- Aprovação/Rejeição de pré-cadastros
- Notificação ao beneficiário sobre status

---

### 2. Formulário de Triagem

**Descrição:** Formulário para equipe realizar triagem dos beneficiários aprovados.

#### 2.1 Funcionalidades
- Formulário interno para equipe
- Campos específicos de avaliação/triagem
- Registro de informações coletadas na triagem
- Histórico de triagens realizadas

---

### 3. Análise de Documentos via WhatsApp

**Descrição:** Sistema de comunicação via WhatsApp para análise e solicitação de documentos complementares.

#### 3.1 Funcionalidades
- Integração com WhatsApp Business API
- Envio de solicitações de documentos
- Recebimento de documentos via WhatsApp
- Análise e validação de documentos
- Comunicação bidirecional com beneficiário
- Histórico de conversas/documentos trocados

#### 3.2 Fluxo Sugerido
```
Sistema → WhatsApp: "Olá [Nome], recebemos seu pré-cadastro. 
                     Precisamos que você envie o documento X."

Usuário → WhatsApp: [Envia foto/PDF do documento]

Sistema → WhatsApp: "Documento recebido! Nossa equipe vai analisar."

Equipe analisa documento internamente

Sistema → WhatsApp: "Documento aprovado!" ou 
                     "Precisamos de uma foto melhor, por favor."
```

---

### 4. MVP de Dados dos Atendimentos (Google Forms + Sheets)

**Descrição:** Solução temporária usando Google Forms e Google Sheets para registro de atendimentos dos profissionais.

#### 4.1 Estrutura
- **Google Forms:** Formulário para profissionais preencherem após cada atendimento
- **Google Sheets:** Planilha centralizada com todos os registros
- Campos básicos de atendimento (data, profissional, beneficiário, tipo, observações)

#### 4.2 Funcionalidades Mínimas
- Formulário simples e rápido de preencher
- Registro de atendimentos realizados
- Consulta básica de histórico
- Possibilidade de gerar relatórios simples

#### 4.3 Considerações
- Solução provisória até desenvolvimento de sistema próprio
- Fácil migração de dados posterior
- Baixo custo de implementação
- Rapidez para colocar em produção

---

## ✅ Checklist de Implementação

### Liberação para Triagem
- [ ] Painel administrativo (dashboard)
- [ ] Listagem de pré-cadastros pendentes
- [ ] Visualização de documentos enviados
- [ ] Botões de aprovar/rejeitar
- [ ] Sistema de notificação (email/WhatsApp)
- [ ] Registro de auditoria (quem aprovou/rejeitou)
- [ ] Filtros e busca

### Formulário de Triagem
- [ ] Definir campos necessários para triagem
- [ ] Criar formulário (web ou mobile)
- [ ] Validações de campos
- [ ] Salvamento de dados
- [ ] Integração com cadastro do beneficiário
- [ ] Impressão/exportação de ficha de triagem

### Análise de Documentos via WhatsApp
- [ ] Configurar WhatsApp Business API
- [ ] Criar fluxo de conversação
- [ ] Sistema de recebimento de mídia (fotos/PDFs)
- [ ] Armazenamento de documentos recebidos
- [ ] Vinculação de documentos ao cadastro
- [ ] Interface para equipe analisar documentos
- [ ] Templates de mensagens padronizadas
- [ ] Histórico de conversas

### MVP Google Forms + Sheets
- [ ] Criar Google Form para atendimentos
- [ ] Configurar Google Sheet vinculada
- [ ] Definir campos do formulário
- [ ] Criar dropdowns para seleção (profissional, tipo atendimento, etc)
- [ ] Configurar validações básicas
- [ ] Criar dashboards/relatórios básicos no Sheets
- [ ] Treinar equipe no uso
- [ ] Documentar processo de migração futura

### Integrações
- [ ] Integrar painel admin com sistema de pré-cadastro
- [ ] Integrar WhatsApp com armazenamento de documentos
- [ ] Sincronização de status entre sistemas

---

## 📝 Notas

### Considerações Técnicas

**WhatsApp Business API:**
- Provedor a definir (Twilio, MessageBird, Meta)
- Webhook para receber mensagens
- Storage para mídias recebidas
- Sistema de filas para processamento

**Google Forms + Sheets:**
- Conta Google Workspace ou gratuita?
- Permissões de acesso (quem pode preencher/visualizar)
- Backup de dados
- Plano de migração para sistema definitivo

**Painel Administrativo:**
- Autenticação e controle de acesso
- Diferentes níveis de permissão
- Logs de auditoria

### Perguntas/Decisões Pendentes

- [ ] Quais campos específicos para formulário de triagem?
- [ ] Critérios de aprovação/rejeição de pré-cadastros?
- [ ] Tipos de documentos que podem ser solicitados via WhatsApp?
- [ ] Quem da equipe terá acesso ao painel administrativo?
- [ ] Estrutura exata do formulário de atendimentos (Google Forms)?
- [ ] Quando migrar do Google Sheets para sistema próprio?
- [ ] Notificações: apenas WhatsApp ou também email/SMS?

### Dependências

- ✅ Entrega 1 concluída (pré-cadastro funcionando)
- Definição de stack tecnológica
- Contratação de provedor WhatsApp API
- Conta Google configurada

### Riscos

- Complexidade da integração WhatsApp
- Limitações do Google Forms para uso profissional
- Volume de dados crescente no Google Sheets
- Migração futura dos dados do Sheets

---

## 🔄 Evolução Futura

**Google Forms → Sistema Próprio:**
- Quando volume aumentar
- Quando precisar de funcionalidades avançadas
- Integração com prontuário eletrônico
- Relatórios e analytics mais robustos

---

## 🔗 Referências

- [Entrega 1 - Requisitos](./entrega-1-22-outubro.md)
- [Ideias e Discussões](../docs/ideias-discussoes.md) - Estratégia WhatsApp
- [WhatsApp Business API Docs](https://developers.facebook.com/docs/whatsapp)
- [Google Forms API](https://developers.google.com/forms)
