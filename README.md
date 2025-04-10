# ICT0008 Advanced Programming Skills
com essas informacoes : Diagrama de Classes - Sistema de Biblioteca
Classe Book
Atributos:

title: string

author: string

isbn: string

available: bool

Métodos:

setBookDetails(t: string, a: string, i: string, avl: bool): void

displayBookDetails(): void

getISBN(): string

isAvailable(): bool

borrowBook(): void

returnBook(): void

Classe Library
Atributos:

books: vector<Book>

Métodos:

addBook(book: Book): void

findBook(isbn: string): Book*

borrowBook(isbn: string): void

returnBook(isbn: string): void

displayAllBooks(): void

Classe UserInterface
Métodos:

displayMenu(): void

handleUserInput(): void

start(): void

Este modelo permite a separação das responsabilidades:

A classe Book representa os livros individualmente.

A classe Library gerencia a coleção de livros e suas operações.

A classe UserInterface lida com a interação com o usuário. me de um diagrama de classes
