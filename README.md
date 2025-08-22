# 🚀 NodeJS + NPM + Express + MySQL

## 💡 Como Instalar o NodeJS?

📘 Acesse o site oficial e baixe a versão recomendada:  
👉 [https://nodejs.org/pt/download](https://nodejs.org/pt/download)

---

## 📊 Resultado Geral
<img width="632" height="766" alt="image" src="https://github.com/user-attachments/assets/590509d0-ff22-4610-97f4-b8c522e73c91" />

### Outras Prints 📑
<img width="626" height="218" alt="image" src="https://github.com/user-attachments/assets/ff85a9db-8c1c-4967-ad90-01066025705c" />
<img width="626" height="339" alt="image" src="https://github.com/user-attachments/assets/0b1efd47-6e10-4c97-a313-e7a4b24493fa" />

---

## 📦 O que é o NPM?

O **NPM (Node Package Manager)** é um dos maiores repositórios de software do mundo.  
Ele já vem junto com o **Node.js** e serve para gerenciar pacotes, instalar dependências e facilitar o desenvolvimento.  

Todo projeto em Node que utiliza NPM contém um arquivo **`package.json`**, responsável por armazenar:
- Metadados do projeto  
- Dependências  
- Versões de pacotes  
- Scripts personalizados  

🔹 Antes de publicar um projeto, é essencial ter o `package.json` configurado.

---

## 🔑 Principais Comandos NPM

<img width="885" height="255" alt="image" src="https://github.com/user-attachments/assets/e4dd60de-9b57-4df5-bee2-d8160fe2b5b8" />

### Comandos mais usados:
- `npm init -y` → Inicializa o projeto com um `package.json` padrão  
- `npm install <pacote>` → Instala um pacote  
- `npm install <pacote> --save-dev` → Instala um pacote apenas para desenvolvimento  
- `npm start` → Executa o script configurado no `package.json`

---

## ⚙️ Inicializando o Gerenciador de Pacotes

<img width="722" height="425" alt="image" src="https://github.com/user-attachments/assets/a2d17a34-8669-4dd1-a727-2fd32d36eb6c" />

---

## 🌐 Instalando o Express com NPM

O **Express.js** é um framework web para Node.js que facilita a criação de **APIs e servidores HTTP**.

### Instalação:
```bash
npm install express


// Importar pacotes para aplicação
const express = require("express");
const cors = require("cors");
const connection = require("./db_config");

// Definir a porta e instanciar o express
const porta = 3000;
const app = express();

// Habilitar o cors e utilização de JSON
app.use(cors());
app.use(express.json());

// Rota POST para cadastrar novo usuário
app.post("/usuarios/cadastrar", (request, response) => {
  let params = [
    request.body.name,
    request.body.email,
    request.body.password,
    request.body.cpf_number,
  ];

  let query =
    "INSERT INTO users(name, email, password, cpf_number) VALUES(?, ?, ?, ?);";

  connection.query(query, params, (err, results) => {
    if (results) {
      response.status(201).json({ success: true, message: "Sucesso", data: results });
    } else {
      response.status(400).json({ success: false, message: "Sem sucesso", data: err });
    }
  });
});

// Rota GET para listar usuários
app.get("/usuario/listar", (request, response) => {
  const query = "SELECT * FROM users";
  connection.query(query, (err, results) => {
    if (results) {
      response.status(200).json({ success: true, message: "Sucesso!", data: results });
    } else {
      response.status(400).json({ success: false, message: "Sem sucesso!", data: err });
    }
  });
});

// Rota PUT para editar usuário
app.put("/usuario/editar/:id", (request, response) => {
  let params = [request.body.name, request.params.id];
  let query = "UPDATE users SET name = ? WHERE id = ?";
  connection.query(query, params, (err, results) => {
    if (results) {
      response.status(200).json({ success: true, message: "Sucesso", data: results });
    } else {
      response.status(400).json({ success: false, message: "Sem Sucesso", data: err });
    }
  });
});

// Rota DELETE para excluir usuário
app.delete("/usuario/deletar/:id", (request, response) => {
  let params = [request.params.id];
  let query = "DELETE FROM users WHERE id = ?;";
  connection.query(query, params, (err, results) => {
    if (results) {
      response.status(200).json({ success: true, message: "Sucesso", data: results });
    } else {
      response.status(400).json({ success: false, message: "Sem Sucesso", data: err });
    }
  });
});

// Iniciar servidor
app.listen(porta, () => console.log(`Rodando na porta ${porta}`));


-----------------------------------------------------------------

// Importar pacote do MySql
const mysql = require("mysql2");

// Criar conexão com o banco de dados
const connection = mysql.createConnection({
  host: "localhost",
  user: "root",
  password: "root",
  database: "crud_api",
});

// Testar conexão
connection.connect((err) => {
  if (err) {
    throw err;
  } else {
    console.log("MySql Conectado");
  }
});

module.exports = connection;





{
  "name": "api",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "start": "nodemon ./src/server.js"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "cors": "^2.8.5",
    "dotenv": "^17.2.1",
    "express": "^5.1.0",
    "mysql2": "^3.14.3",
    "nodemon": "^3.1.10"
  }
}

