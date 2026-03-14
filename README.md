# Demo

Aplicacao Spring Boot com API simples de CRUD de usuarios usando Spring Web MVC, Spring Data JPA e banco H2 em memoria.

## Pre-requisitos

- Java JDK 25
- Maven Wrapper do projeto (`mvnw.cmd` no Windows ou `./mvnw` no Linux/macOS)

## Observacao sobre Java

O projeto esta configurado no [`pom.xml`](/C:/Users/johne/OneDrive/Documentos/matrix/projects/demo/pom.xml) com:

```xml
<java.version>25</java.version>
```

Se a IDE estiver usando Java 21 ou inferior, o build vai falhar. Nesse caso:

- instale um JDK 25 e associe ao projeto na IDE, ou
- altere o `java.version` do `pom.xml` para uma versao suportada pelo JDK instalado

## Como iniciar

No Windows:

```powershell
.\mvnw.cmd spring-boot:run
```

No Linux/macOS:

```bash
./mvnw spring-boot:run
```

A aplicacao sobe em:

```text
http://localhost:8081
```

## Como testar

Executar todos os testes:

No Windows:

```powershell
.\mvnw.cmd test
```

No Linux/macOS:

```bash
./mvnw test
```

Hoje o projeto possui um teste basico de contexto em [`src/test/java/com/example/demo/DemoApplicationTests.java`](/C:/Users/johne/OneDrive/Documentos/matrix/projects/demo/src/test/java/com/example/demo/DemoApplicationTests.java).

## Banco H2

Configuracao em [`src/main/resources/application.properties`](/C:/Users/johne/OneDrive/Documentos/matrix/projects/demo/src/main/resources/application.properties):

- URL: `jdbc:h2:mem:usuarios`
- usuario: `CRUD`
- senha: `JOHN`
- console H2: `http://localhost:8081/h2-console`

## Endpoints

Controller principal em [`src/main/java/com/example/demo/controller/UsuarioController.java`](/C:/Users/johne/OneDrive/Documentos/matrix/projects/demo/src/main/java/com/example/demo/controller/UsuarioController.java).

### Criar usuario

```http
POST /usuario
Content-Type: application/json
```

Exemplo:

```json
{
  "email": "john@example.com",
  "nome": "John"
}
```

### Buscar usuario por email

```http
GET /usuario?email=john@example.com
```

### Atualizar usuario por id

```http
PUT /usuario?id=1
Content-Type: application/json
```

Exemplo:

```json
{
  "nome": "John Atualizado"
}
```

### Deletar usuario por email

```http
DELETE /usuario?email=john@example.com
```

## Exemplo com curl

Criar:

```bash
curl -X POST http://localhost:8081/usuario ^
  -H "Content-Type: application/json" ^
  -d "{\"email\":\"john@example.com\",\"nome\":\"John\"}"
```

Buscar:

```bash
curl "http://localhost:8081/usuario?email=john@example.com"
```

Atualizar:

```bash
curl -X PUT "http://localhost:8081/usuario?id=1" ^
  -H "Content-Type: application/json" ^
  -d "{\"nome\":\"John Atualizado\"}"
```

Deletar:

```bash
curl -X DELETE "http://localhost:8081/usuario?email=john@example.com"
```
