# 🎵 MWE Harmonize

> Sistema de gerenciamento para eventos, clientes, equipe, agenda e repertórios musicais.

O **MWE Harmonize** é uma aplicação web desenvolvida com **TypeScript, Node.js, Express e PostgreSQL**, com autenticação de usuários, gerenciamento de eventos e clientes, agenda, equipe, repertório e outros módulos do sistema.

---

## ✨ Funcionalidades

### 🔐 Autenticação
- Login e logout
- Recuperação de acesso
- Sessões de usuário
- Controle de permissões
- Organização/empresa isolada por usuário
- Alteração de senha

### 📅 Eventos
- Cadastro de eventos
- Consulta de eventos
- Edição e exclusão
- Cliente, local, data e horário
- Status do evento
- Detalhes do evento
- Associação de integrantes da equipe
- Associação de repertórios

### 🗓️ Agenda
- Visualização mensal
- Visualização semanal
- Visualização em lista
- Busca de eventos
- Filtros
- Criação de eventos pela agenda

### 👥 Clientes
- Cadastro de clientes
- Consulta
- Edição
- Exclusão
- Busca e filtros
- Associação com eventos

### 🎤 Equipe
- Cadastro de integrantes
- Função
- Instrumento
- Formação
- Disponibilidade e escalas
- Associação com eventos

### 🎶 Repertório
- Cadastro de músicas
- Artista/compositor
- Instrumentação
- Observações
- Associação de músicas aos eventos
- Aprovação de repertório
- Organização por momentos

### 💰 Financeiro
- Receitas
- Recebimentos
- Valores a receber
- Parcelas e vencimentos
- Status
- Filtros
- Relatórios e indicadores

### 📊 Relatórios
- Indicadores de eventos
- Status e taxas de confirmação
- Informações financeiras
- Exportação de dados

---

## 🛠️ Tecnologias

| Tecnologia | Uso |
|---|---|
| **Node.js** | Ambiente de execução |
| **TypeScript** | Backend e tipagem |
| **Express** | API e servidor web |
| **PostgreSQL** | Banco de dados principal |
| **pg** | Conexão com PostgreSQL |
| **HTML/CSS/JavaScript** | Interface web |
| **tsx** | Execução do TypeScript |
| **Node Test Runner** | Testes automatizados |

---

# 🚀 Como executar

## 1. Pré-requisitos

Antes de começar, instale:

- **Node.js 20+**
- **PostgreSQL 15+**
- **Git**

Verifique as instalações:

```powershell
node -v
npm -v
psql --version
git --version
```

---

## 2. Baixar o projeto

No terminal:

```powershell
git clone https://github.com/BlackAlexandre/mweharmonize.git
```

Entre na pasta:

```powershell
cd mweharmonize
```

---

## 3. Instalar as dependências

Execute:

```powershell
npm install
```

---

## 4. Configurar o banco PostgreSQL

Crie um banco de dados PostgreSQL para o projeto.

Exemplo:

```text
Nome do banco: mwe_harmonize
Usuário: postgres
Porta: 5432
```

Depois, crie o arquivo `.env` a partir do modelo:

```powershell
Copy-Item .env.example .env
```

Abra o `.env`:

```powershell
notepad .env
```

Configure pelo menos a conexão com o PostgreSQL:

```env
DATABASE_URL=postgresql://postgres:SUA_SENHA@localhost:5432/mwe_harmonize
```

Também configure as variáveis administrativas e de e-mail presentes no `.env.example` conforme necessário.

> ⚠️ **Nunca envie o arquivo `.env` para o GitHub.**
>
> O `.env` já está protegido pelo `.gitignore`.

---

## 5. Preparar o banco

Se o projeto estiver sendo configurado em um banco PostgreSQL novo, execute:

```powershell
npm run migrate:postgres -- ./harmonize.db
```

Esse comando realiza a migração dos dados do banco SQLite existente para o PostgreSQL.

Se você estiver iniciando o sistema sem dados antigos, siga a estrutura de banco prevista pelo projeto e pelo arquivo `database.ts`.

---

# ▶️ Executar o sistema

Com o PostgreSQL funcionando e o `.env` configurado:

```powershell
npm run dev
```

O servidor será iniciado localmente.

Abra no navegador:

```text
http://localhost:3000
```

### Para parar o servidor

No terminal:

```text
Ctrl + C
```

---

# 🧪 Testes

Para executar os testes:

```powershell
npm test
```

Para verificar a compilação TypeScript e a sintaxe do JavaScript:

```powershell
npm run build
```

Para verificar problemas de formatação:

```powershell
npm run format
```

> Alguns testes específicos de PostgreSQL podem exigir uma variável `TEST_DATABASE_URL` configurada para um banco de testes.

---

# 📁 Estrutura principal

```text
mweharmonize/
│
├── public/
│   ├── app.js
│   ├── index.html
│   ├── style.css
│   └── icons/
│
├── scripts/
│   └── migrate-sqlite-to-postgres.ts
│
├── tests/
│   ├── api.test.ts
│   ├── email-config.test.ts
│   ├── migration.test.ts
│   ├── persistence.test.ts
│   ├── postgres-test.ts
│   └── ui.test.ts
│
├── database.ts
├── email-service.ts
├── server.ts
├── package.json
├── tsconfig.json
├── .env.example
└── README.md
```

---

# 🔒 Segurança

O projeto utiliza variáveis de ambiente para informações sensíveis.

**Nunca coloque no código ou publique:**

- Senhas
- Chaves de API
- Tokens
- Credenciais do PostgreSQL
- Dados reais de usuários
- Arquivo `.env`

Antes de fazer um commit:

```powershell
git status
```

Confira se nenhum arquivo sensível está sendo enviado.

---

# 🔄 Fluxo de desenvolvimento

Depois de fazer alterações:

```powershell
git status
```

Adicionar os arquivos:

```powershell
git add .
```

Criar o commit:

```powershell
git commit -m "feat: descricao da alteracao"
```

Enviar para o GitHub:

```powershell
git push
```

---

# 🧹 Comandos úteis

### Iniciar o sistema

```powershell
npm run dev
```

### Instalar dependências

```powershell
npm install
```

### Testar

```powershell
npm test
```

### Verificar build

```powershell
npm run build
```

### Formatar código

```powershell
npm run format
```

### Verificar Git

```powershell
git status
```

### Ver histórico

```powershell
git log --oneline
```

---

# 🗄️ PostgreSQL

O MWE Harmonize utiliza **PostgreSQL como banco de dados principal**.

A aplicação utiliza a variável:

```env
DATABASE_URL=postgresql://usuario:senha@localhost:5432/banco
```

O banco deve estar ativo antes de iniciar o servidor.

Para verificar se o PostgreSQL está acessível, você pode usar:

```powershell
psql -U postgres -h localhost
```

---

# 📧 Recuperação de acesso

O sistema possui integração de e-mail para recursos como recuperação de acesso e convites.

As configurações devem ser informadas no `.env`.

Consulte o arquivo:

```text
.env.example
```

para saber quais variáveis estão disponíveis.

---

# 📚 Documentação adicional

Informações mais detalhadas sobre execução, banco de dados e migração estão disponíveis em:

```text
docs/EXECUCAO-E-DEPLOY.md
```

---

# 👨‍💻 Desenvolvimento

Este projeto foi estruturado para desenvolvimento local utilizando:

```text
Node.js
    ↓
Express + TypeScript
    ↓
PostgreSQL
    ↓
Interface Web
```

O desenvolvimento pode ser realizado completamente pelo **terminal + navegador local**, sem necessidade de serviços de hospedagem para executar o projeto localmente.

---

## 📌 Repositório

**GitHub:**

https://github.com/BlackAlexandre/mweharmonize

---

## 📄 Licença

Este projeto possui licença conforme definido pelos responsáveis pelo repositório.
