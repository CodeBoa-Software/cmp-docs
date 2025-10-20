# Requisitos para Fase 4 - Data a Definir

**Data da Entrega:** A definir  
**Projeto:** Casa Mãe Paulistana  
**Responsável:** CodeBoa Software

---

## 📋 Escopo da Entrega

A Fase 4 implementa **integração completa com WhatsApp** para substituir as comunicações via email por mensagens via WhatsApp em todo o fluxo do sistema, desde o cadastro inicial até agendamentos de atendimentos e oficinas.

**Importante:** Esta fase **NÃO** inclui:
- Chatbot com inteligência artificial
- WhatsApp Business API Premium com múltiplos atendentes simultâneos
- Integração com CRM externo
- Sistema de atendimento ao cliente via chat
- Documentação técnica detalhada

### Pré-requisitos
- Fase 1 concluída (Cadastro e Aprovação)
- Fase 2 concluída (Triagem, Atendimentos e Oficinas)
- Fase 3 concluída (Sistema de Agendamentos)
- Conta WhatsApp Business API configurada
- Número de telefone verificado

---

## 📊 Resumo Executivo

### Objetivo
Substituir todas as notificações via email por mensagens via WhatsApp, tornando a comunicação mais direta, acessível e eficiente com os responsáveis cadastrados no sistema.

### Módulos da Fase 4

| Módulo | Descrição | Principais Funcionalidades |
|--------|-----------|---------------------------|
| **Cadastro via WhatsApp** | Substituir confirmações de cadastro por WhatsApp | • Confirmação de cadastro recebido<br>• Notificação de aprovação/rejeição<br>• Envio do número de protocolo |
| **Triagem via WhatsApp** | Notificações de agendamento de triagem | • Confirmação de agendamento<br>• Lembrete 24h antes<br>• Instruções sobre a triagem |
| **Atendimentos via WhatsApp** | Notificações de agendamentos especializados | • Confirmação de agendamento<br>• Lembrete de atendimento<br>• Notificação de reagendamento<br>• Notificação de cancelamento |
| **Oficinas via WhatsApp** | Comunicações sobre oficinas | • Confirmação de inscrição<br>• Lembretes de encontros<br>• Avisos de cancelamento<br>• Resumo de frequência |
| **Sistema de Templates** | Gestão de mensagens padronizadas | • Cadastro de templates<br>• Variáveis dinâmicas<br>• Versionamento<br>• Aprovação Meta |
| **Log e Monitoramento** | Controle de envios e falhas | • Log de mensagens enviadas<br>• Status de entrega<br>• Tratamento de erros<br>• Dashboard de monitoramento |

### Estimativa de Complexidade

**Integrações:** 2 principais
- WhatsApp Business API (Meta)
- Sistema interno de notificações

**Templates de Mensagem:** ~20 templates
- Cadastro: 3 templates
- Triagem: 3 templates
- Atendimentos: 4 templates
- Oficinas: 4 templates
- Genéricas: 6 templates

**Funcionalidades Especiais:**
- Sistema de fila de mensagens
- Retry automático em caso de falha
- Validação de número de telefone
- Rate limiting (respeitar limites da API)
- Tratamento de opt-out
- Log completo de comunicações
- Dashboard de monitoramento

---

## 1. Módulo de Integração Técnica

**Descrição:** Configuração e integração técnica com a API do WhatsApp Business.

### 1.1 Configuração da API

**Objetivo:** Estabelecer conexão com WhatsApp Business API.

**Requisitos Técnicos:**
- Conta Meta Business
- WhatsApp Business API configurada
- Número de telefone verificado
- Tokens de acesso configurados
- Webhooks configurados

**Funcionalidades:**
- Autenticação com Meta API
- Envio de mensagens de template
- Recebimento de status de entrega
- Tratamento de webhooks
- Renovação automática de tokens

### 1.2 Sistema de Fila de Mensagens

**Objetivo:** Gerenciar envio de mensagens de forma confiável e escalável.

**Funcionalidades:**
- Fila de mensagens a enviar
- Priorização (urgente, normal, baixa)
- Processamento assíncrono
- Retry automático em caso de falha
- Rate limiting (respeitar limites da API)
- Log de tentativas de envio

**Regras de Retry:**
- 1ª tentativa: imediata
- 2ª tentativa: após 5 minutos
- 3ª tentativa: após 30 minutos
- 4ª tentativa: após 2 horas
- Após 4 tentativas: marcar como falha e notificar administrador

### 1.3 Validação de Números de Telefone

**Objetivo:** Garantir que números cadastrados são válidos para WhatsApp.

**Funcionalidades:**
- Validação de formato (DDD + número)
- Normalização de números (+55 XX XXXXX-XXXX)
- Verificação se número está no WhatsApp
- Detecção de números inválidos
- Sugestão de correção
- Bloqueio de envio para números inválidos

**Tratamento:**
- Se número inválido: notificar equipe interna
- Permitir correção manual do número
- Registrar tentativas de envio falhadas

### 1.4 Tratamento de Opt-Out

**Objetivo:** Respeitar usuários que não desejam receber mensagens.

**Funcionalidades:**
- Detectar quando usuário solicita parar mensagens
- Marcar responsável como "opt-out" no sistema
- Bloquear envios futuros automaticamente
- Permitir opt-in novamente (via equipe)
- Log de opt-outs
- Dashboard de usuários opt-out

---

## 2. Módulo de Cadastro via WhatsApp

**Descrição:** Substituir emails de cadastro por mensagens via WhatsApp.

### 2.1 Confirmação de Cadastro Recebido

**Objetivo:** Notificar responsável que cadastro foi recebido com sucesso.

**Quando Enviar:**
- Imediatamente após submissão do formulário público (Fase 1)

**Conteúdo da Mensagem:**
```
🏠 *Casa Mãe Paulistana*

Olá, [Nome do Responsável]!

✅ Seu cadastro foi recebido com sucesso!

📋 *Número do Protocolo:* [PROTOCOLO]

Sua solicitação está em análise pela nossa equipe. 
Em breve você receberá uma resposta sobre a aprovação.

⏱️ Prazo estimado: até 5 dias úteis

Se tiver dúvidas, entre em contato pelo telefone: (XX) XXXX-XXXX

Obrigado!
```

**Variáveis Dinâmicas:**
- `[Nome do Responsável]`
- `[PROTOCOLO]`

### 2.2 Notificação de Aprovação

**Objetivo:** Informar aprovação do cadastro e próximos passos.

**Quando Enviar:**
- Quando equipe aprovar cadastro (Fase 1)

**Conteúdo da Mensagem:**
```
🏠 *Casa Mãe Paulistana*

Olá, [Nome do Responsável]!

🎉 Seu cadastro foi APROVADO!

📋 *Protocolo:* [PROTOCOLO]

Em breve entraremos em contato para agendar sua triagem presencial.

Mantenha seu telefone por perto para não perder nossos contatos!

Até breve! 😊
```

**Variáveis Dinâmicas:**
- `[Nome do Responsável]`
- `[PROTOCOLO]`

### 2.3 Notificação de Rejeição

**Objetivo:** Informar rejeição do cadastro com motivo claro.

**Quando Enviar:**
- Quando equipe reprovar cadastro (Fase 1)

**Conteúdo da Mensagem:**
```
🏠 *Casa Mãe Paulistana*

Olá, [Nome do Responsável],

Informamos que seu cadastro não foi aprovado.

📋 *Protocolo:* [PROTOCOLO]

*Motivo:* [MOTIVO_REJEICAO]

Se tiver dúvidas ou quiser esclarecimentos, entre em contato:
📞 (XX) XXXX-XXXX

Atenciosamente,
Equipe Casa Mãe Paulistana
```

**Variáveis Dinâmicas:**
- `[Nome do Responsável]`
- `[PROTOCOLO]`
- `[MOTIVO_REJEICAO]`

---

## 3. Módulo de Triagem via WhatsApp

**Descrição:** Notificações relacionadas ao agendamento de triagem presencial.

### 3.1 Confirmação de Agendamento de Triagem

**Objetivo:** Confirmar data e horário da triagem presencial.

**Quando Enviar:**
- Quando equipe agendar triagem (Fase 3)

**Conteúdo da Mensagem:**
```
🏠 *Casa Mãe Paulistana*

Olá, [Nome do Responsável]!

✅ Sua *Triagem* foi agendada!

📅 *Data:* [DATA]
🕒 *Horário:* [HORARIO]
📍 *Local:* [ENDERECO]

*O que levar:*
• RG ou CNH
• Comprovante de residência original
• Laudo médico do dependente (se tiver)

⚠️ Importante: Chegar com 15 minutos de antecedência.

Até lá! 😊

_Para reagendar, ligue: (XX) XXXX-XXXX_
```

**Variáveis Dinâmicas:**
- `[Nome do Responsável]`
- `[DATA]`
- `[HORARIO]`
- `[ENDERECO]`

### 3.2 Lembrete de Triagem (24h antes)

**Objetivo:** Lembrar responsável sobre triagem no dia anterior.

**Quando Enviar:**
- 24 horas antes do horário agendado

**Conteúdo da Mensagem:**
```
🏠 *Casa Mãe Paulistana*

Olá, [Nome do Responsável]!

🔔 Lembrete: Sua *Triagem* é AMANHÃ!

📅 *Data:* [DATA]
🕒 *Horário:* [HORARIO]
📍 *Local:* [ENDERECO]

*Não esqueça de levar:*
✓ RG ou CNH
✓ Comprovante de residência original
✓ Laudo médico (se tiver)

⏰ Chegue com 15 minutos de antecedência!

Aguardamos você! 😊

_Caso não possa comparecer, ligue: (XX) XXXX-XXXX_
```

**Variáveis Dinâmicas:**
- `[Nome do Responsável]`
- `[DATA]`
- `[HORARIO]`
- `[ENDERECO]`

### 3.3 Reagendamento de Triagem

**Objetivo:** Notificar sobre mudança de data/horário da triagem.

**Quando Enviar:**
- Quando equipe reagendar triagem (Fase 3)

**Conteúdo da Mensagem:**
```
🏠 *Casa Mãe Paulistana*

Olá, [Nome do Responsável],

⚠️ Sua triagem foi *REAGENDADA*.

*Nova data e horário:*
📅 *Data:* [NOVA_DATA]
🕒 *Horário:* [NOVO_HORARIO]
📍 *Local:* [ENDERECO]

_Data anterior: [DATA_ANTERIOR] às [HORARIO_ANTERIOR]_

Desculpe pelo transtorno!

Até lá! 😊
```

**Variáveis Dinâmicas:**
- `[Nome do Responsável]`
- `[NOVA_DATA]`
- `[NOVO_HORARIO]`
- `[ENDERECO]`
- `[DATA_ANTERIOR]`
- `[HORARIO_ANTERIOR]`

---

## 4. Módulo de Atendimentos via WhatsApp

**Descrição:** Notificações sobre atendimentos especializados (advogado, psicólogo, assistente social).

### 4.1 Confirmação de Agendamento de Atendimento

**Objetivo:** Confirmar atendimento especializado agendado.

**Quando Enviar:**
- Quando equipe agendar atendimento (Fase 3)

**Conteúdo da Mensagem:**
```
🏠 *Casa Mãe Paulistana*

Olá, [Nome do Responsável]!

✅ Seu atendimento foi agendado!

👤 *Profissional:* [NOME_PROFISSIONAL]
🩺 *Especialidade:* [ESPECIALIDADE]

📅 *Data:* [DATA]
🕒 *Horário:* [HORARIO]
📍 *Local:* [ENDERECO]

⏰ Chegue com 10 minutos de antecedência.

Até breve! 😊

_Para reagendar, ligue: (XX) XXXX-XXXX_
```

**Variáveis Dinâmicas:**
- `[Nome do Responsável]`
- `[NOME_PROFISSIONAL]`
- `[ESPECIALIDADE]` (Advogado, Psicólogo, Assistente Social)
- `[DATA]`
- `[HORARIO]`
- `[ENDERECO]`

### 4.2 Lembrete de Atendimento (24h antes)

**Objetivo:** Lembrar responsável sobre atendimento no dia anterior.

**Quando Enviar:**
- 24 horas antes do horário agendado

**Conteúdo da Mensagem:**
```
🏠 *Casa Mãe Paulistana*

Olá, [Nome do Responsável]!

🔔 Lembrete: Seu atendimento é AMANHÃ!

👤 *Profissional:* [NOME_PROFISSIONAL]
🩺 *Especialidade:* [ESPECIALIDADE]

📅 *Data:* [DATA]
🕒 *Horário:* [HORARIO]
📍 *Local:* [ENDERECO]

⏰ Chegue com 10 minutos de antecedência!

Aguardamos você! 😊

_Caso não possa comparecer, ligue: (XX) XXXX-XXXX_
```

**Variáveis Dinâmicas:**
- `[Nome do Responsável]`
- `[NOME_PROFISSIONAL]`
- `[ESPECIALIDADE]`
- `[DATA]`
- `[HORARIO]`
- `[ENDERECO]`

### 4.3 Reagendamento de Atendimento

**Objetivo:** Notificar sobre mudança de data/horário do atendimento.

**Quando Enviar:**
- Quando equipe reagendar atendimento (Fase 3)

**Conteúdo da Mensagem:**
```
🏠 *Casa Mãe Paulistana*

Olá, [Nome do Responsável],

⚠️ Seu atendimento foi *REAGENDADO*.

👤 *Profissional:* [NOME_PROFISSIONAL]

*Nova data e horário:*
📅 *Data:* [NOVA_DATA]
🕒 *Horário:* [NOVO_HORARIO]
📍 *Local:* [ENDERECO]

_Data anterior: [DATA_ANTERIOR] às [HORARIO_ANTERIOR]_

Desculpe pelo transtorno!

Até breve! 😊
```

**Variáveis Dinâmicas:**
- `[Nome do Responsável]`
- `[NOME_PROFISSIONAL]`
- `[NOVA_DATA]`
- `[NOVO_HORARIO]`
- `[ENDERECO]`
- `[DATA_ANTERIOR]`
- `[HORARIO_ANTERIOR]`

### 4.4 Cancelamento de Atendimento

**Objetivo:** Informar cancelamento e orientar sobre próximos passos.

**Quando Enviar:**
- Quando equipe cancelar atendimento (Fase 3)

**Conteúdo da Mensagem:**
```
🏠 *Casa Mãe Paulistana*

Olá, [Nome do Responsável],

⚠️ Seu atendimento foi *CANCELADO*.

👤 *Profissional:* [NOME_PROFISSIONAL]
📅 *Data:* [DATA_CANCELADA]
🕒 *Horário:* [HORARIO_CANCELADO]

*Motivo:* [MOTIVO_CANCELAMENTO]

📞 Em breve entraremos em contato para reagendar.

Desculpe pelo transtorno!

Dúvidas: (XX) XXXX-XXXX
```

**Variáveis Dinâmicas:**
- `[Nome do Responsável]`
- `[NOME_PROFISSIONAL]`
- `[DATA_CANCELADA]`
- `[HORARIO_CANCELADO]`
- `[MOTIVO_CANCELAMENTO]`

---

## 5. Módulo de Oficinas via WhatsApp

**Descrição:** Notificações sobre inscrições e participação em oficinas.

### 5.1 Confirmação de Inscrição em Oficina

**Objetivo:** Confirmar inscrição em oficina e fornecer informações.

**Quando Enviar:**
- Quando equipe inscrever responsável em oficina (Fase 2)

**Conteúdo da Mensagem:**
```
🏠 *Casa Mãe Paulistana*

Olá, [Nome do Responsável]!

🎉 Você foi inscrito(a) na oficina:

📚 *Oficina:* [NOME_OFICINA]

📅 *Início:* [DATA_INICIO]
🕒 *Horário:* [HORARIO_OFICINA]
📍 *Local:* [LOCAL_OFICINA]

*Próximos encontros:*
[LISTA_PROXIMOS_ENCONTROS]

⚠️ Importante: Presença mínima de 75% para certificado.

Aguardamos você! 😊

_Dúvidas: (XX) XXXX-XXXX_
```

**Variáveis Dinâmicas:**
- `[Nome do Responsável]`
- `[NOME_OFICINA]`
- `[DATA_INICIO]`
- `[HORARIO_OFICINA]`
- `[LOCAL_OFICINA]`
- `[LISTA_PROXIMOS_ENCONTROS]`

### 5.2 Lembrete de Encontro de Oficina (24h antes)

**Objetivo:** Lembrar responsável sobre próximo encontro da oficina.

**Quando Enviar:**
- 24 horas antes de cada encontro da oficina

**Conteúdo da Mensagem:**
```
🏠 *Casa Mãe Paulistana*

Olá, [Nome do Responsável]!

🔔 Lembrete: Você tem oficina AMANHÃ!

📚 *Oficina:* [NOME_OFICINA]
📅 *Data:* [DATA_ENCONTRO]
🕒 *Horário:* [HORARIO]
📍 *Local:* [LOCAL]

⏰ Não se atrase!

Aguardamos você! 😊

_Caso não possa comparecer, ligue: (XX) XXXX-XXXX_
```

**Variáveis Dinâmicas:**
- `[Nome do Responsável]`
- `[NOME_OFICINA]`
- `[DATA_ENCONTRO]`
- `[HORARIO]`
- `[LOCAL]`

### 5.3 Cancelamento de Encontro de Oficina

**Objetivo:** Informar sobre cancelamento de encontro.

**Quando Enviar:**
- Quando equipe cancelar um encontro da oficina

**Conteúdo da Mensagem:**
```
🏠 *Casa Mãe Paulistana*

Olá, [Nome do Responsável],

⚠️ O encontro da oficina foi *CANCELADO*.

📚 *Oficina:* [NOME_OFICINA]
📅 *Data cancelada:* [DATA_CANCELADA]

*Motivo:* [MOTIVO_CANCELAMENTO]

*Próximo encontro:*
📅 *Data:* [PROXIMA_DATA]
🕒 *Horário:* [HORARIO]

Desculpe pelo transtorno!

Até o próximo encontro! 😊
```

**Variáveis Dinâmicas:**
- `[Nome do Responsável]`
- `[NOME_OFICINA]`
- `[DATA_CANCELADA]`
- `[MOTIVO_CANCELAMENTO]`
- `[PROXIMA_DATA]`
- `[HORARIO]`

### 5.4 Resumo de Frequência na Oficina

**Objetivo:** Informar status de frequência periodicamente.

**Quando Enviar:**
- A cada 4 encontros ou mensalmente (configurável)

**Conteúdo da Mensagem:**
```
🏠 *Casa Mãe Paulistana*

Olá, [Nome do Responsável]!

📊 *Resumo de Frequência*

📚 *Oficina:* [NOME_OFICINA]

*Sua frequência até agora:*
✅ Presenças: [NUM_PRESENCAS]
❌ Faltas: [NUM_FALTAS]
📈 Percentual: [PERCENTUAL]%

⚠️ *Lembre-se:* É necessário 75% de presença para certificado.

Continue participando! 💪😊

_Dúvidas: (XX) XXXX-XXXX_
```

**Variáveis Dinâmicas:**
- `[Nome do Responsável]`
- `[NOME_OFICINA]`
- `[NUM_PRESENCAS]`
- `[NUM_FALTAS]`
- `[PERCENTUAL]`

---

## 6. Sistema de Templates

**Descrição:** Gestão de templates de mensagens no sistema.

### 6.1 Cadastro de Templates

**Objetivo:** Permitir criação e edição de templates de mensagens.

**Funcionalidades:**
- Criar novo template
- Editar template existente
- Versionar templates
- Definir variáveis dinâmicas
- Preview de mensagem
- Aprovar template para uso

**Dados do Template:**
- Nome do template
- Categoria (cadastro, triagem, atendimento, oficina, genérica)
- Texto da mensagem
- Variáveis dinâmicas
- Status (rascunho, aprovado, arquivado)
- Data de criação
- Versão

### 6.2 Variáveis Dinâmicas

**Objetivo:** Definir e gerenciar variáveis que serão substituídas dinamicamente.

**Variáveis Globais:**
- `[Nome do Responsável]`
- `[PROTOCOLO]`
- `[DATA]`
- `[HORARIO]`
- `[ENDERECO]`
- `[TELEFONE_CONTATO]`

**Variáveis por Contexto:**

**Atendimentos:**
- `[NOME_PROFISSIONAL]`
- `[ESPECIALIDADE]`
- `[SALA]`

**Oficinas:**
- `[NOME_OFICINA]`
- `[DATA_INICIO]`
- `[LOCAL_OFICINA]`
- `[NUM_PRESENCAS]`
- `[NUM_FALTAS]`
- `[PERCENTUAL]`

**Funcionalidades:**
- Validação de variáveis ao salvar template
- Sugestão de variáveis disponíveis
- Teste de substituição

### 6.3 Aprovação Meta (WhatsApp Business API)

**Objetivo:** Gerenciar processo de aprovação de templates pela Meta.

**Fluxo:**
1. Template criado no sistema
2. Enviado para aprovação Meta
3. Aguardar resposta (pode levar até 24h)
4. Atualizar status no sistema (aprovado/rejeitado)
5. Se rejeitado: exibir motivo e permitir edição

**Status Possíveis:**
- Rascunho (não enviado)
- Aguardando Aprovação Meta
- Aprovado
- Rejeitado
- Arquivado

**Funcionalidades:**
- Enviar template para Meta
- Verificar status de aprovação
- Reenviar após correção
- Histórico de tentativas

---

## 7. Sistema de Log e Monitoramento

**Descrição:** Controle e rastreamento de todas as mensagens enviadas.

### 7.1 Log de Mensagens

**Objetivo:** Registrar todas as mensagens enviadas pelo sistema.

**Dados do Log:**
- ID da mensagem
- Template utilizado
- Destinatário (nome e telefone)
- Data e hora de envio
- Status de entrega (enviado, entregue, lido, falhou)
- Tentativas de envio
- Erro (se houver)
- Contexto (cadastro, triagem, atendimento, oficina)
- ID do registro relacionado (cadastro, agendamento, etc.)

**Funcionalidades:**
- Visualizar histórico de mensagens por responsável
- Filtrar por status, data, tipo
- Buscar por telefone ou nome
- Exportar logs (Excel/CSV)
- Reenviar mensagem manualmente

### 7.2 Dashboard de Monitoramento

**Objetivo:** Fornecer visão geral do sistema de mensagens.

**Métricas Exibidas:**
- Total de mensagens enviadas (hoje, semana, mês)
- Taxa de entrega
- Taxa de leitura
- Mensagens com falha
- Mensagens em fila
- Tempo médio de entrega
- Distribuição por tipo de mensagem

**Visualizações:**
- Gráfico de mensagens ao longo do tempo
- Gráfico de status de entrega
- Gráfico de falhas por motivo
- Lista de mensagens recentes
- Alertas de falhas críticas

**Funcionalidades:**
- Atualização em tempo real
- Filtros por período
- Drill-down em métricas
- Exportar relatórios

### 7.3 Tratamento de Erros

**Objetivo:** Identificar e resolver problemas de envio.

**Tipos de Erro:**
- Número inválido
- Número não está no WhatsApp
- Usuário bloqueou o número
- Limite de API atingido
- Erro de rede/servidor
- Template não aprovado
- Outros erros da API

**Ações Automáticas:**
- Retry conforme regras definidas
- Notificar administrador após X falhas
- Marcar número como inválido
- Pausar envios se limite de API atingido

**Funcionalidades:**
- Dashboard de erros
- Filtrar erros por tipo
- Ações manuais (reenviar, corrigir número)
- Histórico de resolução

### 7.4 Configurações de Envio

**Objetivo:** Permitir ajustes no comportamento do sistema de mensagens.

**Configurações:**
- Horário permitido para envio (ex: 8h às 20h)
- Intervalo mínimo entre mensagens para mesmo destinatário
- Número máximo de tentativas de reenvio
- Tempo entre tentativas de reenvio
- Ativar/desativar envio de tipos específicos
- Números de telefone bloqueados (opt-out)

**Funcionalidades:**
- Painel de configurações
- Validação de valores
- Histórico de alterações
- Restaurar configurações padrão

---

## ✅ Checklist de Implementação

### 1. Integração Técnica

- [ ] **Configuração da API**
  - [ ] Criar conta Meta Business
  - [ ] Configurar WhatsApp Business API
  - [ ] Verificar número de telefone
  - [ ] Configurar tokens de acesso
  - [ ] Implementar autenticação
  - [ ] Configurar webhooks

- [ ] **Sistema de Fila**
  - [ ] Criar fila de mensagens
  - [ ] Processamento assíncrono
  - [ ] Sistema de priorização
  - [ ] Retry automático
  - [ ] Rate limiting

- [ ] **Validação de Números**
  - [ ] Validar formato de telefone
  - [ ] Normalizar números (+55)
  - [ ] Verificar se está no WhatsApp
  - [ ] Tratamento de números inválidos

- [ ] **Tratamento de Opt-Out**
  - [ ] Detectar opt-out
  - [ ] Marcar no sistema
  - [ ] Bloquear envios futuros
  - [ ] Permitir opt-in manual

### 2. Cadastro via WhatsApp

- [ ] **Template: Confirmação de Cadastro**
  - [ ] Criar template
  - [ ] Aprovar na Meta
  - [ ] Integrar com Fase 1
  - [ ] Testar envio

- [ ] **Template: Aprovação de Cadastro**
  - [ ] Criar template
  - [ ] Aprovar na Meta
  - [ ] Integrar com Fase 1
  - [ ] Testar envio

- [ ] **Template: Rejeição de Cadastro**
  - [ ] Criar template
  - [ ] Aprovar na Meta
  - [ ] Integrar com Fase 1
  - [ ] Testar envio

### 3. Triagem via WhatsApp

- [ ] **Template: Confirmação de Triagem**
  - [ ] Criar template
  - [ ] Aprovar na Meta
  - [ ] Integrar com Fase 3
  - [ ] Testar envio

- [ ] **Template: Lembrete de Triagem**
  - [ ] Criar template
  - [ ] Configurar agendador (24h antes)
  - [ ] Integrar com Fase 3
  - [ ] Testar envio

- [ ] **Template: Reagendamento de Triagem**
  - [ ] Criar template
  - [ ] Aprovar na Meta
  - [ ] Integrar com Fase 3
  - [ ] Testar envio

### 4. Atendimentos via WhatsApp

- [ ] **Template: Confirmação de Atendimento**
  - [ ] Criar template
  - [ ] Aprovar na Meta
  - [ ] Integrar com Fase 3
  - [ ] Testar envio

- [ ] **Template: Lembrete de Atendimento**
  - [ ] Criar template
  - [ ] Configurar agendador (24h antes)
  - [ ] Integrar com Fase 3
  - [ ] Testar envio

- [ ] **Template: Reagendamento de Atendimento**
  - [ ] Criar template
  - [ ] Aprovar na Meta
  - [ ] Integrar com Fase 3
  - [ ] Testar envio

- [ ] **Template: Cancelamento de Atendimento**
  - [ ] Criar template
  - [ ] Aprovar na Meta
  - [ ] Integrar com Fase 3
  - [ ] Testar envio

### 5. Oficinas via WhatsApp

- [ ] **Template: Confirmação de Inscrição**
  - [ ] Criar template
  - [ ] Aprovar na Meta
  - [ ] Integrar com Fase 2
  - [ ] Testar envio

- [ ] **Template: Lembrete de Encontro**
  - [ ] Criar template
  - [ ] Configurar agendador (24h antes)
  - [ ] Integrar com Fase 2
  - [ ] Testar envio

- [ ] **Template: Cancelamento de Encontro**
  - [ ] Criar template
  - [ ] Aprovar na Meta
  - [ ] Integrar com Fase 2
  - [ ] Testar envio

- [ ] **Template: Resumo de Frequência**
  - [ ] Criar template
  - [ ] Configurar periodicidade
  - [ ] Integrar com Fase 2
  - [ ] Testar envio

### 6. Sistema de Templates

- [ ] **Gestão de Templates**
  - [ ] CRUD de templates
  - [ ] Sistema de variáveis dinâmicas
  - [ ] Versionamento
  - [ ] Preview de mensagem
  - [ ] Validações

- [ ] **Integração com Meta**
  - [ ] Enviar template para aprovação
  - [ ] Verificar status de aprovação
  - [ ] Tratar rejeições
  - [ ] Histórico de tentativas

### 7. Log e Monitoramento

- [ ] **Log de Mensagens**
  - [ ] Registrar todos os envios
  - [ ] Armazenar status de entrega
  - [ ] Histórico por responsável
  - [ ] Filtros e buscas
  - [ ] Exportações

- [ ] **Dashboard**
  - [ ] Métricas principais
  - [ ] Gráficos de visualização
  - [ ] Atualização em tempo real
  - [ ] Alertas de falhas
  - [ ] Exportar relatórios

- [ ] **Tratamento de Erros**
  - [ ] Identificar tipos de erro
  - [ ] Ações automáticas
  - [ ] Dashboard de erros
  - [ ] Resolução manual

- [ ] **Configurações**
  - [ ] Painel de configurações
  - [ ] Horários permitidos
  - [ ] Regras de retry
  - [ ] Opt-out management

### 8. Funcionalidades Transversais

- [ ] **Integração com Fases Anteriores**
  - [ ] Substituir envios de email por WhatsApp
  - [ ] Manter compatibilidade com fluxo existente
  - [ ] Migração gradual

- [ ] **Testes**
  - [ ] Testes unitários
  - [ ] Testes de integração com API
  - [ ] Testes de templates
  - [ ] Testes de retry
  - [ ] Testes de rate limiting

- [ ] **Documentação**
  - [ ] Documentar templates
  - [ ] Documentar variáveis
  - [ ] Documentar processo de aprovação Meta
  - [ ] Guia de troubleshooting

- [ ] **Segurança e Privacidade**
  - [ ] Conformidade LGPD
  - [ ] Criptografia de dados
  - [ ] Controle de acesso aos logs
  - [ ] Retenção de dados configurável

---

## 🔄 Fluxos Principais do Sistema

### Fluxo 1: Cadastro Completo com WhatsApp

```
1. CADASTRO PÚBLICO (Fase 1)
   ├─ Responsável preenche formulário
   ├─ Envia documentos
   └─ Sistema gera protocolo
   ↓
2. CONFIRMAÇÃO AUTOMÁTICA VIA WHATSAPP
   ├─ Mensagem enviada imediatamente
   ├─ Inclui número de protocolo
   └─ Status: "Aguardando Aprovação"
   ↓
3. REVISÃO PELA EQUIPE
   ├─ Equipe analisa documentos
   └─ Decisão: Aprovar ou Reprovar
   ↓
4A. SE APROVAR:
   ├─ WhatsApp: Notificação de aprovação
   └─ Status: "Aprovado - Aguardando Triagem"
   ↓
4B. SE REPROVAR:
   ├─ WhatsApp: Notificação de rejeição + motivo
   └─ Status: "Reprovado"
```

### Fluxo 2: Agendamento de Triagem com Lembretes

```
1. TRIAGEM AGENDADA (Fase 3)
   ├─ Equipe agenda triagem
   └─ Sistema confirma horário
   ↓
2. CONFIRMAÇÃO IMEDIATA VIA WHATSAPP
   ├─ Mensagem com data, hora e local
   ├─ Instruções sobre o que levar
   └─ Status entrega: "Enviado"
   ↓
3. AGENDADOR AUTOMÁTICO
   ├─ Sistema monitora agendamentos
   └─ 24h antes do horário marcado
   ↓
4. LEMBRETE AUTOMÁTICO VIA WHATSAPP
   ├─ Mensagem de lembrete enviada
   ├─ Reforça instruções
   └─ Status entrega: "Enviado"
   ↓
5. TRIAGEM REALIZADA
   └─ Profissional registra conclusão (Fase 2)
```

### Fluxo 3: Atendimento com Notificações

```
1. ATENDIMENTO AGENDADO (Fase 3)
   ├─ Equipe agenda com profissional
   └─ Sistema valida disponibilidade
   ↓
2. CONFIRMAÇÃO VIA WHATSAPP
   ├─ Mensagem com profissional, data, hora
   └─ Status: "Agendado"
   ↓
3. LEMBRETE AUTOMÁTICO (24h antes)
   ├─ Sistema envia lembrete
   └─ Responsável recebe notificação
   ↓
4. SE REAGENDADO:
   ├─ Sistema detecta mudança
   ├─ WhatsApp: Nova data e hora
   └─ Compara com horário anterior
   ↓
5. SE CANCELADO:
   ├─ WhatsApp: Notificação de cancelamento
   ├─ Inclui motivo
   └─ Orienta sobre próximos passos
```

### Fluxo 4: Oficina com Acompanhamento

```
1. INSCRIÇÃO EM OFICINA (Fase 2)
   ├─ Responsável inscrito pela equipe
   └─ Oficina tem múltiplos encontros
   ↓
2. CONFIRMAÇÃO VIA WHATSAPP
   ├─ Detalhes da oficina
   ├─ Lista de próximos encontros
   └─ Requisito de 75% de presença
   ↓
3. LEMBRETES AUTOMÁTICOS
   ├─ 24h antes de CADA encontro
   ├─ Sistema envia lembrete
   └─ Responsável notificado
   ↓
4. REGISTRO DE PRESENÇA (Fase 2)
   ├─ Equipe marca presença após cada encontro
   └─ Sistema atualiza estatísticas
   ↓
5. RESUMO PERIÓDICO
   ├─ A cada 4 encontros (configurável)
   ├─ WhatsApp: Resumo de frequência
   └─ Mostra presenças, faltas e percentual
   ↓
6. SE ENCONTRO CANCELADO:
   ├─ WhatsApp: Notificação de cancelamento
   └─ Informa próximo encontro
```

### Fluxo 5: Tratamento de Falhas de Envio

```
1. MENSAGEM NA FILA
   ├─ Sistema tenta enviar mensagem
   └─ Chamada à API do WhatsApp
   ↓
2. FALHA NO ENVIO
   ├─ Erro retornado pela API
   ├─ Ex: Número inválido, limite atingido, etc
   └─ Status: "Falha"
   ↓
3. SISTEMA DE RETRY
   ├─ 1ª tentativa: imediata
   ├─ 2ª tentativa: após 5 minutos
   ├─ 3ª tentativa: após 30 minutos
   └─ 4ª tentativa: após 2 horas
   ↓
4. SE AINDA FALHAR
   ├─ Marcar como "Falha Definitiva"
   ├─ Registrar erro no log
   └─ Notificar administrador
   ↓
5. AÇÃO MANUAL
   ├─ Admin visualiza erro no dashboard
   ├─ Identifica problema (ex: número errado)
   ├─ Corrige número no cadastro
   └─ Reenvia mensagem manualmente
```

### Fluxo 6: Aprovação de Template

```
1. CRIAÇÃO DE NOVO TEMPLATE
   ├─ Admin cria template no sistema
   ├─ Define texto e variáveis
   └─ Status: "Rascunho"
   ↓
2. ENVIO PARA APROVAÇÃO META
   ├─ Admin clica "Enviar para Aprovação"
   ├─ Sistema envia para WhatsApp Business API
   └─ Status: "Aguardando Aprovação Meta"
   ↓
3. VERIFICAÇÃO PERIÓDICA
   ├─ Sistema verifica status periodicamente
   └─ Meta pode levar até 24h para responder
   ↓
4A. SE APROVADO:
   ├─ Status: "Aprovado"
   └─ Template pronto para uso
   ↓
4B. SE REJEITADO:
   ├─ Status: "Rejeitado"
   ├─ Sistema exibe motivo da rejeição
   ├─ Admin edita template
   └─ Reenvia para aprovação
```

---

## 📝 Notas Importantes

### Considerações Técnicas

**WhatsApp Business API:**
- Requer conta Meta Business verificada
- Processo de aprovação pode levar dias
- Templates devem ser pré-aprovados pela Meta
- Limitações de envio (rate limits)
- Custos por mensagem enviada
- Não permite mensagens promocionais sem consentimento

**Restrições da API:**
- Mensagens apenas com templates aprovados (primeiras 24h)
- Após 24h da última mensagem do usuário, apenas templates
- Não pode enviar mensagens de marketing sem opt-in
- Rate limits variam por nível de conta (tier)
- Monitoramento de qualidade pela Meta

**Armazenamento de Logs:**
- Manter logs por período configurável (sugestão: 6 meses)
- Após período, arquivar ou excluir conforme LGPD
- Criptografar logs que contenham dados sensíveis
- Considerar volume de logs para dimensionar storage

**Performance:**
- Sistema de fila deve processar assíncrono
- Não bloquear interface ao enviar mensagens
- Otimizar consultas de disponibilidade de templates
- Cache de templates aprovados
- Monitorar uso da API para evitar limites

### Regras de Negócio

**Horários de Envio:**
- Apenas entre 8h e 20h (configurável)
- Evitar domingos e feriados (exceto urgências)
- Respeitar fuso horário local

**Tipos de Mensagem:**
- **Transacionais:** Confirmações, lembretes (prioridade alta)
- **Informativas:** Resumos, atualizações (prioridade média)
- **Promocionais:** Avisos de eventos (prioridade baixa)

**Privacidade:**
- Não compartilhar número de telefone com terceiros
- Permitir opt-out a qualquer momento
- Informar usuário sobre uso do número no cadastro
- Conformidade com LGPD

**Templates:**
- Usar linguagem clara e acessível
- Emojis para melhor comunicação (com moderação)
- Identificação clara (Casa Mãe Paulistana no início)
- Informações de contato para dúvidas
- CTA (Call to Action) claro quando aplicável

### Custos

**WhatsApp Business API:**
- Cobrança por mensagem enviada
- Valores variam por país e tipo de mensagem
- Mensagens de template: custo fixo
- Mensagens de resposta (dentro de 24h): grátis ou menor custo
- Considerar volume mensal para orçamento

**Infraestrutura:**
- Servidor para processar fila de mensagens
- Storage para logs
- Banco de dados para controle
- Monitoramento e alertas

### Perguntas/Decisões Pendentes

- [ ] Qual provedor de WhatsApp Business API usar? (Twilio, MessageBird, oficial Meta?)
- [ ] Qual número de telefone será usado?
- [ ] Orçamento mensal para envio de mensagens?
- [ ] Permitir respostas dos usuários ou apenas envio?
- [ ] Implementar chatbot básico para respostas automáticas?
- [ ] Integrar com CRM ou sistema de atendimento?
- [ ] Período de retenção de logs?
- [ ] Processo de opt-in explícito ou implícito no cadastro?

---

## 🎯 Resumo de Funcionalidades

### Funcionalidades Principais

**1. Integração Técnica**
- Configuração WhatsApp Business API
- Sistema de fila de mensagens
- Validação de números
- Tratamento de opt-out
- Retry automático

**2. Cadastro via WhatsApp**
- Confirmação de cadastro recebido (com protocolo)
- Notificação de aprovação
- Notificação de rejeição (com motivo)

**3. Triagem via WhatsApp**
- Confirmação de agendamento
- Lembrete 24h antes
- Notificação de reagendamento

**4. Atendimentos via WhatsApp**
- Confirmação de agendamento
- Lembrete 24h antes
- Notificação de reagendamento
- Notificação de cancelamento

**5. Oficinas via WhatsApp**
- Confirmação de inscrição
- Lembrete antes de cada encontro
- Notificação de cancelamento
- Resumo periódico de frequência

**6. Sistema de Templates**
- Cadastro e gestão de templates
- Variáveis dinâmicas
- Versionamento
- Aprovação Meta
- Preview de mensagens

**7. Log e Monitoramento**
- Registro de todas as mensagens
- Dashboard de métricas
- Tratamento de erros
- Configurações de envio
- Exportações e relatórios

---

## 🔗 Referências

- [Requisitos Fase 1 - Cadastro e Aprovação](../fase-1/fase-1-cadastro-e-aprovacao.md)
- [Requisitos Fase 2 - Triagem, Atendimentos e Oficinas](../fase-2/fase-2-triagem-atendimentos-oficinas.md)
- [Requisitos Fase 3 - Sistema de Agendamentos](../fase-3/fase-3-sistema-agendamentos.md)
- [Estimativa de Horas Fase 4](./estimativa-horas-fase-4.md)
- [Precificação Fase 4](./precificacao-fase-4.md)
- [README Principal do Projeto](../../README.md)
- [WhatsApp Business API Documentation](https://developers.facebook.com/docs/whatsapp)
- [WhatsApp Business Platform](https://business.whatsapp.com/)

---

*Documento sujeito a alterações conforme validação com stakeholders e equipe de desenvolvimento.*
