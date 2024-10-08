    # Lab-1-POO
    Laboratorul 1 la POO
    
    
    // --------------------------------
    // --- Interfata pentru Library ---
    // --------------------------------
    
    package Lab_0;
    
    public interface LibraryInterface {
        void addElement();
        void deleteElement();
        void printAllElements();
    }
    
    
    
    // ----------------------
    // --- Clasa Librarie ---
    // ----------------------
    
    package Lab_0;
    import java.util.ArrayList;
    import java.util.Scanner;
    
    public class Library implements LibraryInterface{
        Scanner sc = new Scanner(System.in);
        ArrayList<Book> libraryQueue = new ArrayList<>();
    
        // 1.Adaugam cartea
        @Override
        public void addElement() {
            Book objectBook = new Book("Autor", "Titlul", 0);
    
            System.out.println("Introduceti numele autorului: ");
            String userAuthor = sc.nextLine();
            objectBook.setAuthor(userAuthor);
    
            System.out.println("Introduceti titlul: ");
            String userTitle = sc.nextLine();
            objectBook.setTitle(userTitle);
    
            System.out.println("Introduceti ISBN: ");
            long userISBN = sc.nextLong();
            objectBook.setISBN(userISBN);
            sc.nextLine();
    
            libraryQueue.add(objectBook);
    
            System.out.println("Succes: Cartea a fost adaugata.");
        }
    
    
        // 2.Stergeam cartea
        @Override
        public void deleteElement() {
            libraryQueue.remove(0);
            System.out.println("Succes: Cartea a fost stearsa.");
        }
    
    
        // 3.Printam toata biblioteca
        @Override
        public void printAllElements() {
            if(libraryQueue.size() == 0){
                System.out.println("\nError: Biblioteca este goala.\n");
            }
    
            int bookCount = 1;
            for(Book item : libraryQueue){
                System.out.println("\nCartea nr:" + bookCount);
                System.out.println(item);
                bookCount++;
            }
        }
    }
    
    
    
    
    // -------------------
    // --- Clasa Carte ---
    // -------------------
    
    package Lab_0;
    
    public class Book {
        private String author;
        private String title;
        private long ISBN;
    
        // Setteri si getteri
        public String getAuthor() {
            return author;
        }
    
        public void setAuthor(String author) {
            this.author = author;
        }
    
        public String getTitle() {
            return title;
        }
    
        public void setTitle(String title) {
            this.title = title;
        }
    
        public long getISBN() {
            return ISBN;
        }
    
        public void setISBN(long ISBN) {
            this.ISBN = ISBN;
        }
    
        // Lego Constructor
        public Book(String author, String title, long ISBN){
            this.author = author;
            this.title = title;
            this.ISBN = ISBN;
        }
    
    
        // Din Object in String pentru printare
        @Override
        public String toString() {
            return "Author: " + getAuthor() + "\nTitle: " + getTitle() + "\nISBN: " + getISBN();
        }
    }
    
    
    
    
    // ------------
    // --- Main ---
    // ------------
    
    package Lab_0;

    import java.util.Scanner;

    public class Main {
    public static void main(String[] args) {
        Library library = new Library();
        Scanner sc = new Scanner(System.in);
        int userInput;

        do {
            System.out.println("\nAlegeti optiunea: ");
            System.out.println("1. Adaugarea cartii");
            System.out.println("2. Stergerea cartii");
            System.out.println("3. Printarea bibliotecii\n");

            userInput = sc.nextInt();

            switch (userInput) {
                case 1 -> library.addElement();
                case 2 -> library.deleteElement();
                case 3 -> library.printAllElements();
                case 0 ->{
                    return;
                }
                default -> System.out.println("Error: Optiunea este invalida. ");
            }
        }while(true);
    }
}

