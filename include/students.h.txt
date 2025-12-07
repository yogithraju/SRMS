#ifndef STUDENTS_H
#define STUDENTS_H

struct Student {
    int id;
    char name[50];
    float marks;
};

void loadStudents();
void saveStudents();
void displayStudents();
void searchStudent();
void sortStudents();
void exportCSV();

#endif
