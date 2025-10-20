# Requisitos para Entrega 1 - 10 de Novembro 2025

**Data da Entrega:** 10/11/2025  
**Projeto:** Casa Mãe Paulistana  
**Responsável:** CodeBoa Software

---

## 📋 Escopo da Entrega

### 1. Formulário Público de Cadastro em Formato de Chat

**Descrição:** Formulário público (link compartilhável) para pré-cadastro de beneficiários com validações e bloqueio automático.

#### 1.1 Dados a Coletar
- Informações pessoais do responsável
- Informações do dependente
- Preferência de agendamento para triagem
- Dependente frequenta atividades externas? Se sim, em quais períodos? (Informação necessária para priorização do atendimento na Triagem)

#### 1.2 Documentos Obrigatórios (Upload)
- ✅ Comprovante de residência
- ✅ Laudo médico
- ✅ RG do Responsável
- ✅ RG ou Certidão de Nascimento do Dependente

#### 1.3 Pré-Agendamento de Triagem
- Sistema de seleção de preferência de dia/hora
- Usuário escolhe preferência (não é agendamento definitivo)
- Sistema deve permitir flexibilidade para equipe ajustar depois

#### 1.4 Funcionalidades Automáticas do Formulário
- **Geração de Número de Protocolo:** Número não-sequencial único gerado automaticamente ao completar o cadastro
- **Envio Automático de Email:** Email de confirmação enviado automaticamente com o número de protocolo
- **Bloqueio Automático:** O formulário deve bloquear automaticamente quando:
  - Atingir número parametrizável de cadastros aguardando aprovação, OU
  - Atingir número parametrizável de triagens agendadas
- **Armazenamento do Protocolo:** Número de protocolo gravado no banco junto com o cadastro

---

### 2. Sistema Interno de Revisão e Aprovação

**Descrição:** Sistema administrativo para equipe interna revisar documentos e aprovar/reprovar cadastros.

#### 2.1 Tela de Revisão de Documentos
- Visualização de cadastros pendentes de aprovação
- Visualização de todos os documentos enviados
- Dados do cadastro completos para análise
- Opções: **Aprovar** ou **Reprovar**

#### 2.2 Processo de Aprovação
- **Ao Aprovar:**
  - Excluir documentos do armazenamento
  - Enviar email de notificação ao cadastrado
  - Mover cadastro para lista de "Aprovados Aguardando Triagem"
  
- **Ao Reprovar:**
  - Excluir documentos do armazenamento
  - Campo obrigatório para descrição do motivo da rejeição
  - Enviar email de notificação ao cadastrado com o motivo da rejeição
  - Registrar rejeição no histórico

#### 2.3 Gestão de Armazenamento
- **Objetivo:** Manter armazenamento baixo excluindo documentos após decisão
- Documentos mantidos apenas enquanto aguardam aprovação
- Após aprovação ou rejeição, documentos são excluídos do storage

---

### 3. Sistema de Agendamento de Triagem

**Descrição:** Sistema para gerenciar aprovados e agendar triagens considerando preferências.

#### 3.1 Tela: Aprovados Aguardando Triagem
- Lista de todos os cadastros aprovados sem agendamento confirmado
- Informações relevantes de cada cadastrado
- Preferências de agendamento indicadas no cadastro
- Botão para acessar tela de agendamento

#### 3.2 Tela: Agendamento de Triagem
- **Busca Inteligente:** Sistema busca preferências de agendamento do cadastro
- **Sugestões de Horários:** Mostra horários disponíveis dentro das preferências
- **Período de Busca:** Horários disponíveis nas próximas X semanas (parametrizável)
- **Confirmação:** Ao confirmar agendamento, atualiza contadores para bloqueio do formulário público

---

## ✅ Checklist de Implementação

### 1. Formulário Público
- [ ] Criar formulário público com link compartilhável
- [ ] Campos de dados pessoais (responsável)
- [ ] Campos de dados pessoais (dependente)
- [ ] Sistema de upload de documentos (4 documentos obrigatórios)
- [ ] Validação de formatos de arquivo aceitos
- [ ] Validação de tamanho máximo de arquivo
- [ ] Seletor de preferência de dia/hora para triagem
- [ ] **Geração automática de número de protocolo não-sequencial**
- [ ] **Gravação do protocolo no banco de dados junto com cadastro**
- [ ] **Envio automático de email com número de protocolo**
- [ ] **Sistema de bloqueio parametrizável:**
  - [ ] Parâmetro: limite de cadastros aguardando aprovação
  - [ ] Parâmetro: limite de triagens agendadas
  - [ ] Lógica de bloqueio quando atingir qualquer um dos limites
  - [ ] Mensagem clara quando formulário estiver bloqueado

### 2. Sistema Interno - Revisão e Aprovação
- [ ] **Tela de revisão de documentos pendentes**
  - [ ] Listagem de cadastros aguardando aprovação
  - [ ] Visualizador de documentos enviados
  - [ ] Exibição completa dos dados do cadastro
- [ ] **Botão: Aprovar Cadastro**
  - [ ] Excluir documentos do storage
  - [ ] Enviar email de aprovação ao cadastrado
  - [ ] Mover para lista de "Aprovados Aguardando Triagem"
  - [ ] Atualizar contadores de bloqueio
- [ ] **Botão: Reprovar Cadastro**
  - [ ] Campo obrigatório para motivo da rejeição
  - [ ] Excluir documentos do storage
  - [ ] Enviar email com notificação e motivo da rejeição
  - [ ] Registrar no histórico
  - [ ] Atualizar contadores de bloqueio

### 3. Sistema de Agendamento de Triagem
- [ ] **Tela: Aprovados Aguardando Triagem**
  - [ ] Lista de cadastros aprovados sem triagem agendada
  - [ ] Exibir preferências de agendamento de cada cadastrado
  - [ ] Botão para acessar agendamento
- [ ] **Tela: Agendamento de Triagem**
  - [ ] Buscar preferências de agendamento do cadastro selecionado
  - [ ] Parâmetro: número de semanas para busca (X semanas)
  - [ ] Exibir horários disponíveis dentro das preferências
  - [ ] Confirmar agendamento
  - [ ] Atualizar contador de triagens agendadas
  - [ ] Enviar email de confirmação do agendamento

### 4. Backend
- [ ] API para receber dados do formulário público
- [ ] **Gerador de protocolo não-sequencial (UUID ou similar)**
- [ ] Armazenamento seguro de documentos (temporário)
- [ ] **Sistema de contadores parametrizáveis**
- [ ] **API para aprovação/rejeição de cadastros**
- [ ] **Lógica de exclusão de documentos após decisão**
- [ ] API para gestão de triagens
- [ ] **Sistema de envio de emails automáticos:**
  - [ ] Email de confirmação de cadastro (com protocolo)
  - [ ] Email de aprovação
  - [ ] Email de rejeição (com motivo)
  - [ ] Email de confirmação de agendamento de triagem

### 5. Painel Administrativo
- [ ] Autenticação e autorização
- [ ] Dashboard com métricas:
  - [ ] Cadastros aguardando aprovação
  - [ ] Triagens agendadas
  - [ ] Status dos bloqueios
- [ ] Navegação entre telas do sistema interno
- [ ] Configuração de parâmetros do sistema

### 6. UX/UI
- [ ] Interface responsiva (mobile-first) - Formulário público
- [ ] Interfaces compatíveis com leitores de tela
- [ ] Interfaces com alto contraste para pessoas com deficiência visual
- [ ] Feedback de upload de documentos
- [ ] Confirmação de envio com número de protocolo
- [ ] Mensagem quando formulário estiver bloqueado
- [ ] Interface administrativa intuitiva
- [ ] Preview de documentos na tela de revisão
- [ ] Confirmações antes de ações irreversíveis

### 7. Segurança
- [ ] Armazenamento seguro de documentos (criptografia)
- [ ] Conformidade LGPD
- [ ] Link público sem exposição de dados sensíveis
- [ ] Proteção contra spam/abuso no formulário público
- [ ] Autenticação segura para sistema interno
- [ ] Logs de auditoria (aprovações, rejeições, exclusões)
- [ ] **Exclusão segura de documentos (não apenas marcar como excluído)**

### 8. Testes
- [ ] ⚠️ **IMPORTANTE:** Testar upload de documentos em dispositivos diferentes
  - [ ] Android (celular e tablet)
  - [ ] iOS (iPhone e iPad)
  - [ ] Desktop (Windows, Mac, Linux)
  - [ ] Diferentes navegadores (Chrome, Safari, Firefox, Edge)
- [ ] Validar upload de PDFs
- [ ] Validar upload de imagens (JPG, PNG)
- [ ] Validar captura direta da câmera (mobile)
- [ ] **Testar geração de protocolo (garantir não-sequencial e único)**
- [ ] **Testar envio automático de emails**
- [ ] **Testar lógica de bloqueio do formulário**
- [ ] **Testar processo completo de aprovação**
- [ ] **Testar processo completo de rejeição**
- [ ] **Testar exclusão de documentos**
- [ ] **Testar agendamento de triagens**
- [ ] Testar em diferentes tamanhos de tela
- [ ] Validar limites de tamanho de arquivo
- [ ] Testar conexões lentas/instáveis

---

## 📝 Notas

### Considerações Técnicas

**Número de Protocolo Não-Sequencial:**
- Utilizar UUID v4 ou algoritmo similar
- Garantir unicidade no banco de dados
- Formato legível e fácil de comunicar por telefone/WhatsApp
- Exemplo: `CMP-2025-A7K9-P3M8` ou similar

**Upload de Documentos:**
- Formatos aceitos: PDF, JPG, PNG
- Tamanho máximo sugerido: 5MB por arquivo
- Total: 4 arquivos obrigatórios
- **⚠️ CRÍTICO:** Interface deve funcionar bem em dispositivos móveis
  - Permitir seleção de arquivos da galeria
  - Permitir captura direta da câmera
  - Preview do arquivo antes do envio
  - Indicador de progresso durante upload
  - Mensagem clara de sucesso/erro
- **Armazenamento Temporário:** Documentos mantidos apenas até aprovação/rejeição
- **Exclusão Automática:** Após decisão, documentos devem ser permanentemente excluídos

**Sistema de Bloqueio Parametrizável:**
- Dois parâmetros configuráveis via painel admin:
  1. Limite de cadastros aguardando aprovação (ex: 50)
  2. Limite de triagens agendadas (ex: 30)
- Bloqueio ativado ao atingir QUALQUER um dos limites
- Mensagem clara ao usuário: "No momento não estamos aceitando novos cadastros. Por favor, tente novamente em breve."
- Desbloqueio automático quando números caírem abaixo do limite

**Sistema de Emails Automáticos:**
- **Email 1 - Confirmação de Cadastro:**
  - Enviado imediatamente após submissão
  - Contém número de protocolo
  - Informa próximos passos (aguardar análise)
  
- **Email 2 - Aprovação:**
  - Notifica aprovação do cadastro
  - Informa que entrará em contato para agendamento
  
- **Email 3 - Rejeição:**
  - Notifica rejeição
  - Inclui motivo detalhado da rejeição
  - Instruções sobre como proceder (se aplicável)
  
- **Email 4 - Confirmação de Triagem:**
  - Enviado após agendamento confirmado
  - Data, hora e local da triagem
  - Instruções sobre o que levar

**Agendamento de Triagem:**
- Busca preferências indicadas no cadastro inicial
- Parâmetro: X semanas para frente (configurável, sugestão: 4 semanas)
- Interface deve mostrar apenas horários que atendem as preferências
- Flexibilidade para equipe forçar horário fora da preferência se necessário
- Ao confirmar, incrementa contador de "triagens agendadas"

**Gestão de Armazenamento:**
- Objetivo: Manter custos baixos de storage
- Fluxo:
  1. Upload → Armazenamento temporário (S3, Azure Blob, etc)
  2. Aprovação/Rejeição → Exclusão permanente dos arquivos
  3. Apenas metadados mantidos no banco (nome do arquivo, data upload, etc)
- Considerar política de exclusão automática após X dias sem decisão

---

### Perguntas/Decisões Pendentes

**Formulário Público:**
- [ ] Qual formato exato do número de protocolo? (sugestão: `CMP-YYYY-XXXX-XXXX`)
- [ ] Valores iniciais dos parâmetros de bloqueio?
- [ ] Interface conversacional (chat)

**Emails:**
- [ ] Templates de email definidos?
- [ ] Remetente/domínio de email configurado?
- [ ] Logo e identidade visual para emails?

**Sistema Interno:**
- [ ] Quem terá acesso ao sistema de aprovação?
- [ ] Precisa de diferentes níveis de permissão?
- [ ] Histórico de aprovações/rejeições deve ser auditável?

**Agendamento:**
- [ ] Quantas semanas à frente buscar horários? (padrão: 4)
- [ ] Horários de funcionamento da triagem?
- [ ] Duração padrão de cada triagem?
- [ ] Sistema de calendário já existe ou criar do zero?

**Armazenamento:**
- [ ] Qual serviço de storage usar? (Google Cloud Storage)
- [ ] Política de backup dos documentos temporários?
- [ ] Período de retenção antes de exclusão forçada?

---

## 🎯 Funcionalidades Principais

### Fluxo Completo do Sistema

```
1. CADASTRO PÚBLICO
   ↓
   ├─ Formulário preenchido
   ├─ Documentos enviados
   ├─ Protocolo gerado (não-sequencial)
   ├─ Email automático enviado
   └─ Status: "Aguardando Aprovação"

2. REVISÃO INTERNA
   ↓
   ├─ Equipe visualiza documentos
   ├─ Decisão: Aprovar ou Reprovar
   │
   ├─ SE APROVAR:
   │  ├─ Documentos excluídos
   │  ├─ Email de aprovação enviado
   │  └─ Status: "Aprovado - Aguardando Triagem"
   │
   └─ SE REPROVAR:
      ├─ Motivo obrigatório
      ├─ Documentos excluídos
      ├─ Email com motivo enviado
      └─ Status: "Reprovado"

3. AGENDAMENTO DE TRIAGEM
   ↓
   ├─ Equipe acessa "Aprovados Aguardando Triagem"
   ├─ Seleciona cadastrado
   ├─ Sistema mostra preferências + horários disponíveis
   ├─ Confirma agendamento
   ├─ Email de confirmação enviado
   └─ Status: "Triagem Agendada"

4. BLOQUEIO AUTOMÁTICO
   ↓
   └─ Formulário bloqueia se:
      ├─ Muitos "Aguardando Aprovação" OU
      └─ Muitas "Triagens Agendadas"
```

---

## 🔗 Referências

- [Estimativa de Horas](./estimativa-horas-entrega-1.md)
- [Precificação](./precificacao-projeto.md)
- LGPD - Lei Geral de Proteção de Dados

