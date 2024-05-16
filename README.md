import java.io.IOException;
import java.util.ArrayList;

public class Borrow {

    private Book currentBook;
    private ArrayList<Book> borrowedBooks = new ArrayList<>();

    public Borrow() {
        this.borrowedBooks = new ArrayList<>();
    }

    // to borrow book
    public String borrowBook(Book currentBook) throws IOException {
        //to check if the user iligable to borrow 
        for (int i = 0; i <= 2; i++) {
            if (borrowedBooks.get(i) != null) {
                if (equals(borrowedBooks.get(i))) {
                    return "you have already borrowed " + currentBook.getBookName() + ".";
                }
            } else {
                borrowedBooks.add(currentBook);
                currentBook.removeBook(currentBook.getBookName());
                return "you have borrowed " + currentBook.getBookName() + " successfully.";
            }
        }//end for loop
        return "you can't borrow " + currentBook.getBookName() + "\nyou have reached maximum capacity.";
    }//end borrowBook

    //to return book
    public String returnBook(Book currentBook) throws IOException {
        //to check if the user borrowed the book
        for (int i = 0; i <= 2; i++) {
            if (equals(borrowedBooks.get(i))) {
                borrowedBooks.remove(currentBook);
                currentBook.addBook(currentBook.getBookName());
                return "you have returned " + currentBook.getBookName() + " successfully.";
            }
        }//end for loop
        return "you didn't borrow " + currentBook.getBookName() + ".";
    }//end returnBook

    @Override
    public boolean equals(Object o) {
        return this.currentBook == o;
    }
}//end Borrow
