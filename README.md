# 📝 To-Do List API

Esta é uma API de gerenciamento de tarefas (To-do List) desenvolvida em Java utilizando Spring Boot. A aplicação permite que os usuários criem contas, adicionem, visualizem, editem e excluam tarefas. Apenas o usuário que criou a tarefa pode editá-la ou excluí-la. Além disso, a aplicação utiliza autenticação de usuários e criptografia de senha com a biblioteca BCrypt.

## ⚙️ Funcionalidades

- 👤 **Criação de Usuários**: Permite criar novos usuários para utilizar a API.
- 📝 **Criação de Tarefas**: Usuários podem criar novas tarefas.
- ✏️ **Edição de Tarefas**: Apenas o usuário que criou a tarefa pode editá-la.
- 🗑️ **Exclusão de Tarefas**: Apenas o usuário que criou a tarefa pode excluí-la.
- 📋 **Listagem de Tarefas**: Usuários podem visualizar suas tarefas.
 🔑 **Autenticação de Usuários**: Utiliza autenticação baseada em `HttpServletRequest` para que apenas usuários autenticados possam acessar a API.
- 🔒 **Criptografia de Senhas**: As senhas dos usuários são criptografadas utilizando a biblioteca BCrypt.


## 🛠️ Tecnologias Utilizadas

- ☕ **Java**: Linguagem principal utilizada para desenvolver a aplicação.
- 🍃 **Spring Boot**: Framework para facilitar o desenvolvimento da aplicação, incluindo o suporte a RESTful APIs.
- 🔒 **BCrypt**: Biblioteca utilizada para criptografar as senhas dos usuários.
- 🗄️ **H2 Database**: Banco de dados em memória utilizado para armazenar as informações de usuários e tarefas.
- ✨ **Lombok**: Biblioteca que reduz a verbosidade do código, gerando automaticamente getters, setters e outros métodos.
- 📦 **Maven**: Gerenciador de dependências e build da aplicação.


## Requisitos

- **JDK 17** ou superior
- **Maven 3.8.1** ou superior

## 🚀 Como Rodar o Projeto

1. Clone o repositório:
```bash
git clone https://github.com/joschonarth/java-todo-list
```

2. Acesse o diretório do projeto:
```bash
cd todo-list
```

3. Compile o projeto e baixe as dependências:
```bash
mvn clean install
```

4. Execute a aplicação:
```bash
mvn spring-boot:run
```

A aplicação estará disponível em `http://localhost:8080`.

## Endpoints da API

### Autenticação


* **POST** `/users/`: Registra um novo usuário.

    * Corpo da requisição:

    ```json
    {
        "name": "João Otávio",
        "username": "joschonarth",
        "password": "123456"
    }
    ```