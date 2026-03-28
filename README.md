Sistema de Cadastro de Imóveis - São Leopoldo
📋 Sobre o projeto

Este sistema foi desenvolvido com o objetivo de gerenciar o cadastro de pessoas e imóveis da Prefeitura de São Leopoldo. A ideia foi criar algo simples de usar, mas completo o suficiente para atender às necessidades do desafio proposto pelo setor de desenvolvimento.

✨ O que o sistema faz
🔐 Login e controle de acesso
Login com autenticação
Controle básico de acesso às páginas
Sessão do usuário validada
Logout com limpeza dos dados
👤 Cadastro de pessoas
Cadastro com validação de CPF
Campos obrigatórios: nome, data de nascimento e CPF
Campos opcionais: sexo, telefone e e-mail
Possibilidade de editar dados
Exclusão com confirmação (pra evitar apagar sem querer)
🏠 Cadastro de imóveis
Número de inscrição gerado automaticamente
Campos obrigatórios: logradouro, número e bairro
Campo opcional: complemento
Cada imóvel fica vinculado a um proprietário
Edição de dados, inclusive troca de proprietário
Exclusão com confirmação
🔎 Listagens e buscas
Listagem de pessoas com paginação
Filtro por nome, CPF e outros campos
Listagem de imóveis também com paginação
Filtros por inscrição, endereço, bairro e proprietário
Busca em tempo real
🎨 Interface
Funciona bem em celular, tablet e computador
Layout feito com Tailwind
Interface simples e direta
Notificações na tela (tipo alerta)
Confirmações antes de ações importantes
Indicadores de carregamento
🧪 Testes
Foram criados 12 testes automatizados
Testes de validação, autenticação e regras principais
Cobertura das partes mais importantes do sistema
🛠️ Tecnologias usadas
Front-end: React
Estilização: Tailwind CSS
Back-end: tRPC + Express
Banco de dados: MySQL
ORM: Drizzle
Autenticação: OAuth (Manus)
Validação: Zod
Testes: Vitest
Build: Vite
📦 Como rodar o projeto
Pré-requisitos
Node.js 22+
npm ou pnpm
MySQL 8+
Git
1. Clonar o projeto
git clone https://github.com/SEU_USUARIO/cadastro-imoveis-sao-leopoldo.git
cd cadastro-imoveis-sao-leopoldo
2. Instalar as dependências
pnpm install
3. Configurar o banco

Você pode importar o backup com:

mysql -u root -p < database_backup.sql

Ou criar manualmente um banco chamado cadastro_imoveis e importar o arquivo.

4. Criar o .env.local
DATABASE_URL=mysql://root:password@localhost:3306/cadastro_imoveis

JWT_SECRET=sua_chave_secreta

VITE_APP_ID=seu_app_id
OAUTH_SERVER_URL=https://api.manus.im
VITE_OAUTH_PORTAL_URL=https://portal.manus.im

OWNER_NAME=Raul Heisser
OWNER_OPEN_ID=seu_open_id
5. Rodar o projeto
pnpm dev

Acesse: http://localhost:3000

🧪 Rodando os testes
pnpm test
📂 Organização do projeto

O projeto está dividido em duas partes principais:

client/ → Front-end em React
server/ → Back-end com tRPC e Express
drizzle/ → Schema e migrations do banco

Cada parte está separada pra facilitar manutenção e organização.

📊 Banco de dados

O sistema possui três tabelas principais:

users → usuários do sistema
pessoas → cadastro de pessoas
imoveis → cadastro de imóveis

Os imóveis são vinculados a pessoas através de chave estrangeira.

🚀 Build para produção
pnpm build
pnpm start
🔗 API (resumo)
Pessoas
Listar
Buscar por ID
Criar
Atualizar
Deletar
Imóveis
Listar
Buscar por ID
Buscar por proprietário
Criar
Atualizar
Deletar
Autenticação
Ver usuário logado
Logout
👤 Autor

Raul Heisser
raulheisser36@gmail.com

📄 Observação

Projeto desenvolvido como parte de um desafio técnico.

🎯 O que foi atendido
CRUD completo
Autenticação
Validações
Banco de dados integrado
Interface responsiva
Testes automatizados
