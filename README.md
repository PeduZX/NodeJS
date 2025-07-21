# NodeJS

## 💡 Como Instalar ?

- 📘  https://nodejs.org/pt/download 

---
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

## CONFIGURANDO EXPRESS
<h4>Construir código de configuração:</h4>

 <h2>Código Em JS:</h2>
//Solicitar pacote instalado
const express = require("express")
//Instanciar express na constante app
const app = express()
//Criar porta para rodar o servidor
const port = 3333;

//Executar servidor express
app.listen(port, () => console.log(`rodando na porta ${port}`))
