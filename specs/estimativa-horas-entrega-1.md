# Estimativa de Horas - Entrega 1

**Projeto:** Casa Mãe Paulistana  
**Entrega:** Entrega 1 - 22/10/2025  
**Status:** 🔄 Pendente estimativa

---

## 📊 Resumo

| Categoria | Horas Estimadas | Observações |
|-----------|----------------|-------------|
| **Frontend** | TBD | Interface do formulário + uploads |
| **Backend** | TBD | APIs + armazenamento + validações |
| **Infraestrutura** | TBD | Storage, deploy, segurança |
| **Testes** | TBD | Testes unitários + integração + E2E |
| **Documentação** | TBD | Docs técnicas + guias |
| **Gestão/Reuniões** | TBD | Planning, dailies, review |
| **TOTAL** | **TBD** | |

---

## 🎯 Escopo a Estimar

### 1. Formulário de Pré-Cadastro

#### Frontend
- [ ] Interface do formulário (responsivo)
- [ ] Campos de dados pessoais (responsável + dependente)
- [ ] Sistema de upload de documentos (4 arquivos)
- [ ] Seletor de preferência de agendamento
- [ ] Validações client-side
- [ ] Feedback visual (loading, sucesso, erro)
- [ ] Página de confirmação com protocolo

#### Backend
- [ ] API REST/GraphQL para formulário
- [ ] Validação de dados server-side
- [ ] Integração com storage (upload de documentos)
- [ ] Geração de protocolo/identificador único
- [ ] Sistema de notificação (email/webhook)
- [ ] Endpoint para consulta de status

#### Infraestrutura
- [ ] Configuração de storage seguro (S3/Azure/GCP)
- [ ] Configuração de banco de dados
- [ ] Deploy da aplicação
- [ ] SSL/HTTPS
- [ ] Backup e redundância
- [ ] Monitoramento básico

#### Segurança
- [ ] Implementação de criptografia de arquivos
- [ ] Adequação LGPD
- [ ] Rate limiting / proteção contra spam
- [ ] Sanitização de inputs
- [ ] Política de retenção de dados

#### Testes
- [ ] Testes unitários (frontend)
- [ ] Testes unitários (backend)
- [ ] Testes de integração
- [ ] Testes E2E do fluxo completo
- [ ] Testes de upload de arquivos
- [ ] Testes de validação

#### Design/UX
- [ ] Wireframes
- [ ] Protótipo navegável
- [ ] Design system/components
- [ ] Ajustes baseados em feedback

---

## 💡 Considerações para Estimativa

### Fatores que Podem Impactar
- Interface conversacional (chat) vs formulário tradicional
  - Chat: +30-40% de tempo de desenvolvimento
- Complexidade do sistema de agendamento
- Integração com sistemas existentes
- Nível de polimento/UX desejado
- Requisitos de acessibilidade (WCAG)

### Premissas
- _(A definir nas discussões)_
- Stack tecnológica: ?
- Equipe: ? desenvolvedores
- Disponibilidade: ? horas/semana
- Prioridades: MVP vs polido

### Riscos
- Integrações externas não documentadas
- Mudanças de requisitos
- Complexidade não prevista em LGPD
- Performance com múltiplos uploads simultâneos

---

## 📅 Cronograma Sugerido

_(A definir após estimativa)_

**Prazo final:** 22/10/2025

---

## 📝 Notas

**Próximos passos:**
1. Revisar e refinar requisitos
2. Definir stack tecnológica
3. Decidir entre interface chat vs formulário tradicional
4. Estimar horas por componente
5. Definir sprints/milestones
6. Validar viabilidade do prazo

---

## 🔗 Referências

- [Requisitos Detalhados](./entrega-1-22-outubro.md)
- [Ideias e Discussões](../docs/ideias-discussoes.md)
