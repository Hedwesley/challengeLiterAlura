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

Este projeto gerencia livros e autores em um banco de dados, permitindo o cadastro de livros. Utilizei a API [Gutendex](https://gutendex.com/), para obter dados dos livros.


## Funcionalidades

- Cadastro de livros e autores
- Verificação de existência de livros antes do cadastro
- Relacionamento bidirecional entre livros e autores
- Listar os autores vivos em um determinado ano
- Listar todos autores
- Pesquisa de livros por título
- Listar os livros de um determinado idioma



## Método `save(Book book, Author author)`
Este é o método central para associar livros e autores no banco de dados. Ele realiza a verificação de duplicação antes de salvar um livro e garante a associação bidirecional entre livros e autores. As operações realizadas são:

- **Verificação do livro existente**: Antes de salvar, o método verifica se o livro já está cadastrado no banco.
- **Verificação do autor existente**: Se o autor não estiver cadastrado, o autor é salvo junto com o livro, estabelecendo a relação entre eles.
- **Relacionamento bidirecional**: O método adiciona o livro à lista de livros do autor, garantindo a associação bidirecional.
- **Associação do livro a autor já existente**: Caso o autor já esteja cadastrado no banco, o livro é simplesmente associado a esse autor, sem duplicar o autor no banco.
### Código do Método `save`:

```java
private void save(Book book, Author author) {
    Optional<Book> bookFound = repository.findByTitle(book.getTitle());
    bookFound.ifPresentOrElse(
            b -> System.out.println("Livro já cadastrado tente outro"),
            () -> {
                Author authorToSave = repository.findByNameContainingIgnoreCase(author.getName())
                        .orElse(author);
                authorToSave.addBook(book);
                repository.save(authorToSave);
            }
    );
}
```
### Explicação

- **`findByTitle()`**: Verifica se o livro já está registrado no banco.
- **`findByNameContainingIgnoreCase()`**: Verifica se o autor já está no banco, ignorando diferenças de maiúsculas/minúsculas no nome.
- **`orElse(author)`**: Se o autor não for encontrado, o próprio autor passado como parâmetro é usado.
- **`addBook()`**: O livro é adicionado à lista de livros do autor, estabelecendo o relacionamento bidirecional.
- **`repository.save()`**: O autor é salvo (ou atualizado) no banco, com o livro já associado.
