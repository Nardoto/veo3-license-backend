# VEO3 License Backend

🔐 **Sistema de Gerenciamento de Licenças** para extensões Chrome VEO3 Automator.

## 📋 Descrição

Backend centralizado que gerencia:
- Geração de licenças
- Painel de leads e clientes
- Formulários de cadastro
- Integração com Firebase Firestore

## 🗂️ Estrutura

```
veo3-license-backend/
├── geradores/
│   └── gerador-pro.html       ← Gerador de licenças (admin)
├── landing-page/
│   ├── cadastro.html          ← Formulário de cadastro
│   ├── painel-leads.html      ← Painel de gerenciamento
│   └── ativar-licenca.html    ← Página de ativação
└── api/
    └── firestore.rules        ← Regras de segurança Firebase
```

## 🔥 Firebase Configuration

### Firestore Collections:
- **licenses/** - Licenças geradas
- **leads/** - Leads cadastrados

### Security Rules:
As regras do Firebase estão em `api/firestore.rules`

## 🚀 Funcionalidades

### Gerador de Licenças (`geradores/gerador-pro.html`)
- Geração de chaves únicas (formato: XXXX-XXXX-XXXX-XXXX)
- Criação de credenciais (username/senha)
- Tipos de licença: Trial 3/7 dias, Mensal, Anual, Vitalícia
- Status: inactive → active (quando cliente ativa)
- Tags e categorias
- Mensagens personalizadas para clientes
- Sistema de busca e filtros
- Modal com detalhes completos da licença
- Extensão automática de licenças
- WhatsApp integration

### Painel de Leads (`landing-page/painel-leads.html`)
- Gerenciamento de leads
- Sistema de busca (nome, email, telefone, ferramentas)
- Status tracking: Novo → Contactado → Licenciado
- Link direto para gerador (auto-preenche dados)
- Integração com Firebase

### Cadastro (`landing-page/cadastro.html`)
- Formulário de interesse
- Seleção de ferramentas que o lead usa
- Teste grátis de 3 dias
- Envio automático para Firebase
- Redirecionamento para WhatsApp

## 🔐 Sistema de Licenciamento

### Fluxo de Licença:
1. **Geração** → Admin cria licença no gerador
2. **Envio** → Credenciais enviadas via WhatsApp
3. **Ativação** → Cliente ativa na extensão
4. **Validação** → Firebase valida device fingerprint
5. **Uso** → Extensão funciona enquanto licença válida

### Campos da Licença:
```javascript
{
  licenseKey: "XXXX-XXXX-XXXX-XXXX",
  username: "cliente",
  password: "senha",
  name: "Nome do Cliente",
  email: "email@exemplo.com",
  phone: "+55(99) 99999-9999",
  type: "monthly|trial3|trial7|annual|lifetime",
  plan: "Mensal|Trial 3 Dias|Anual|Vitalícia",
  status: "inactive|active|suspended",
  deviceFingerprint: "hash_do_dispositivo",
  expiresAt: 1234567890,
  createdAt: "2024-01-01T00:00:00Z",
  activatedAt: "2024-01-01T00:00:00Z",
  tag: "test|vip|etc",
  notes: "Observações internas",
  message: "Mensagem para o cliente"
}
```

## 🌐 Deploy

Este backend é servido via **GitHub Pages** através do repositório público:
- Site: https://nardoto.com.br

## 🔗 Links Relacionados

- **Site Público**: https://github.com/Nardoto/nardoto.github.io
- **Extensões**: Cada extensão tem seu próprio repositório privado

## 👥 Colaboradores

- Tharcisio Nardoto (Criador)
- Jackson (Desenvolvedor)

## 📝 Notas

- Sistema integrado com Firebase Firestore
- Licenças compartilhadas entre todas as extensões via chrome.storage.sync
- Device fingerprinting para vinculação única por máquina
