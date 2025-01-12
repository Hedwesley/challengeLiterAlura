# 📖LiterAlura ![Static Badge](https://img.shields.io/badge/CONCLU%C3%8DDO-%236DB33F?style=flat-square&color=%236DB33F)
📅Sunday, 19th 2025 - 📍São Luís, Brazil<br>
🌎[@Alura](https://www.alura.com.br/) [@One](https://www.oracle.com/br/)<br>
 
![Static Badge](https://img.shields.io/badge/SpringBoot-%236DB33F?style=for-the-badge&logo=springboot&labelColor=black)
![Static Badge](https://img.shields.io/badge/Postgresql-4169E1?style=for-the-badge&logo=postgresql&logoColor=white&labelColor=black)
![Static Badge](https://img.shields.io/badge/Javascript-%23F7DF1E?style=for-the-badge&logo=javascript&labelColor=black)

![LiterAlura](https://github.com/user-attachments/assets/1d249375-fdda-4422-8a0b-1fe7a51e5511)

## Descrição do Desafio
A aplicação deve conseguir:
- Listar livros consultados pelo seu `titulo` na base de dados, caso não haja. Deverá consultar na API da `Gutendex`
- Listar todos os livros da base de dados e mostrar uma breve estatística dos downloads de cada livro se estão acima ou abaixo da média
- Listar o top10 livros mais baixados com Média, Mínimo, Máximo e se o livro está acima ou abaixo da média
- Listar os livros de determinada língua
- Contar quantidade de livros de determinada língua
- Listar todos autores
- Listar os autores vivos em um determinado ano
- Encontrar um autor pelo seu nome

# Projeto de Gerenciamento de Livros e Autores

## 1. Configuração do Ambiente

- **Linguagem de Programação**: Java
- **Ferramenta de Gerenciamento de Projetos**: Maven
- **Versão do Spring Boot**: A versão utilizada no exemplo da aula.

### Dependências:
- **Spring Data JPA**: Facilita a persistência de dados.
- **Driver do PostgreSQL**: Para conectar ao banco de dados PostgreSQL.

## 2. Consumo da API Gutendex

O aplicativo utiliza a API Gutendex para:

- **Realizar a busca de livros por título**: O usuário pode inserir o título de um livro e a aplicação busca na API.
- **Obter informações do livro**: A API retorna dados como título, autor, idioma e número de downloads.

## 3. Persistência de Dados no Banco de Dados PostgreSQL

- **Criar Tabelas**: O aplicativo cria tabelas para armazenar dados dos livros, incluindo informações como título, autor, idioma e número de downloads.
- **Inserir Dados**: Os dados obtidos da API Gutendex são inseridos no banco de dados.

## 4. Interface do Usuário (Terminal)

O aplicativo oferece as seguintes opções no menu interativo:

1. **Buscar Livro pelo Título**: O usuário pode inserir o título de um livro, que será buscado na API Gutendex e registrado no banco de dados, caso não esteja previamente registrado.

2. **Listar Livros Registrados**: O usuário pode listar todos os livros armazenados no banco de dados.

3. **Listar Autores Registrados**: O usuário pode listar todos os autores dos livros armazenados.

4. **Listar Autores Vivos em um Determinado Ano**: O usuário pode inserir um ano e a aplicação lista todos os autores que estavam vivos naquele ano.

5. **Listar Livros em um Determinado Idioma**: O usuário pode inserir um idioma e a aplicação lista todos os livros disponíveis nesse idioma.
