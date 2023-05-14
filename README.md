# Book-donation-sytem

#include <stdio.h>
#include <string.h>

// Structure to represent a book
struct Book {
    char title[50];
    char author[50];
    int year;
};

// Function to display book details
void displayBook(struct Book b) {
    printf("Title: %s\n", b.title);
    printf("Author: %s\n", b.author);
    printf("Year: %d\n", b.year);
}

int main() {
    struct Book books[100];
    int numBooks = 0;
    int choice = 0;

    while (choice != 4) {
        printf("\n");
        printf("1. Donate a book\n");
        printf("2. List all donated books\n");
        printf("3. Search for a book by author\n");
        printf("4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
                   case 1: // Donate a book
                       if (numBooks >= 100) {
                           printf("Sorry, the donation system is full.\n");
                       } else {
                           struct Book b;
                           printf("Enter book title: ");
                           scanf("%s", b.title);
                           printf("Enter book author: ");
                           scanf("%s", b.author);
                           printf("Enter year of publication: ");
                           scanf("%d", &b.year);
                           books[numBooks] = b;
                           numBooks++;
                           printf("Thank you for donating a book!\n");
                       }
                       break;
                   case 2: // List all donated books
                       if (numBooks == 0) {
                           printf("No books have been donated yet.\n");
                       } else {
                           printf("List of donated books:\n");
                           for (int i = 0; i < numBooks; i++) {
                               displayBook(books[i]);
                               printf("\n");
                           }
                       }
                       break;
                   case 3: // Search for a book by author
                       if (numBooks == 0) {
                           printf("No books have been donated yet.\n");
                       } else {
                           char author[50];
                           printf("Enter author name: ");
                           scanf("%s", author);
                           int found = 0;
                           for (int i = 0; i < numBooks; i++) {
                               if (strcmp(books[i].author, author) == 0) {
                                   displayBook(books[i]);
                                   printf("\n");
                                   found = 1;
                               }
                           }
                           if (!found) {
                                                 printf("No books found for author '%s'.\n", author);
                                             }
                                         }
                                         break;
                                     case 4: // Exit
                                         printf("Goodbye!\n");
                                         break;
                                     default:
                                         printf("Invalid choice. Please try again.\n");
                                         break;
                                 }
                             }

                             return 0;
                         }
