#include <stdio.h>
#include "../include/auth.h"
#include "../include/students.h"
#include "../include/utils.h"

int main() {

    if (!login()) {
        printf("Login failed!\n");
        return 0;
    }

    loadStudents();

    int choice;

    while (1) {
        printf("\n--- MENU ---\n");
        printf("1. View Students\n");
        printf("2. Search Student\n");
        printf("3. Sort Students\n");
        printf("4. Export CSV\n");
        printf("5. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1: displayStudents(); break;
            case 2: searchStudent(); break;
            case 3: sortStudents(); break;
            case 4: exportCSV(); break;
            case 5: saveStudents(); return 0;
            default: printf("Invalid!\n");
        }
    }
}
