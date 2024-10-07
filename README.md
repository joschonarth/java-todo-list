# 📝 To-Do List API

Esta é uma API de gerenciamento de tarefas (To-do List) desenvolvida em Java utilizando Spring Boot. A aplicação permite que os usuários criem contas, adicionem, visualizem, editem e excluam tarefas. Apenas o usuário que criou a tarefa pode editá-la ou excluí-la. Além disso, a aplicação utiliza autenticação de usuários e criptografia de senha com a biblioteca BCrypt.

## ⚙️ Funcionalidades

- 👤 **Criação de Usuários**: Permite criar novos usuários para utilizar a API.
- 📝 **Criação de Tarefas**: Usuários podem criar novas tarefas.
- ✏️ **Edição de Tarefas**: Apenas o usuário que criou a tarefa pode editá-la.
- 🗑️ **Exclusão de Tarefas**: Apenas o usuário que criou a tarefa pode excluí-la.
- 📋 **Listagem de Tarefas**: Usuários podem visualizar suas tarefas.
- 🔑 **Autenticação de Usuários**: Utiliza autenticação baseada em `HttpServletRequest` para que apenas usuários autenticados possam acessar a API.
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

### Usuários


* **POST** `/users/`: Registra um novo usuário.

    * Exemplo de corpo da requisição:

    ```json
    {
        "name": "João Otávio",
        "username": "joschonarth",
        "password": "123456"
    }
    ```

    * Exemplo de retorno:

    ```json
    {
        "id": "99265598-642a-4b07-8794-b307384a1c3d",
        "username": "joschonarth",
        "name": "João Otávio",
        "password": "$2a$12$0YOjfRcD8ET9hW410NT68eBU/cUM14ZQEDNSoTEtzjTSVJwnJQxIi",
        "createdAt": "2024-10-06T22:05:54.924557"
    }
    ```

### Tarefas

* **POST** `/tasks/`: Cria uma nova tarefa.

    * **Authorization**: Basic Auth (digite o username e o password informados na criação do usuário).
    * Exemplo de corpo da requisição:

    ```json
    {
        "description": "Aprender mais sobre Spring Boot",
        "title": "Estudar Spring Boot",
        "priority": "Alta",
        "startAt": "2024-10-07T15:00",
        "endAt": "2024-10-08T10:00"
    }
    ```

    * Exemplo de retorno:

    ```json
    {
        "id": "f8f25626-41c2-4188-b0a6-6a22e910adee",
        "description": "Aprender mais sobre Spring Boot",
        "title": "Estudar Spring Boot",
        "startAt": "2024-10-07T15:00:00",
        "endAt": "2024-10-08T10:00:00",
        "priority": "Alta",
        "idUser": "99265598-642a-4b07-8794-b307384a1c3d",
        "createdAt": "2024-10-06T22:06:33.403349"
    }
    ```

* **GET** `/tasks/`: Lista todas as tarefas.

    * **Authorization**: Basic Auth (digite o username e o password informados na criação do usuário).
    * Exemplo de retorno:
    
    ```json
    [
        {
            "id": "f8f25626-41c2-4188-b0a6-6a22e910adee",
            "description": "Aprender mais sobre Spring Boot",
            "title": "Estudar Spring Boot",
            "startAt": "2024-10-07T15:00:00",
            "endAt": "2024-10-08T10:00:00",
            "priority": "Alta",
            "idUser": "99265598-642a-4b07-8794-b307384a1c3d",
            "createdAt": "2024-10-06T22:06:33.403349"
        },
        {
            "id": "f410a093-1037-4de0-a980-45fe7491e7e8",
            "description": "Aprender mais sobre Java",
            "title": "Estudar Java",
            "startAt": "2024-10-07T15:00:00",
            "endAt": "2024-10-08T10:00:00",
            "priority": "Alta",
            "idUser": "99265598-642a-4b07-8794-b307384a1c3d",
            "createdAt": "2024-10-06T22:14:17.621538"
        }
    ]
    ```

* **PUT** `/tasks/{id}`: Atualiza uma tarefa existente, passando o `id` da tarefa como parâmetro.

    * **Authorization**: Basic Auth (digite o username e o password informados na criação do usuário).
    
    * **Exemplo de URL**: `http://localhost:8080/tasks/f8f25626-41c2-4188-b0a6-6a22e910adee`
    
    * Exemplo de corpo da requisição:

    ```json
    {
        "title": "Estudar Spring Boot Avançado"
    }
    ```

    * Exemplo de retorno:

    ```json
    {
        "id": "f8f25626-41c2-4188-b0a6-6a22e910adee",
        "description": "Aprender mais sobre Spring Boot",
        "title": "Estudar Spring Boot Avançado",
        "startAt": "2024-10-07T15:00:00",
        "endAt": "2024-10-08T10:00:00",
        "priority": "Alta",
        "idUser": "99265598-642a-4b07-8794-b307384a1c3d",
        "createdAt": "2024-10-06T22:06:33.403349"
    }
    ```

* **DELETE** `/tasks/{id}`: Exclui uma tarefa, passando o `id` da tarefa como parâmetro.

    * **Authorization**: Basic Auth (digite o username e o password informados na criação do usuário).
    
    * **Exemplo de URL**: `http://localhost:8080/tasks/f410a093-1037-4de0-a980-45fe7491e7e8`


## 🗄️ Banco de Dados

Esta aplicação utiliza o banco de dados H2 em memória. Para acessar o console do H2, após rodar a aplicação, acesse:

* URL: http://localhost:8080/h2-console
* JDBC URL: jdbc:h2:mem:todolist
* Username: admin
* Password: admin

## 🔒 Segurança e Autenticação

As senhas dos usuários são armazenadas de forma segura utilizando a biblioteca BCrypt, garantindo que elas sejam devidamente criptografadas. Além disso, a API utiliza o `HttpServletRequest` para autenticação, permitindo que apenas usuários autenticados possam acessar suas respectivas tarefas.

## 📦 Dependências do Maven

Aqui estão as principais dependências utilizadas no projeto:

```xml
    <dependencies>

        <!-- DevTools para recarregamento automático durante o desenvolvimento -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-devtools</artifactId>
            <optional>true</optional>
        </dependency>

        <!-- Web Starter para criar APIs RESTful -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <!-- Test Starter para testes unitários e de integração -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>

        <!-- JPA Starter para interação com o banco de dados -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-data-jpa</artifactId>
        </dependency>

        <!-- Banco de dados H2 para desenvolvimento e testes em memória -->
        <dependency>
            <groupId>com.h2database</groupId>
            <artifactId>h2</artifactId>
            <scope>runtime</scope>
        </dependency>

        <!-- BCrypt para criptografar senhas de usuários -->
        <dependency>
            <groupId>org.springframework.security</groupId>
            <artifactId>spring-security-crypto</artifactId>
        </dependency>

        <!-- Lombok para reduzir a verbosidade do código -->
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <scope>provided</scope>
        </dependency>

    </dependencies>
```