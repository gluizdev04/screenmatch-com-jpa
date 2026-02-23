# Screenmatch (API REST & Persistência de Dados)

Projeto desenvolvido e evoluído durante as formações de **"Java e Spring Boot"** da Alura (Cursos: *Persistência de Dados* e *Criando a sua primeira API*). 

O objetivo desta aplicação foi construir um sistema completo de gerenciamento de um catálogo de séries. O projeto nasceu como uma aplicação de linha de comando, evoluiu para persistir dados em um banco de dados relacional (**PostgreSQL**) e, em sua versão final, foi transformado em uma **API RESTful** estruturada para servir dados a uma aplicação Front-end.

## Sobre o Projeto
O **Screenmatch** consome a API externa (**OMDB**) para buscar dados reais de séries e temporadas, armazena essas informações em um banco **PostgreSQL** e expõe esses dados através de **endpoints HTTP**. O projeto aplica conceitos fundamentais de backend moderno e arquitetura de software corporativa.

## Funcionalidades

### 1. API REST (Endpoints Expostos)
A aplicação fornece rotas HTTP para o Front-end consumir:
* **`GET /series`**: Lista todas as séries cadastradas.
* **`GET /series/top5`**: Retorna as 5 séries com melhor avaliação.
* **`GET /series/lancamentos`**: Retorna as 5 séries com os episódios mais recentes adicionados.
* **`GET /series/{id}`**: Detalhes de uma série específica.
* **`GET /series/{id}/temporadas/todas`**: Lista o catálogo completo de episódios de uma série.
* **`GET /series/{id}/temporadas/{temporada}`**: Busca episódios de uma temporada específica.
* **`GET /series/categoria/{genero}`**: Filtra séries por gênero literário/cinematográfico.

### 2. Persistência e Modelagem (Banco de Dados)
* **Consumo de API Externa:** Busca e desserialização de dados da OMDB API.
* **Relacionamentos:** Modelagem de entidades com relacionamento **1:N** (Uma Série tem Vários Episódios).
* **Consultas Avançadas:** Consultas personalizadas e otimizadas utilizando **JPQL** (ex: `GROUP BY`, `JOIN`) e **Derived Queries**.

## Tecnologias Utilizadas
* **Java 21**
* **Spring Boot**
* **Spring Web** (Criação de rotas e REST Controllers)
* **Spring Data JPA** (Hibernate)
* **Spring Boot DevTools** (Live Reload para agilizar o desenvolvimento)
* **PostgreSQL** (Banco de Dados)
* **Jackson** (Serialização e Desserialização de JSON)
* **Maven**

## Aprendizados e Padrões Aplicados
Durante o desenvolvimento, foram praticados conceitos essenciais do mercado:
* **Padrão MVC e Arquitetura em Camadas:** Separação clara de responsabilidades entre **`Controller`** (Rotas HTTP), **`Service`** (Regras de negócio) e **`Repository`** (Banco de dados).
* **Padrão DTO (Data Transfer Object):** Utilização de *Records* para formatar e proteger os dados enviados na resposta da API, ocultando as entidades originais do banco de dados.
* **Configuração de CORS:** Liberação e configuração de acesso (`WebMvcConfigurer`) para permitir que o Front-end consuma a API de forma segura.
* **Mapeamento Objeto-Relacional (ORM):** Uso de anotações `@Entity`, `@OneToMany`, `@ManyToOne` e compreensão de `EAGER` vs `LAZY` loading.
* **Tratamento de Dados:** Uso de Java Streams, Lambdas e otimização de consultas no banco vs processamento em memória.

## Como rodar este projeto

**Pré-requisitos:** Ter **Java 17+** e **PostgreSQL** instalados na máquina.

1. **Configuração do Banco de Dados:**
   Crie um banco de dados no PostgreSQL com o nome `screenmatch_jpa`.
   As credenciais de acesso devem ser configuradas no arquivo `application.properties` ou injetadas via variáveis de ambiente.
2. **Chave da API OMDB:**
   Insira sua chave da OMDB nas variáveis de ambiente do seu sistema.
3. **Execução:**
   * Clone este repositório.
   * Rode a classe `ScreenmatchApplication` (A aplicação irá subir um servidor Tomcat embutido na porta `8080`).
   * Acesse `http://localhost:8080/series` no seu navegador ou Postman para testar a API.
  
## Como rodar e integrar com o Front-end

Para visualizar esta API funcionando na prática através de uma interface gráfica, você pode utilizar o projeto Front-end base do curso.

1. Faça o download ou clone do repositório Front-end: **https://github.com/alura-cursos/3356-java-web-front**
2. Certifique-se de que esta aplicação Back-end (Spring Boot) esteja rodando na porta `8080`.
3. Abra a pasta do Front-end em um editor de código (como VS Code).
4. Utilize a extensão **Live Server** para rodar o arquivo `index.html` (ou simplesmente abra o arquivo `index.html` diretamente no seu navegador).
5. O Front-end irá se comunicar automaticamente com a sua API local e exibir o catálogo de séries!
