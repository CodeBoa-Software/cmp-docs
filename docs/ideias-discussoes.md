# Ideias e Discussões - Casa Mãe Paulistana

> **Nota:** Este documento contém ideias e discussões em andamento. 
> Decisões formalizadas serão movidas para ADRs apropriados posteriormente.

**Última atualização:** 2025-01-04

---

## 💬 Envio e Armazenamento de Documentos

### Ideia Principal
Utilizar WhatsApp como canal principal para envio de documentos aos usuários/beneficiários.

### Detalhes
- **Canal Primário:** WhatsApp Business API
  - Alta penetração no público brasileiro
  - Familiaridade dos usuários
  - Boa taxa de visualização e entrega
  
- **Fallback (quando WhatsApp não disponível):**
  - Armazenar documentos temporariamente em storage seguro
  - Notificar por canal alternativo (SMS, email, notificação)
  - Permitir download via link autenticado com expiração
  - Definir política de retenção (ex: 30 dias)

### Questões Abertas
- [ ] Qual provedor de WhatsApp API? (Twilio, MessageBird, Meta oficial?)
- [ ] Onde armazenar temporariamente? (AWS S3, Azure, Google Cloud?)
- [ ] Quanto tempo manter documentos não entregues?
- [ ] Criptografia necessária?
- [ ] Conformidade LGPD - validar com jurídico

---

## 💬 Interface de Cadastro Conversacional

### Ideia Principal
Fazer o sistema de cadastro em formato de chat, ao invés de formulário tradicional. Por trás funcionar exatamente como um formulário.

### Detalhes
- **UX/UI:**
  - Interface de chat (similar a WhatsApp/Messenger)
  - Uma pergunta por vez
  - Progressão natural e guiada
  - Menos intimidador que formulário longo
  - Melhor para mobile-first

- **Backend:**
  - Mesma lógica de validação de formulário
  - Validação por campo
  - Estado de sessão para manter progresso
  - API padrão (REST/GraphQL)

- **Fluxo Exemplo:**
  ```
  Bot: Olá! Bem-vindo(a) à Casa Mãe Paulistana. 
       Vou fazer algumas perguntas para seu cadastro.
  
  Bot: Qual é o seu nome completo?
  Usuário: Maria Silva Santos
  
  Bot: Muito bem, Maria! Qual é a sua data de nascimento?
  Usuário: [seletor de data]
  
  Bot: Qual é o seu CPF?
  Usuário: [máscara ___.___.___-__]
  ```

### Questões Abertas
- [ ] Desenvolver do zero ou usar biblioteca? (Typeform, Landbot, custom?)
- [ ] Como salvar progresso parcial?
- [ ] Permitir voltar e editar respostas?
- [ ] Como fazer upload de documentos no formato chat?
- [ ] Oferecer opção de formulário tradicional como alternativa?

### Benefícios
- ✅ Menor taxa de abandono
- ✅ Mais amigável para público menos digitalizado
- ✅ Experiência moderna e diferenciada
- ✅ Melhor para mobile

### Desafios
- ⚠️ Desenvolvimento mais complexo
- ⚠️ Precisa testes extensivos de UX
- ⚠️ Pode ser mais lento para usuários experientes

---

## 📋 Próximas Ideias a Discutir

_(Adicionar novas ideias abaixo conforme as discussões)_

---

## 🎯 Decisões a Formalizar

Quando as ideias acima estiverem maduras, criar ADRs para:
- [ ] ADR sobre estratégia de comunicação e envio de documentos
- [ ] ADR sobre interface de usuário do cadastro
- [ ] Outras decisões conforme surgir necessidade

---

## 📝 Notas Gerais

- Público-alvo: beneficiários da Casa Mãe Paulistana
- Foco em acessibilidade e usabilidade
- Mobile-first
- Considerar diferentes níveis de alfabetização digital
