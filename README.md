[![Build Status](https://app.travis-ci.com/sandromendes/DockerToAWSWithJava.svg?branch=main)](https://app.travis-ci.com/sandromendes/DockerToAWSWithJava)

# Aplicação Java 11 com Spring Boot, MySQL, Docker e Travis CI

Este é um exemplo de aplicação Java 11 com Spring Boot que utiliza um banco de dados MySQL, Docker para contêinerização da aplicação e do banco de dados, e integração contínua com Travis CI.

## Requisitos

- Java 11
- Docker
- MySQL
- Maven

## Configuração do MySQL

Certifique-se de que o MySQL está instalado e em execução na sua máquina. Você pode configurar as credenciais e o banco de dados no arquivo `application.properties`.

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/nome_do_banco_de_dados
spring.datasource.username=seu_usuario
spring.datasource.password=sua_senha
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.jpa.hibernate.ddl-auto=update
```

## Executando a aplicação

Para executar a aplicação localmente, você pode usar o Maven:

```bash
mvn spring-boot:run
```

A aplicação estará acessível em `http://localhost:8080`.

## Docker

Este projeto também pode ser executado em um contêiner Docker. Certifique-se de ter o Docker instalado na sua máquina.

### Construindo a imagem Docker

```bash
docker build -t nome_da_imagem .
```

### Executando o contêiner Docker

```bash
docker run -p 8080:8080 nome_da_imagem
```

## Integração Contínua com Travis CI

Este projeto está configurado para integração contínua com Travis CI. Qualquer push para o repositório desencadeará automaticamente o build e os testes no Travis CI.

Para configurar o Travis CI para seu próprio repositório, você precisará de uma conta no Travis CI e de um arquivo de configuração `.travis.yml` na raiz do seu projeto.

Exemplo de `.travis.yml`:

```yaml
language: java
jdk:
  - openjdk11
services:
  - mysql
before_install:
  - mysql -e 'CREATE DATABASE nome_do_banco_de_dados;'
```

## Contribuindo

Sinta-se à vontade para contribuir para este projeto abrindo novas issues ou enviando pull requests!
