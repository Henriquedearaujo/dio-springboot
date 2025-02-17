# SpringBoot Fremework

# O que é Spring Boot?

Spring Boot é um framework para construção de aplicações Java baseado no projeto Spring. Ele facilita a criação de aplicações stand-alone, production-grade e Spring-based, com mínima configuração. Com Spring Boot, desenvolvedores podem iniciar um novo projeto rapidamente, sem a necessidade de configuração manual extensiva, permitindo maior produtividade.

## Vantagens do Spring Boot

- **Configuração Automática**: Spring Boot vem com configurações padrão que cobrem muitos cenários comuns, eliminando a necessidade de configurar manualmente muitos aspectos da aplicação.
- **Starters**: Dependências que agregam automaticamente todas as outras dependências necessárias para uma funcionalidade específica, simplificando a adição de bibliotecas ao projeto.
- **Standalone**: Permite a criação de aplicações standalone que podem ser executadas de forma independente, sem a necessidade de um servidor de aplicação separado.
- **Spring Boot Actuator**: Fornece monitoramento e gerenciamento da aplicação, expondo métricas, informações sobre o estado da aplicação, e endpoints de gerenciamento.
- **Facilidade de Testes**: Inclui várias bibliotecas de teste e suporte para testes integrados, permitindo que os desenvolvedores escrevam e executem testes de maneira simples e eficaz.

## Como Funciona o Spring Boot?

Spring Boot utiliza uma abordagem baseada em convenções para configurar automaticamente uma aplicação Spring, reduzindo a necessidade de configuração manual. Ele inclui uma série de "starters" que agrupam dependências comuns, facilitando a inclusão de novas funcionalidades na aplicação.

## Starters

Spring Boot introduziu o conceito de "Starters", que são dependências que agregam automaticamente todas as outras dependências necessárias para uma funcionalidade específica. Isso elimina a necessidade de adicionar manualmente cada dependência individual.

## Principais Starters

Alguns dos principais starters fornecidos pelo Spring Boot incluem:

- **spring-boot-starter-web**: Inclui dependências para construir aplicações web, incluindo RESTful.
- **spring-boot-starter-data-jpa**: Inclui Spring Data JPA com Hibernate.
- **spring-boot-starter-security**: Inclui Spring Security para autenticação e controle de acesso.
- **spring-boot-starter-thymeleaf**: Inclui Thymeleaf para templates de renderização de páginas web.
- **spring-boot-starter-test**: Inclui várias bibliotecas de teste, como JUnit, Hamcrest, e Mockito.
------------------------------------------------------------------------------------------------------------------
# Como Criar um Projeto Spring Boot

## Passos para Criar um Projeto Spring Boot

### 1. Usando Spring Initializr

Spring Initializr é uma ferramenta web que permite gerar rapidamente um projeto Spring Boot. Siga os passos abaixo:

1. Acesse [Spring Initializr](https://start.spring.io/).
2. Configure o projeto conforme necessário:
   - Escolha a **versão do Spring Boot**.
   - Selecione **Group** e **Artifact**.
   - Escolha a **versão do Java**.
   - Adicione as **dependências** que você precisa, como `spring-boot-starter-web`, `spring-boot-starter-data-jpa`, etc.
3. Clique em **"Generate"** para baixar o projeto como um arquivo ZIP.
4. Extraia o arquivo ZIP em seu diretório de trabalho.

### 2. Importar o Projeto em sua IDE

1. Abra sua IDE (por exemplo, IntelliJ IDEA, Eclipse ou VS Code).
2. Importe o projeto como um **Projeto Maven** ou **Projeto Gradle**, dependendo da escolha feita no Spring Initializr.
3. Aguarde a IDE baixar todas as dependências e configurar o ambiente.

-----------------------------------------------------------------------------------------------------------------

# IoC (Inversion of Control) e DI (Dependency Injection)

## IoC (Inversion of Control)

Inversion of Control (Inversão de Controle) é um princípio de design usado para reverter o fluxo de controle de uma aplicação. Em vez de o código da aplicação estar no controle total do fluxo, o controle é delegado a um framework ou container. Isso ajuda a criar aplicações que são mais modulares, testáveis e flexíveis.

### Explicação

**@Autowired:** A anotação @Autowired indica ao Spring que ele deve injetar a dependência fornecida. No exemplo, o Spring injeta uma instância de ClienteRepository ao criar uma instância de PedidoService.

**Construtor:** O uso de injeção via construtor permite que as dependências sejam passadas na criação da instância, promovendo a imutabilidade.

Essa abordagem com IoC e injeção de dependências melhora significativamente a modularidade e a flexibilidade do seu código.

Se precisar de mais alguma coisa ou tiver outras dúvidas, estou aqui para ajudar!


**Como Funciona:** O framework assume a responsabilidade de criar instâncias de classes e gerenciar suas dependências.

**Exemplo:** Em um aplicativo Spring, o contêiner Spring cria os objetos e injeta suas dependências. Isso contrasta com um cenário tradicional, onde cada classe é responsável por criar suas próprias dependências.

## DI (Dependency Injection)

**Definição:** DI é um padrão de projeto que implementa o princípio de IoC, fornecendo uma maneira de injetar dependências em uma classe em vez de permitir que a própria classe crie as dependências.

**Como Funciona:** As dependências são injetadas de fora da classe, geralmente por um framework ou container. Isso pode ser feito via construtores, métodos setters ou diretamente nos campos.

**Exemplo:** O Spring oferece suporte à injeção de dependências por meio de anotações como @Autowired.

## Resumo das Diferenças
**IoC** é um princípio geral de design que reverte o controle do fluxo de uma aplicação para um framework ou container.

**DI** é uma técnica específica para implementar IoC, injetando as dependências necessárias em uma classe de fora.

**Ambos os conceitos são utilizados para criar aplicações mais modulares, testáveis e fáceis de manter. IoC estabelece a base, enquanto DI é uma maneira prática de aplicar esse princípio.**

### Benefícios:
**Acoplamento Fraco:** Reduz a dependência direta entre os componentes.

**Manutenção:** Facilita a manutenção e a evolução do código.

**Testabilidade:** Permite a injeção de dependências mockadas para testes unitários.

-----------------------------------------------------------------------------------------------------------------
# Integração com Banco de Dados no Spring Boot
Spring Boot facilita muito a integração de aplicações Java com bancos de dados, proporcionando uma configuração simplificada e uma série de ferramentas poderosas para gerenciar a persistência de dados. Vamos explorar a integração com o banco de dados PostgreSQL como exemplo.

### Passos para a Integração

**Dependências do Projeto:**
Primeiro, você precisa adicionar as dependências necessárias no arquivo pom.xml (para Maven) ou build.gradle (para Gradle). Aqui estão algumas das dependências mais comuns:

````java
<!-- pom.xml -->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>
<dependency>
    <groupId>org.postgresql</groupId>
    <artifactId>postgresql</artifactId>
    <scope>runtime</scope>
</dependency>
````

### Configuração do Banco de Dados:

Configure as propriedades do banco de dados no arquivo application.properties ou application.yml. Aqui está um exemplo de configuração para um banco de dados PostgreSQL:

**application.properties**
````java
spring.datasource.url=jdbc:postgresql://localhost:5432/mydatabase
spring.datasource.username=postgres
spring.datasource.password=senha
spring.datasource.driver-class-name=org.postgresql.Driver
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect

````
### Entidade JPA:

Crie uma entidade JPA que representa uma tabela do banco de dados. Use a anotação **@Entity** para marcar a classe como uma entidade JPA.

````java
package com.exemplo.myproject.model;

import javax.persistence.Entity;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;
import javax.persistence.Id;

@Entity
public class Produto {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String codigo;
    private String nome;
    private int quantidade;

    // Getters e Setters
}
````
### Repositório JPA:

Crie um repositório JPA que permitirá executar operações CRUD (Create, Read, Update, Delete) na entidade.

````java
package com.exemplo.myproject.repository;

import org.springframework.data.jpa.repository.JpaRepository;
import com.exemplo.myproject.model.Produto;

public interface ProdutoRepository extends JpaRepository<Produto, Long> {
}
`
````

### Serviço e Controlador:

Crie um serviço e um controlador para gerenciar a lógica de negócios e as requisições HTTP, respectivamente.

````
package com.exemplo.myproject.service;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;
import com.exemplo.myproject.model.Produto;
import com.exemplo.myproject.repository.ProdutoRepository;

import java.util.List;

@Service
public class ProdutoService {
    @Autowired
    private ProdutoRepository produtoRepository;

    public List<Produto> findAll() {
        return produtoRepository.findAll();
    }

    public Produto save(Produto produto) {
        return produtoRepository.save(produto);
    }

    // Outros métodos de serviço
}
````
-----------------------------------------------------------------------------------------------------------------
````java
package com.exemplo.myproject.controller;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;
import com.exemplo.myproject.model.Produto;
import com.exemplo.myproject.service.ProdutoService;

import java.util.List;

@RestController
@RequestMapping("/produtos")
public class ProdutoController {
    @Autowired
    private ProdutoService produtoService;

    @GetMapping
    public List<Produto> findAll() {
        return produtoService.findAll();
    }

    @PostMapping
    public Produto save(@RequestBody Produto produto) {
        return produtoService.save(produto);
    }

    // Outros endpoints
}
````

### Benefícios

- **Configuração Simplificada:** Spring Boot oferece configurações automáticas que facilitam a configuração de conexões com bancos de dados.

- **Repositórios JPA:** Uso de interfaces como JpaRepository que simplificam as operações CRUD.

- **Produtividade:** Ferramentas e anotações que aceleram o desenvolvimento.

- **Testabilidade:** Integração fácil com frameworks de teste.

**Com esses passos você pode configurar e integrar um banco de dados PostgreSQL em sua aplicação Spring Boot, permitindo manipular dados de maneira eficiente e segura.**


