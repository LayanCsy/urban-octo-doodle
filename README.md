import java.io.IOException;
import java.util.ArrayList;

public class Borrow {

    private Book currentBook;
    private ArrayList<Book> borrowedBooks = new ArrayList<>();

    public Borrow() {
        this.borrowedBooks = new ArrayList<>();
    }

    public String borrowBook(Book currentBook) throws IOException {
        for (int i = 0; i <= 2; i++) {
            if (borrowedBooks.get(i) != null) {
                if (equals(borrowedBooks.get(i))) {
                    return "you have already borrowed " + currentBook.getBookName();
                } else {
                    return "you have reached maximum capacity";
                }
            } else {
                borrowedBooks.add(currentBook);
                currentBook.removeBook(currentBook.getBookName());
            }
        }
        return "you have borrowed this book successfully";
    }

    public String returnBook(Book currentBook) throws IOException {
        for (int i = 0; i <= 2; i++) {
            if (equals(borrowedBooks.get(i))) {
                borrowedBooks.remove(currentBook);
                currentBook.addBook(currentBook.getBookName());
                return "you have returned " + currentBook.getBookName() + "successfully";
            }
        }
        return "you didn't borrow " + currentBook.getBookName();
    }

    @Override
    public boolean equals(Object o) {
        return this.currentBook == o;
    }
}
