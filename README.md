Student Management System

A simple and efficient Student Management System built using C.
This project helps store, manage, update, delete, search, and export student records.
It works completely on file handling, ensuring data is permanently stored even after the program closes.

Features: 

Core Features

Add new student records

View all student records

Search for a student by ID or name

Update existing student information

Delete a student record

Export student records to a CSV file

Maintain a login system

Track login history

Store credentials securely in a text file

Generate student reports

Display top performers

Count total number of students

Categorize students by department

Sort students by marks, name, or ID

Additional Features:

Simple file-based database

Auto-save after every operation

Error handling for invalid inputs

Duplicate-ID prevention

Minimal and easy-to-read C code structure

File Structure
Source Code

Contains all C files needed to run the system.

Data Folder

Stores:

students.txt – raw student data

exported_students.csv – exported report

credentials.txt – admin login credentials

login_history.txt – timestamped login records

Output Folder

Contains generated files such as:

report.txt

top_students.txt

backups (if enabled)

How It Works

The admin logs in using a username and password stored in credentials.txt.

Every login is recorded inside login_history.txt.

Students are added and stored in students.txt using a predefined format.

When export is selected, the system generates exported_students.csv.

Updates and deletions modify the same file using temporary file handling.

How to Run

Install a C compiler (GCC recommended).

Compile the program:
gcc main.c -o sms

Run the program:
./sms

Credentials File Format

File: credentials.txt
admin password

(First line is username, second line is password.)

Login History File Format

File: login_history.txt
Each line contains a timestamp and login status.

Example:
2025-01-11 14:32:22 – Login successful

Exported CSV Format

File: exported_students.csv
CSV includes:
student_id, name, department, marks, age

Future Enhancements

GUI version

Online database integration

Role-based login

Encrypted credential storage

Attendance and fee management

Author

YOGITH RAJU MEDIDI
Passionate about C programming, data management, and automation.
