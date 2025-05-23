#include <iostream>
#include <string>
#include <vector>
#include <algorithm>

class Book {
private:
    std::string title;
    std::string author;
    std::string isbn;
    bool available;

public:

    Book(std::string t, std::string a, std::string i, bool av) 
        : title(t), author(a), isbn(i), available(av) {}

    std::string getTitle() const { return title; }
    std::string getAuthor() const { return author; }
    std::string getISBN() const { return isbn; }
    bool isAvailable() const { return available; }

    void displayDetails() const {
        std::cout << " Título: " << title << "\n"
                  << "  Autor: " << author << "\n"
                  << " ISBN: " << isbn << "\n"
                  << " Status: " << (available ? "Disponível" : "Emprestado") 
                  << "\n\n";
    }
};

bool compareByTitle(const Book &a, const Book &b) {
    return a.getTitle() < b.getTitle();
}

int main() {
    std::cout << " TESTE 1: Correct book information initialisation\n";
    Book book1("Freakonomics", "Steven D. Levitt & Stephen J. Dubner", "006073132X", true);
    Book book2("O Andar do Bêbado", "Leonard Mlodinow", "8535916814", false);
    Book book3("A Riqueza das Nações", "Adam Smith", "8572329226", true);

    book1.displayDetails();
    book2.displayDetails();
    book3.displayDetails();

    std::cout << " TESTE 2: Incorrect book information initialisation\n";
    try {
        Book invalidBook1("", "Autor Genérico", "123ABC", true);
        std::cout << "⚠ ERRO: Livro inválido criado (título vazio)\n";
    } catch (...) {
        std::cout << " Capturado livro inválido (título vazio)\n";
    }

    try {
        Book invalidBook2("Título Válido", "", "9781234567890", false);
        std::cout << " ERRO: Livro inválido criado (autor vazio)\n";
    } catch (...) {
        std::cout << " Capturado livro inválido (autor vazio)\n";
    }

    try {
        Book invalidBook3("Outro Título", "Outro Autor", "INVALIDISBN", true);
        std::cout << "ERRO: Livro inválido criado (ISBN inválido)\n";
    } catch (...) {
        std::cout << " Capturado livro inválido (ISBN inválido)\n";
    }

    std::cout << "TESTE 3: ORDENANDO OS LIVROS ";
    std::vector<Book> books = {book2, book1, book3}; // ordem mista

    std::sort(books.begin(), books.end(), compareByTitle);

    std::cout << "Livros ordenados por título:\n";
    for (const auto &book : books) {
        std::cout << "- " << book.getTitle() << "\n";
    }

    return 0;
}









