# NodeJS

## 💡 Como Instalar ?

- 📘  https://nodejs.org/pt/download 

---
## Resultado Geral ->
<img width="632" height="766" alt="image" src="https://github.com/user-attachments/assets/590509d0-ff22-4610-97f4-b8c522e73c91" />


## Outras Prints 📑📑
<img width="626" height="218" alt="image" src="https://github.com/user-attachments/assets/ff85a9db-8c1c-4967-ad90-01066025705c" />

<img width="626" height="339" alt="image" src="https://github.com/user-attachments/assets/0b1efd47-6e10-4c97-a313-e7a4b24493fa" />


---
- O QUE É NPM
O gerenciador de pacotes Node (npm) é um dos maiores repositórios de software do
mundo. Ele vem acompanhado do node.js, um ambiente de servidor de código aberto.
Todo projeto npm contém um package.json, um arquivo localizado no diretório raiz. Ele
contém os metadados de projetos ou pacotes npm, como versões de pacotes e
colaboradores.
O arquivo package.json simplifica a identificação, gerenciamento e instalação de um
pacote. É por isso que é essencial incluir um arquivo package.json antes de publicar
projetos no registro npm.

Obs.: O npm vem junto com o NODE JS
---

Comando Atalho Descrição


## PRINCIPAIS COMANDOS NPM

<img width="885" height="255" alt="image" src="https://github.com/user-attachments/assets/e4dd60de-9b57-4df5-bee2-d8160fe2b5b8" />


---

## COMANDOS E ARQUIVOS DO NPM
<h4>Inicializando o gerenciador de pacotes da aplicação:</h4>
<img width="722" height="425" alt="image" src="https://github.com/user-attachments/assets/a2d17a34-8669-4dd1-a727-2fd32d36eb6c" />

---

## INSTALANDO PACOTE EXPRESS COM NPM
<h4>Express.js é um framework web para Node.js, projetado para simplificar o processo de desenvolvimento de
aplicações web e APIs. Ele fornece uma série de funcionalidades robustas para criar servidores HTTP de maneira
eficiente. Com o terminal aberto, execute o comando a seguir:</h4>

<img width="726" height="309" alt="image" src="https://github.com/user-attachments/assets/e92b95df-280b-4dcf-9578-468fc2b6ce10" />

---
<img width="969" height="229" alt="image" src="https://github.com/user-attachments/assets/f9d8edc1-3b2a-4755-9cb6-04eb600f1d30" />

--

## CONFIGURANDO EXPRESS
<h4>Construir código de configuração:</h4>

 ## Código pra rodar o banco
## SERVER.JS
----------------

//Importar pacotes para aplicação
const express = require("express");
const cors = require("cors");
const connection = require("./db_config");
//Definir a porta e instanciar o express
const porta = 3000;
const app = express();
//Habilitar o cors e utilização de JSON
app.use(cors());
app.use(express.json());
// Testar API

// Rota post para cadastrar novo usuario
app.post("/usuarios/cadastrar", (request, response) => {
  // Criar um array  com os dados recebidos
  let params = Array(
    request.body.name,
    request.body.email,
    request.body.password,
    request.body.cpf_number
  );

  // Criar comando de execução no banco de dados
  let query =
    "INSERT INTO users(name, email, password, cpf_number) VALUES( ? ,? ,? ,? );";

  // Passar comando e os dados para função query
  connection.query(query, params, (err, results) => {
    if (results) {
      response.status(201).json({
        success: true,
        message: "Sucesso",
        data: results,
      });
    } else {
      response.status(400).json({
        success: false,
        message: "Sem sucesso",
        data: err,
      });
    }
  });
});

app.get("/usuario/listar", (request, response) => {
  const query = "SELECT * FROM users";

  connection.query(query, (err, results) => {
    if (results) {
      response.status(200).json({
        success: true,
        message: "Sucesso!",
        data: results,
      });
    } else {
      response.status(400).json({
        success: false,
        message: "Sem sucesso!",
        data: err,
      });
    }
  });
});

app.put("/usuario/editar/:id", (request, response) => {

  let params = Array(
    request.body.name, 
    request.params.id
    );
  
  let query = "UPDATE users SET name = ? WHERE id = ?";
  
  connection.query(query, params, (err, results) => {
    if (results) {
      response.status(200).json({
        success: true,
        message: "Sucesso",
        data: results,
      });
    } else {
      response.status(400).json({
        success: false,
        message: "Sem Sucesso",
        data: err,
      });
    }
  });

})

app.delete("/usuario/deletar/:id", (request, response) => {
let params = Array(
  request.params.id
  );

let query = "DELETE FROM users WHERE id = ?;";

connection.query(query, params, (err, results) => {
  if (results) {
    response.status(200).json({
      success: true,
      message: "Sucesso",
      data: results,
    });
  } else {
    response.status(400).json({
      success: false,
      message: "Sem Sucesso",
      data: err,
    });
  }
});
})


app.listen(porta, () => console.log(`Rodando na porta ${porta}`));
// Importar conexão com o banco





##DB_CONFIG
// Importar pacote do MySql
const mysql = require('mysql2');
// Criar conexão com o banco de dados
const connection = mysql.createConnection({
    host: 'localhost',
    user: 'root',
    password: 'root',
    database: 'crud_api',
});
// Testar conexão
connection.connect((err) => {
    if(err){
        throw err;
    } else {
        console.log("MySql Conectado")
    }
});

module.exports = connection;
