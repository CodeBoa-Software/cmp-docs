# Requisitos para Entrega 1 - 22 de Outubro

**Data da Entrega:** 22/10/2025  
**Projeto:** Casa Mãe Paulistana  
**Responsável:** CodeBoa Software

---

## 📋 Escopo da Entrega

### 1. Formulário de Pré-Cadastro

**Descrição:** Formulário público (link compartilhável) para pré-cadastro de beneficiários.

#### 1.1 Dados a Coletar
- Informações pessoais do responsável
- Informações do dependente
- Preferência de agendamento para triagem

#### 1.2 Documentos Obrigatórios (Upload)
- ✅ Comprovante de residência
- ✅ Laudo médico
- ✅ RG do Responsável
- ✅ RG ou Certidão de Nascimento do Dependente

#### 1.3 Pré-Agendamento de Triagem
- Sistema de seleção de preferência de dia/hora
- Usuário escolhe preferência (não é agendamento definitivo)
- Sistema deve permitir flexibilidade para equipe ajustar depois

---

## ✅ Checklist de Implementação

### Formulário
- [ ] Criar formulário público com link compartilhável
- [ ] Campos de dados pessoais (responsável)
- [ ] Campos de dados pessoais (dependente)
- [ ] Sistema de upload de documentos (4 documentos obrigatórios)
- [ ] Validação de formatos de arquivo aceitos
- [ ] Validação de tamanho máximo de arquivo
- [ ] Seletor de preferência de dia/hora para triagem

### Backend
- [ ] API para receber dados do formulário
- [ ] Armazenamento seguro de documentos
- [ ] Validação de campos obrigatórios
- [ ] Geração de protocolo/confirmação de pré-cadastro
- [ ] Sistema de notificação ao receber novo pré-cadastro

### UX/UI
- [ ] Interface responsiva (mobile-first)
- [ ] Feedback de upload de documentos
- [ ] Confirmação de envio
- [ ] Página de sucesso com protocolo
- [ ] Instruções claras sobre próximos passos

### Segurança
- [ ] Armazenamento seguro de documentos (criptografia)
- [ ] Conformidade LGPD
- [ ] Link público sem exposição de dados sensíveis
- [ ] Proteção contra spam/abuso

### Testes
- [ ] ⚠️ **IMPORTANTE:** Testar upload de documentos em dispositivos diferentes
  - [ ] Android (celular e tablet)
  - [ ] iOS (iPhone e iPad)
  - [ ] Desktop (Windows, Mac, Linux)
  - [ ] Diferentes navegadores (Chrome, Safari, Firefox, Edge)
- [ ] Validar upload de PDFs
- [ ] Validar upload de imagens (JPG, PNG)
- [ ] Validar captura direta da câmera (mobile)
- [ ] Testar em diferentes tamanhos de tela
- [ ] Validar limites de tamanho de arquivo
- [ ] Testar conexões lentas/instáveis

---

## 📝 Notas

### Considerações Técnicas

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

**Pré-Agendamento:**
- Não é agendamento definitivo, apenas preferência
- Equipe poderá ajustar conforme disponibilidade
- Considerar mostrar grade de horários disponíveis ou permitir texto livre?

**Link Público:**
- URL amigável e compartilhável
- Pode ser divulgado em redes sociais, WhatsApp, etc.
- Sem necessidade de autenticação prévia

### Perguntas/Decisões Pendentes

- [ ] Interface conversacional (chat) ou formulário tradicional?
  - _Referência: ver discussão em `/docs/ideias-discussoes.md`_
- [ ] Como será o fluxo de confirmação do agendamento definitivo?
- [ ] Equipe administrativa terá painel para visualizar pré-cadastros?
- [ ] Notificação para equipe: email, dashboard, WhatsApp?
- [ ] Prazo de validade do pré-cadastro?
- [ ] ⚠️ Estratégia de testes cross-device está definida?
- [ ] Quem fará os testes em dispositivos reais?
- [ ] Precisamos de device lab ou usar BrowserStack/similar?

---

## 🔗 Referências

- [Ideias e Discussões](../docs/ideias-discussoes.md) - Interface conversacional vs formulário
- LGPD - Lei Geral de Proteção de Dados

