-----

# QuickAdd - Sistema de Gestão

Este é o repositório do QuickAdd, um projeto full-stack desenvolvido como um sistema de gestão. A aplicação permite o controle de usuários, produtos, vendas, clientes e mais, com um back-end em Node.js e um front-end em JavaScript puro.

Este foi o meu segundo projeto completo, integrando tanto o back-end quanto o front-end, focado em aplicar conceitos de Orientação a Objetos e boas práticas de desenvolvimento.

## 🚀 Funcionalidades

O sistema possui uma API RESTful no back-end e uma interface de usuário no front-end para gerenciar os seguintes módulos:

  * **Autenticação:** Login de usuário com autenticação via JWT (JSON Web Token).
  * **Gestão de Usuários:** CRUD completo de usuários.
  * **Gestão de Perfis/Cargos:** CRUD de perfis de usuário (ex: admin, funcionário).
  * **Gestão de Clientes:** CRUD de clientes.
  * **Gestão de Categorias:** CRUD de categorias para produtos.
  * **Gestão de Produtos:** CRUD de produtos.
  * **Gestão de Fornecedores:** CRUD de fornecedores (Supply).
  * **Gestão de Vendas:** CRUD para registro de vendas.

## 🛠️ Tecnologias Utilizadas

### Back-End

  * **Node.js**
  * **TypeScript**
  * **Express** (para criação da API)
  * **TypeORM** (para o ORM e conexão com o banco)
  * **PostgreSQL** (banco de dados)
  * **JSON Web Token (JWT)** (para autenticação)
  * **Bcrypt.js** (para hash de senhas)
  * **ts-node-dev** (para desenvolvimento)

### Front-End

  * **HTML5**
  * **CSS3**
  * **JavaScript (Vanilla)**
  * **Axios** (para requisições à API)
  * **Parcel** (para empacotamento dos módulos)

## 🏗️ Arquitetura do Back-end

O back-end foi estruturado seguindo princípios de separação de responsabilidades, (próximo ao SOLID), utilizando uma arquitetura em camadas:

  * **Controllers:** Responsáveis por receber as requisições HTTP e retornar as respostas.
  * **Services:** Contêm toda a lógica de negócio da aplicação.
  * **Repositories:** Camada de abstração para acesso aos dados, utilizando os repositórios do TypeORM.
  * **Entities:** Definição das tabelas do banco de dados.
  * **Middleware:** Usado para interceptar requisições, como na verificação de autenticação.

## 📋 Pré-requisitos

  * [Node.js](https://nodejs.org/en/) (v14 ou superior)
  * [Yarn](https://yarnpkg.com/) (gerenciador de pacotes)
  * Um servidor **PostgreSQL** local ou remoto.

## ⚙️ Instalação e Execução

Siga os passos abaixo para configurar e rodar o projeto localmente.

### 1\. Configurando o Back-End

O back-end é responsável pela API e conexão com o banco de dados.

```bash
# 1. Navegue até a pasta do back-end
cd Back

# 2. Instale as dependências
yarn install
```

**Configuração do Banco de Dados:**

1.  Abra o arquivo `ormconfig.json`.
2.  Altere o valor da propriedade `"database"` para o nome do banco de dados que você criou no PostgreSQL.
3.  Atualize as propriedades `"username"` e `"password"` com suas credenciais de acesso ao PostgreSQL.

**Migrações (Migrations):**

Após configurar o `ormconfig.json`, você precisa rodar as migrações para criar as tabelas no banco de dados.

```bash
# 3. Use o script 'typeorm' definido no package.json para rodar as migrações
yarn typeorm migration:run
```

**Iniciando o Servidor:**

```bash
# 4. Inicie o servidor em modo de desenvolvimento
yarn dev
```

O servidor back-end estará rodando em `http://localhost:3000` (ou na porta definida em `src/server.ts`).

### 2\. Configurando o Front-End

O front-end consome a API do back-end.

```bash
# 1. Em um novo terminal, navegue até a pasta do front-end
cd Front

# 2. Instale as dependências
yarn install

# 3. Inicie o servidor de desenvolvimento do Parcel
yarn dev
```

O Parcel iniciará o servidor de desenvolvimento (geralmente em `http://localhost:1234`) e abrirá a aplicação no seu navegador.

## ⚠️ Observação sobre Autenticação

Conforme as instruções originais do projeto, o middleware de autenticação (`ensureAuthenticated`) está comentado no arquivo `src/routes.ts`.

  * **Para testar sem login:** Deixe como está. A API estará aberta.
  * **Para habilitar a autenticação:** Vá ao arquivo `src/routes.ts`, encontre as rotas protegidas e remova o `//` do middleware para que o token JWT seja exigido.
