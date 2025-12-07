#include <stdio.h>
#include <string.h>
#include "../include/students.h"

struct Student students[100];
int studentCount = 0;

void loadStudents() {
    FILE *fp = fopen("data/students.txt", "r");
    studentCount = 0;

    if (fp == NULL) return;

    while (fscanf(fp, "%d %s %f", 
        &students[studentCount].id,
        students[studentCount].name,
        &students[studentCount].marks) != EOF) 
    {
        studentCount++;
    }
    fclose(fp);
}

void saveStudents() {
    FILE *fp = fopen("data/students.txt", "w");
    for (int i = 0; i < studentCount; i++) {
        fprintf(fp, "%d %s %.2f\n",
            students[i].id,
            students[i].name,
            students[i].marks
        );
    }
    fclose(fp);
}

void displayStudents() {
    printf("\n--- Student Records ---\n");
    for (int i = 0; i < studentCount; i++) {
        printf("%d  %s  %.2f\n", 
            students[i].id, 
            students[i].name, 
            students[i].marks
        );
    }
}

void searchStudent() {
    char key[50];
    printf("Enter ID or Name to search: ");
    scanf("%s", key);

    int found = 0;

    for (int i = 0; i < studentCount; i++) {
        if (strcmp(students[i].name, key)==0 || students[i].id == atoi(key)) {
            printf("\nFound: %d %s %.2f\n",
                students[i].id,
                students[i].name,
                students[i].marks
            );
            found = 1;
        }
    }

    if (!found) printf("No student found!\n");
}

void sortStudents() {
    int choice;
    printf("\nSort By: 1-ID  2-Name  3-Marks: ");
    scanf("%d", &choice);

    for (int i = 0; i < studentCount-1; i++) {
        for (int j = i+1; j < studentCount; j++) {
            int swap = 0;

            if (choice == 1 && students[i].id > students[j].id) swap = 1;
            if (choice == 2 && strcmp(students[i].name, students[j].name) > 0) swap = 1;
            if (choice == 3 && students[i].marks < students[j].marks) swap = 1;

            if (swap) {
                struct Student temp = students[i];
                students[i] = students[j];
                students[j] = temp;
            }
        }
    }

    printf("\nStudents sorted successfully.\n");
}

void exportCSV() {
    FILE *fp = fopen("output/exported_students.csv", "w");
    fprintf(fp, "ID,Name,Marks\n");

    for (int i = 0; i < studentCount; i++) {
        fprintf(fp, "%d,%s,%.2f\n",
            students[i].id, students[i].name, students[i].marks
        );
    }

    fclose(fp);
    printf("\nStudents exported to CSV!\n");
}
