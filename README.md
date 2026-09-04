# 🐾 PetHouse — Sistema de Gestão Veterinária

> Sistema web completo para gestão de clínicas veterinárias, desenvolvido em HTML, CSS e JavaScript puro. Funciona diretamente no navegador, sem necessidade de instalação ou servidor.

---

## 📋 Índice

- [Sobre o Projeto](#sobre-o-projeto)
- [Funcionalidades](#funcionalidades)
- [Tecnologias](#tecnologias)
- [Como Usar](#como-usar)
- [Perfis de Acesso](#perfis-de-acesso)
- [Módulos do Sistema](#módulos-do-sistema)
- [Estrutura do Projeto](#estrutura-do-projeto)
- [Armazenamento de Dados](#armazenamento-de-dados)
- [Autores](#autores)

---

## 📌 Sobre o Projeto

O **PetHouse** é um protótipo operacional de sistema de gestão para clínicas veterinárias de bairro, desenvolvido como projeto acadêmico na disciplina de **Prototipagem de Sistemas Computacionais** da Universidade Cidade de São Paulo (UNICID).

O sistema resolve problemas reais identificados em clínicas que ainda operam de forma manual — cadernos, planilhas soltas e mensagens —, centralizando em uma única plataforma:

- Cadastro de tutores e pets
- Gestão de agendamentos com controle de conflitos
- Registro clínico de atendimentos
- Controle de estoque com alertas automáticos

---

## ✅ Funcionalidades

### Geral
- 🔐 Sistema de login com perfis e níveis de acesso
- 💾 Salvamento automático no `localStorage` (dados persistem após fechar o navegador)
- 📱 Layout responsivo (funciona em desktop e mobile)
- 🌙 Tema escuro moderno

### Painel de Controle
- Cards de resumo: tutores, pets, agendamentos do dia e alertas de estoque
- Tabela de próximos agendamentos
- Painel de estoque crítico com barra de progresso
- Tabela dos últimos atendimentos registrados

### Tutores
- Cadastro completo com CPF, telefone, e-mail e endereço
- Validação de CPF duplicado
- Busca em tempo real por nome ou CPF
- Modal de detalhe com lista de pets vinculados

### Pets
- Cadastro vinculado ao tutor
- **Upload de foto** (converte para base64, salvo localmente)
- Avatar circular com foto ou emoji da espécie
- Histórico completo de atendimentos por pet

### Agendamentos
- Criação e edição de agendamentos
- **Verificação de conflito em tempo real** — bloqueia horários já ocupados
- **Grade visual** de disponibilidade do dia (08h às 18h, intervalos de 30min)
- Sugestão automática de horários alternativos disponíveis
- Filtros por status: Pendente, Confirmado, Concluído, Cancelado
- Ações rápidas: Confirmar, Concluir, Cancelar

### Atendimento
- Registro clínico completo: diagnóstico, procedimentos, recomendações
- **Agendamento de retorno** com grade de disponibilidade integrada
- **Envio de protocolo pelo Gmail** com dados preenchidos automaticamente
- **Impressão de protocolo** em layout A4 profissional com área de assinatura
- Busca por nome do pet, tutor ou **número do protocolo** (`#PH-00001`)
- Edição de status: Aguardando, Realizado, Cancelado
- Cancelamento com motivo obrigatório

### Estoque
- Cadastro de itens com código, categoria, unidade e preço
- Movimentação de entrada e saída com validação de saldo
- **Alerta automático** de estoque abaixo do mínimo
- Barra de progresso colorida por nível (verde/amarelo/vermelho)
- Badge de alerta na sidebar
- Filtros por categoria: Vacinas, Medicamentos, Cosméticos, Insumos

---

## 🛠️ Tecnologias

| Tecnologia | Uso |
|---|---|
| **HTML5** | Estrutura, modais, formulários e tabelas |
| **CSS3** | Tema escuro, layout, animações e responsividade |
| **JavaScript (ES6+)** | Lógica, CRUD, validações, localStorage |
| **Google Fonts** | Fontes Playfair Display e DM Sans (opcional, funciona offline) |
| **Gmail API (mailto)** | Envio de protocolo por e-mail |

> Nenhum framework, biblioteca ou dependência obrigatória. Tudo em um único arquivo `.html`.

---

## 🚀 Como Usar

### Opção 1 — Abrir localmente
1. Baixe o arquivo `index.html`
2. Dê **duplo clique** no arquivo
3. O sistema abre diretamente no navegador

### Opção 2 — Hospedar online (Netlify)
1. Acesse [netlify.com/drop](https://app.netlify.com/drop)
2. Arraste o arquivo `index.html` para a página
3. Em segundos você terá uma URL pública

### Opção 3 — GitHub Pages
1. Faça o upload do `index.html` em um repositório público
2. Vá em **Settings → Pages → Branch: main → Save**
3. Acesse `https://seuusuario.github.io/nome-do-repositorio`

---

## 🔐 Perfis de Acesso

| Perfil | Usuário | Painel | Tutores | Pets | Agendamentos | Atendimento | Estoque |
|---|---|---|---|---|---|---|---|
| 👔 Gerente | `gerente` | ✅ | ❌ | ❌ | ❌ | ❌ | ✅ |
| 💼 Recepcionista | `recepcao` | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ |
| 🩺 Veterinário | `veterinario` | ✅ | ❌ | ✅ | ✅ | ✅ | ❌ |
| 📦 Almoxarife | `almoxarife` | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ |

> Senha padrão para todos os perfis: `1234`

---

## 📦 Módulos do Sistema

```
PetHouse
├── 🔐 Login              — Autenticação com perfis de acesso
├── 🏠 Painel de Controle — Visão geral e alertas
├── 👤 Tutores            — Cadastro de clientes
├── 🐾 Pets               — Cadastro de animais com foto
├── 📅 Agendamentos       — Agenda com controle de conflitos
├── 🩺 Atendimento        — Registro clínico e protocolos
└── 📦 Estoque            — Controle de insumos e vacinas
```

---

## 🗂️ Estrutura do Projeto

```
pethouse/
└── index.html    — Sistema completo em arquivo único
```

O sistema inteiro está contido em **um único arquivo HTML** com CSS e JavaScript embutidos, incluindo:
- A logo da clínica em base64
- Todo o sistema de dados em memória
- Persistência via `localStorage`

---

## 💾 Armazenamento de Dados

Os dados são salvos no **`localStorage`** do navegador sob a chave `pethouse_db`. Isso significa:

- ✅ Dados persistem após fechar o navegador
- ✅ Funciona 100% offline
- ✅ Sem necessidade de servidor ou banco de dados
- ⚠️ Dados são por navegador — cada dispositivo tem seu próprio armazenamento
- ⚠️ Limpar dados do navegador apaga os registros

### Resetar dados
Na sidebar, o botão **🗑️ Resetar dados** apaga todos os registros e retorna ao estado inicial (com confirmação).

---

## 📄 Protocolo de Atendimento

Cada atendimento gera um protocolo único no formato:

```
#PH-00001-20260513
 │   │      └── Data do atendimento (AAAAMMDD)
 │   └────────── Número sequencial com 5 dígitos
 └────────────── Prefixo PetHouse
```

O protocolo pode ser:
- **Impresso** em layout A4 com área de assinatura
- **Enviado pelo Gmail** com todos os dados preenchidos automaticamente
- **Pesquisado** na aba de Atendimento pelo número

---

## 👥 Autora

Desenvolvido por **Ellen Cristina Soares de Jesus**

**Professor:** Marcelo de Freitas Pintaud  
**Instituição:** Universidade Cidade de São Paulo (UNICID)  
**Disciplina:** Prototipagem de Sistemas Computacionais — 2026

---

## 📜 Licença

Este projeto foi desenvolvido para fins acadêmicos.

---

<div align="center">
  <strong>🐾 PetHouse — Clínica Veterinária</strong><br/>
  Feito com HTML, CSS e JavaScript puro
</div>
