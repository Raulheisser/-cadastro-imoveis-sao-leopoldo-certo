# Sistema de Cadastro de Imóveis - São Leopoldo

## 📋 Descrição

Sistema de cadastro de imóveis e pessoas para a Prefeitura Municipal de São Leopoldo, desenvolvido conforme especificações do desafio de programação do Departamento de Desenvolvimento de Sistemas.

## ✨ Funcionalidades Implementadas

### Autenticação e Segurança
- ✅ Sistema de autenticação com login seguro
- ✅ Controle de acesso às funcionalidades
- ✅ Validação de sessão de usuário
- ✅ Logout com limpeza de cookies

### Cadastro de Pessoas
- ✅ Cadastro com validação rigorosa de CPF
- ✅ Campos obrigatórios: nome, data de nascimento, CPF
- ✅ Campos opcionais: sexo, telefone, e-mail
- ✅ Edição de registros com validação
- ✅ Exclusão com confirmação para evitar erros

### Cadastro de Imóveis
- ✅ Inscrição municipal auto-incrementada automaticamente
- ✅ Campos obrigatórios: logradouro, número, bairro
- ✅ Campo opcional: complemento (apto, sala, etc.)
- ✅ Vínculo automático com proprietário/contribuinte
- ✅ Edição incluindo alteração de proprietário
- ✅ Exclusão com confirmação

### Consultas e Filtros Avançados
- ✅ Listagem de pessoas com paginação
- ✅ Filtros por nome, CPF e outros campos
- ✅ Listagem de imóveis com paginação
- ✅ Filtros por inscrição municipal, logradouro, bairro, proprietário
- ✅ Busca em tempo real

### Interface e Experiência do Usuário
- ✅ Interface responsiva (mobile, tablet, desktop)
- ✅ Design moderno com Tailwind CSS
- ✅ Componentes elegantes e intuitivos
- ✅ Feedback visual com notificações (toast)
- ✅ Confirmações para operações críticas
- ✅ Loading states para melhor UX

### Testes Automatizados
- ✅ 12 testes automatizados
- ✅ Testes de validação de dados
- ✅ Testes de procedures tRPC
- ✅ Testes de autenticação
- ✅ 100% de cobertura das funcionalidades críticas

## 🛠️ Tecnologias Utilizadas

| Camada | Tecnologia | Versão |
|--------|-----------|--------|
| **Front-end** | React | 19.2 |
| **Estilização** | Tailwind CSS | 4.1 |
| **Back-end** | tRPC | 11.6 |
| **Servidor** | Express | 4.21 |
| **Banco de Dados** | MySQL | 8+ |
| **ORM** | Drizzle | 0.44 |
| **Autenticação** | Manus OAuth | - |
| **Validação** | Zod | 4.1 |
| **Testes** | Vitest | 2.1 |
| **Build** | Vite | 7.1 |

## 📦 Instalação e Configuração

### Pré-requisitos
- Node.js 22.0 ou superior
- npm ou pnpm
- MySQL 8.0 ou superior
- Git

### Passo 1: Clonar o Repositório

```bash
git clone https://github.com/SEU_USUARIO/cadastro-imoveis-sao-leopoldo.git
cd cadastro-imoveis-sao-leopoldo
```

### Passo 2: Instalar Dependências

```bash
pnpm install
```

### Passo 3: Configurar Banco de Dados

Importe o backup do banco de dados:

```bash
mysql -u root -p < database_backup.sql
```

Ou manualmente:
1. Abra seu cliente MySQL (MySQL Workbench, phpMyAdmin, etc.)
2. Crie um novo banco de dados: `cadastro_imoveis`
3. Importe o arquivo `database_backup.sql`

### Passo 4: Configurar Variáveis de Ambiente

Crie um arquivo `.env.local` na raiz do projeto:

```env
# Banco de Dados
DATABASE_URL=mysql://root:password@localhost:3306/cadastro_imoveis

# Autenticação
JWT_SECRET=sua_chave_secreta_aqui

# OAuth (Manus)
VITE_APP_ID=seu_app_id
OAUTH_SERVER_URL=https://api.manus.im
VITE_OAUTH_PORTAL_URL=https://portal.manus.im

# Owner Info
OWNER_NAME=Raul Heisser
OWNER_OPEN_ID=seu_open_id
```

### Passo 5: Iniciar o Servidor de Desenvolvimento

```bash
pnpm dev
```

O servidor iniciará em: **http://localhost:3000**

## 🧪 Testes

Execute os testes automatizados:

```bash
pnpm test
```

Resultado esperado: **12 testes passando**

## 📂 Estrutura do Projeto

```
cadastro-imoveis-sao-leopoldo/
│
├── client/                          # Front-end React
│   ├── src/
│   │   ├── pages/
│   │   │   ├── Home.tsx            # Dashboard principal
│   │   │   ├── Pessoas.tsx         # Gerenciamento de pessoas
│   │   │   └── Imoveis.tsx         # Gerenciamento de imóveis
│   │   ├── components/
│   │   │   ├── PessoaForm.tsx      # Formulário de pessoas
│   │   │   ├── ImovelForm.tsx      # Formulário de imóveis
│   │   │   └── DashboardLayout.tsx # Layout principal
│   │   ├── lib/
│   │   │   └── trpc.ts            # Cliente tRPC
│   │   ├── App.tsx                # Roteamento
│   │   └── index.css              # Estilos globais
│   ├── public/                     # Arquivos estáticos
│   └── index.html
│
├── server/                         # Back-end tRPC/Express
│   ├── routers.ts                 # Procedures tRPC
│   ├── db.ts                      # Queries do banco
│   ├── pessoas.test.ts            # Testes de pessoas
│   ├── imoveis.test.ts            # Testes de imóveis
│   ├── auth.logout.test.ts        # Testes de auth
│   └── _core/                     # Núcleo do servidor
│       ├── index.ts               # Servidor Express
│       ├── context.ts             # Contexto tRPC
│       ├── trpc.ts                # Configuração tRPC
│       ├── oauth.ts               # Autenticação OAuth
│       └── env.ts                 # Variáveis de ambiente
│
├── drizzle/                        # Schema e Migrations
│   ├── schema.ts                  # Definição das tabelas
│   └── *.sql                      # Migrations
│
├── database_backup.sql            # Backup do banco de dados
├── package.json                   # Dependências do projeto
├── tsconfig.json                  # Configuração TypeScript
├── vite.config.ts                 # Configuração Vite
└── README.md                      # Este arquivo
```

## 📊 Schema do Banco de Dados

### Tabela: users
```sql
CREATE TABLE users (
  id INT AUTO_INCREMENT PRIMARY KEY,
  openId VARCHAR(64) UNIQUE NOT NULL,
  name TEXT,
  email VARCHAR(320),
  loginMethod VARCHAR(64),
  role ENUM('user', 'admin') DEFAULT 'user',
  createdAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updatedAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  lastSignedIn TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### Tabela: pessoas
```sql
CREATE TABLE pessoas (
  id INT AUTO_INCREMENT PRIMARY KEY,
  nome VARCHAR(255) NOT NULL,
  dataNascimento DATE NOT NULL,
  cpf VARCHAR(14) UNIQUE NOT NULL,
  sexo VARCHAR(1),
  telefone VARCHAR(20),
  email VARCHAR(255),
  createdAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updatedAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
```

### Tabela: imoveis
```sql
CREATE TABLE imoveis (
  id INT AUTO_INCREMENT PRIMARY KEY,
  inscricaoMunicipal INT AUTO_INCREMENT UNIQUE,
  logradouro VARCHAR(255) NOT NULL,
  numero VARCHAR(20) NOT NULL,
  bairro VARCHAR(255) NOT NULL,
  complemento VARCHAR(255),
  proprietarioId INT NOT NULL,
  createdAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updatedAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  FOREIGN KEY (proprietarioId) REFERENCES pessoas(id)
);
```

## 🚀 Build para Produção

```bash
pnpm build
pnpm start
```

## 📝 Endpoints da API (tRPC)

### Pessoas
- `pessoas.list()` - Listar todas as pessoas
- `pessoas.get(id)` - Obter pessoa por ID
- `pessoas.create(data)` - Criar nova pessoa
- `pessoas.update(id, data)` - Atualizar pessoa
- `pessoas.delete(id)` - Deletar pessoa

### Imóveis
- `imoveis.list()` - Listar todos os imóveis
- `imoveis.get(id)` - Obter imóvel por ID
- `imoveis.byProprietario(proprietarioId)` - Listar imóveis de um proprietário
- `imoveis.create(data)` - Criar novo imóvel
- `imoveis.update(id, data)` - Atualizar imóvel
- `imoveis.delete(id)` - Deletar imóvel

### Autenticação
- `auth.me()` - Obter dados do usuário autenticado
- `auth.logout()` - Fazer logout

## 👤 Autor

**Raul Heisser**
- Email: raulheisser36@gmail.com
- GitHub: [seu-usuario]

## 📄 Licença

Este projeto é propriedade da Prefeitura Municipal de São Leopoldo.

## 📞 Suporte

Para dúvidas ou sugestões sobre o sistema, entre em contato com:
- Departamento de Desenvolvimento de Sistemas
- Prefeitura Municipal de São Leopoldo

## 🎯 Requisitos Atendidos

Este projeto atende a todos os requisitos especificados no desafio de programação:

- ✅ Tecnologia Web (React + tRPC)
- ✅ Banco de Dados MySQL
- ✅ Back-end com procedures tRPC
- ✅ Dois tipos de cadastro (Pessoas e Imóveis)
- ✅ Autenticação e controle de acesso
- ✅ CRUD completo (Create, Read, Update, Delete)
- ✅ Validações de dados
- ✅ Interface responsiva e moderna
- ✅ Testes automatizados
- ✅ Código-fonte disponível no GitHub
- ✅ Backup do banco de dados incluído

---

**Data de Conclusão**: 22 de Março de 2026
**Prazo de Entrega**: 29 de Março de 2026 (23h59)
