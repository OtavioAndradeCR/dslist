# DSList — API de Catálogo e Organização de Jogos

[![Java CI](https://github.com/OtavioAndradeCR/dslist/actions/workflows/maven.yml/badge.svg)](https://github.com/OtavioAndradeCR/dslist/actions/workflows/maven.yml)

API REST desenvolvida com **Java 21 e Spring Boot** para consultar jogos, visualizar listas temáticas e reorganizar a posição dos jogos dentro de cada lista.

O projeto demonstra desenvolvimento backend com Spring Boot, persistência relacional, consultas personalizadas com Spring Data JPA e organização em camadas.

## Funcionalidades

- Consultar o catálogo de jogos.
- Consultar os detalhes de um jogo pelo identificador.
- Listar as coleções disponíveis.
- Consultar os jogos de uma coleção.
- Reordenar jogos dentro de uma coleção.

## Tecnologias

- Java 21
- Spring Boot 3.5
- Spring Web
- Spring Data JPA / Hibernate
- PostgreSQL
- H2 Database para testes
- Maven

## Organização do código

O projeto utiliza uma arquitetura em camadas, organizada por responsabilidade:

| Pacote | Responsabilidade |
| --- | --- |
| `controllers` | Exposição dos endpoints REST |
| `services` | Regras de aplicação e transações |
| `repositories` | Persistência e consultas com Spring Data JPA |
| `entities` | Entidades mapeadas para o banco de dados |
| `dto` | Objetos de transferência de dados |
| `projections` | Projeções utilizadas em consultas específicas |
| `config` | Configurações da aplicação, como CORS |

## Requisitos

- JDK 21
- Git

O Maven Wrapper (`mvnw` / `mvnw.cmd`) já está incluído no repositório. Não é necessário instalar o Maven globalmente.

## Como executar

Clone o repositório:

```bash
git clone https://github.com/OtavioAndradeCR/dslist.git
cd dslist
```

### Executar com o perfil de teste

Por padrão, a aplicação utiliza o perfil `test`, configurado com banco H2 em memória. Para iniciar:

Linux / macOS:

```bash
bash ./mvnw spring-boot:run
```

Windows:

```powershell
.\mvnw.cmd spring-boot:run
```

### Executar com PostgreSQL (perfil dev)

Crie um banco PostgreSQL chamado `dslist` e configure as variáveis de ambiente:

| Variável | Valor de exemplo |
| --- | --- |
| `DB_URL` | `jdbc:postgresql://localhost:5433/dslist` |
| `DB_USERNAME` | usuário do PostgreSQL |
| `DB_PASSWORD` | senha do PostgreSQL |

O perfil de desenvolvimento usa PostgreSQL na porta `5433` por padrão. A URL pode ser sobrescrita por `DB_URL`.

Linux / macOS:

```bash
export APP_PROFILE=dev
export DB_USERNAME=postgres
export DB_PASSWORD=sua_senha
bash ./mvnw spring-boot:run
```

Windows PowerShell:

```powershell
$env:APP_PROFILE = "dev"
$env:DB_USERNAME = "postgres"
$env:DB_PASSWORD = "sua_senha"
.\mvnw.cmd spring-boot:run
```

Não versione senhas ou credenciais reais. O perfil `prod` também recebe URL, usuário e senha pelas variáveis `DB_URL`, `DB_USERNAME` e `DB_PASSWORD`.

A aplicação inicia, por padrão, em:

```
http://localhost:8080
```

## Endpoints

| Método | Endpoint | Descrição |
| --- | --- | --- |
| GET | `/games` | Lista os jogos do catálogo |
| GET | `/games/{id}` | Busca os detalhes de um jogo |
| GET | `/lists` | Lista as coleções |
| GET | `/lists/{listId}/games` | Lista os jogos de uma coleção |
| POST | `/lists/{listId}/replacement` | Altera a ordem dos jogos da coleção |

### Exemplo: consultar jogos

```bash
curl http://localhost:8080/games
```

### Exemplo: consultar jogos de uma lista

```bash
curl http://localhost:8080/lists/1/games
```

### Exemplo: reorganizar jogos

O endpoint recebe os índices de origem e destino no corpo da requisição:

```bash
curl -X POST http://localhost:8080/lists/1/replacement \
  -H "Content-Type: application/json" \
  -d '{"sourceIndex": 0, "destinationIndex": 2}'
```

## Testes

Execute a suíte automatizada com:

Linux / macOS:

```bash
bash ./mvnw --batch-mode verify
```

Windows:

```powershell
.\mvnw.cmd --batch-mode verify
```

O teste de contexto valida a inicialização da aplicação com o perfil de teste e o banco H2.

O GitHub Actions executa o build e os testes automaticamente em pushes e pull requests direcionados à branch `main`.

---

Desenvolvido como projeto de estudo e portfólio para demonstrar práticas de desenvolvimento de APIs REST com Java e Spring Boot.
