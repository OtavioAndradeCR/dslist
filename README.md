# DSList – API de Catálogo de Jogos

## 📌 Visão Geral

O **DSList** é uma **API REST desenvolvida em Java com Spring Boot** para gerenciamento e listagem de jogos organizados por listas. O projeto permite consultar jogos, visualizar listas disponíveis e obter os jogos associados a cada lista, mantendo uma ordenação personalizada.

Este projeto foi desenvolvido com foco em **boas práticas de backend**, arquitetura em camadas e organização de código, sendo ideal para demonstração técnica em **portfólio profissional**.

---

## 🎯 Objetivo do Projeto

* Expor uma API REST para listagem de jogos
* Demonstrar uso de Spring Boot, JPA e arquitetura em camadas
* Aplicar boas práticas como DTOs, Services e Repositories
* Servir como projeto de estudo e portfólio para recrutadores

---

## 🛠️ Tecnologias Utilizadas

* **Java**
* **Spring Boot**
* **Spring Data JPA**
* **Hibernate**
* **Banco de Dados H2 / PostgreSQL** (dependendo do perfil)
* **Maven**
* **API REST**

---

## 🧱 Arquitetura

O projeto segue o padrão de **arquitetura em camadas**:

* **Controller** – Camada de entrada (API REST)
* **Service** – Regras de negócio
* **Repository** – Acesso a dados (JPA)
* **DTOs** – Transporte de dados entre camadas
* **Entities** – Mapeamento das tabelas do banco

Essa separação garante melhor manutenção, legibilidade e escalabilidade do código.

---

## ▶️ Como Executar o Projeto

### Pré-requisitos

* Java 17+
* Maven

### Passos

```bash
# Clonar o repositório
git clone https://github.com/OtavioAndradeCR/dslist.git

# Acessar a pasta do projeto
cd dslist

# Executar a aplicação
mvn spring-boot:run
```

A aplicação estará disponível em:

```
http://localhost:8080
```

---

## 📡 Endpoints Principais

### 🔹 Listar todos os jogos

```
GET /games
```

### 🔹 Buscar jogo por ID

```
GET /games/{id}
```

### 🔹 Listar todas as listas de jogos

```
GET /lists
```

### 🔹 Listar jogos por lista

```
GET /lists/{listId}/games
```

---

## 🧪 Exemplos de Uso (curl)

```bash
curl http://localhost:8080/games
```

```bash
curl http://localhost:8080/lists
```

```bash
curl http://localhost:8080/lists/1/games
```

---

## 🧩 Diferenciais Técnicos

* Uso de **DTOs** para controle de exposição de dados
* Organização clara de pacotes
* Separação de responsabilidades
* Código limpo e fácil de evoluir

---

## 📈 Possíveis Evoluções

* Autenticação e autorização (Spring Security + JWT)
* Paginação e filtros
* Deploy em nuvem (Azure, AWS ou Railway)
* Documentação com Swagger/OpenAPI
