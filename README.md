#  Screenmatch (Versão com Persistência)

Projeto desenvolvido durante a formação **"Java e Spring Boot"** da Alura.
O objetivo principal foi evoluir a aplicação de linha de comando para persistir dados de séries e episódios em um banco de dados relacional, saindo do armazenamento em memória para o uso profissional de **Spring Data JPA**.

##  Sobre o Projeto

O **Screenmatch** é uma aplicação que gerencia um catálogo de séries. Ela consome a API externa (OMDB) para buscar dados reais de séries e temporadas, e agora armazena essas informações em um banco **PostgreSQL**.

**Este repositório contém o código desenvolvido acompanhando as aulas, onde foram aplicados conceitos fundamentais de backend moderno.**

##  Funcionalidades

- **Consumo de API:** Busca dados de séries na OMDB API.
- **Persistência de Dados:** Salva séries e episódios no banco de dados PostgreSQL.
- **Relacionamentos:** Modelagem de entidades com relacionamento 1:N (Uma Série tem Vários Episódios).
- **Consultas Avançadas:**
  - Busca de séries por título, ator ou gênero.
  - Filtragem de "Top 5 Episódios" por série.
  - Consultas personalizadas utilizando **JPQL** e **Derived Queries**.

##  Tecnologias Utilizadas

- **Java 21**
- **Spring Boot 4**
- **Spring Data JPA** (Hibernate)
- **PostgreSQL** (Driver e Banco de Dados)
- **Jackson** (Deserialização de dados JSON)
- **Maven**

##  Aprendizados

Durante o desenvolvimento deste projeto, foram praticados conceitos como:
- Mapeamento Objeto-Relacional (ORM) com anotações `@Entity`, `@OneToMany`, `@ManyToOne`.
- Diferença entre `EAGER` e `LAZY` loading.
- Criação de interface `Repository` e injeção de dependência.
- Tratamento de dados com Java Streams e Lambdas.

##  Como rodar este projeto

1. **Pré-requisitos:** Ter Java 17+ e PostgreSQL instalados.
2. **Configuração:**
   - Crie um banco de dados no Postgres com o nome `screenmatch_jpa` (ou ajuste no `application.properties`).
   - Insira sua chave da API OMDB nas variáveis de ambiente.
3. **Execução:**
   - Clone o repositório.
   - Execute a classe `ScreenmatchApplicationSemWeb`.

---
<sub>Projeto de estudo desenvolvido por Luiz Gustavo do Carmo Silva no curso da Alura.</sub>
