A. How many apps involved = 3
HOMEPAGE.java

STUDENT

STUDENTLOGIN.java

STUDENTHOME.java

REGISTER.java

VIEWGRADE.java

LECTURE

LECTURELOGIN.java

LECTUREHOME.java

VIEWREGISTER.java

INPUTMARK.java

ADMIN

ADMINLOGIN.java

ADMINHOME.java

ADDSTUDENT.java


B. Brief explanation each apps

HOMEPAGE.java- A home page where got 3 button to choose to login which is STUDENT,LECTURE,ADMIN.

STUDENT

STUDENTLOGIN.java - A login page for students which can login by their matric number & password. Wrong matric/password can’t login. Only the registered matric & password can logged in.

STUDENTHOME.java- Once the student logged in successfully, he/she is able to see their name on the page. The name is shown which matric number is currently logged in. They are able to see the STUDENTHOME page where there are buttons of Register, view grade, change password and logout.

REGISTER.java- This page is where it brings once students click the register button. It will have a dropdown for subjects that are available to register. Each student can register many subjects that are available but cant register same subjects that already registered before.

VIEWGRADE.java- Once a student clicks the View grade button in STUDENTHOME page, it is brought over here where the student can view their grade for their registered subjects. The student logged in can view their grades only. If the subject is not graded yet, it will show a blank box.

LECTURER

LECTURELOGIN.java-A login page for lectures which can login by their id & password. Wrong id/password can’t login. Only the registered id & password can logged in.

LECTUREHOME.java-Once the lecture logged in successfully, he/she is able to see their name on the page. The name is shown which id number is currently logged in. They are able to see the LECTUREHOME page where there are buttons of VIEW REGISTEREDE STUDENTS, INPUT MARK,  and logout.

VIEWREGISTER.java- Once the lecturer clicks the View register button in LECTUREHOME page, it is brought over here where the lecturer can view who registered subjects under them only . 

INPUTMARK.java- Once the lecture clicks on the input mark button it is brings over here where lecture can input mark only for the students registered under them. They can update the marks as well and click the save button. They are able to click marks among 0-100 only. And once they input the mark, the grade will be automatically saved according to the marks.



ADMIN

ADMINLOGIN.java - A login page for admin which can login by their ID number & password. Wrong ID number or password can’t login. Only the registered ID number & password can log in.

ADMINHOME.java - Once the admin logged in successfully, he/she is able to see their name on the page. The name is shown which ID number is currently logged in. They are able to see the ADMINHOME page where there are three buttons which are Add Students, Delete Student and Logout. When Add Students button is clicked, it will navigate to ADDSTUDENT page and when Delete Student button is clicked, it will prompt an Input box where admin need to enter the matric number of student which want to be deleted.

ADDSTUDENT.java - Admin have to enter the student name and matric number of new student to be added into the database.



C. Architecture/Layer diagram for each of the apps including the middleware

1)HOMEPAGE.java 

![Untitled Diagram-Page-12 drawio (1)](https://github.com/jeevethaaraju/PROJECT/assets/163825255/dea59e24-dca4-4f25-b392-1598a5b72941)


1) STUDENT

![Untitled Diagram-Page-12 drawio (1)](https://github.com/jeevethaaraju/PROJECT/assets/163825255/5c099c7d-c5a0-49a7-aa59-725e5f6ae32c)



2) LECTURER

![Screenshot 2024-06-25 152407](https://github.com/jeevethaaraju/PROJECT/assets/163825255/c45bf0b4-b028-4eb8-a7e0-736e957c9a43)




3)ADMIN

![Screenshot 2024-06-25 154624](https://github.com/jeevethaaraju/PROJECT/assets/163825255/7d46e53e-a2a4-421d-9950-36a8b7d88617)




D. List of URL endpoints middleware RESTful/SOAP/Socket

http://localhost/project/add_student.php
http://localhost/project/change_password.php
http://localhost/project/deleteStudent.php
http://localhost/project/fetch_students.php
http://localhost/project/getstudents.php
http://localhost/project/getsubject.php
http://localhost/project/login.php
http://localhost/project/loginadmin.php
http://localhost/project/loginlecture.php
http://localhost/project/register.php
http://localhost/project/save_marks.php
http://localhost/project/update_password.php
http://localhost/project/viewgrade.php




E. Functions/Features in the middleware

1) STUDENTLOGIN.java

Login for student
Endpoint: http://localhost/project/login.php
Purpose: login by students to register subject
Request Parameters:
matric: Matriculation number of the student.
Password : Password of student
Response:
JSON object with fields:
status: Status of the login(success or fail).
message (if login is fail): Invalid matric number and password.

2)STUDENTHOME.java
 Student homepage for student
Purpose: homepage for students to choose to weather they want to register subject/view their grades or change their password 
Response:
Direct to register subject page of click register button and same goes to change password button and view grade button
3) REGISTER.java
Register Subject for Student
Endpoint:http://localhost/project/register.php
Purpose: Registers a subject for a student.
Request Parameters:
subjectName: Name of the subject to register.
matric: Matriculation number of the student.
studentName: Name of the student.
Response:
JSON object with fields:
status: Status of the registration (success, already_registered, error).
message: Additional message related to the registration status.

4)VIEWGRADE.java
Fetch Grades by Matriculation Number
Endpoint:http://localhost/project/viewgrade.php
Purpose: Retrieves grades for a specific student identified by their matriculation number (matric).
Request Parameters:
matric: Matriculation number of the student.
Response:
JSON object with fields:
status: Status of the request (success or fail).
message (if status is fail): Error message.
grades (if status is success): Array of objects containing grade details:
subjectname: Name of the subject.
grade: Grade obtained.
5)LECTURELOGIN.java

 Login for lecturer
Endpoint: http://localhost/project/loginlecture.php
Purpose: Login by lecturer to view registered students and to input marks.
Request Parameters:
Id number: Id number of lecturer.
Password : Password of lecturer
Response:
JSON object with fields:
status: Status of the login(success or fail).
message (if login fails): Invalid matric number and password.
message (if login success): Login successfully.









6)VIEWREGISTER.java
 View registered student under lecturer
Endpoint: http://localhost/project/loginlecture.php
Purpose: to fetch registered students' data for a specific lecture under the supervision of a lecturer. 
Request Parameters:
POST:lecture_id: Identifier for the lecture for which to fetch registered students.
Response:
The response from fetch_students.php should provide data based on the lecture_id:
Success Response:
Status: success
Data:
students: Array of student objects.
Each student object contains fields like matric (student identifier) and student_name.
Error Response:
Status: fail
Message: Error message describing the reason for failure (e.g., invalid lecture_id, database error).

7)INPUTMARK.java

 Input student marks for lecturer
Endpoint: http://localhost/project/save_marks.php
Purpose: receive updated marks for a student in a specific lecture and save them to the database.
Request Parameters:
lecture_id: This parameter specifies the unique identifier of the lecture.
matric: This parameter specifies the matriculation number of the student whose marks are being updated.
marks: This parameter specifies the updated marks for the student.

Response:
The endpoint returns a JSON response indicating the status of the update operation:
status: Indicates the status of the request ("success" or "fail").
message: A message providing additional information about the operation's outcome.



8) ADMINLOGIN.java
    Login for admin
Endpoint: http://localhost/project/loginadmin.php
Purpose: Login by admin to add student
Request Parameters:
ID Number: Identification number of the admin.
Password : Password of admin
Response:
JSON object with fields:
status: Status of the login(success or fail).
message (if login is fail): Invalid ID number or password.

9) ADMINHOME.java
      Admin homepage for admin
Purpose: Homepage for admin to choose whether they want to add students or delete student.
Response:
Direct to ADD STUDENT page if click Add Student button and an input box will prompt when delete student button is clicked.
      Delete Student by Admin
Endpoint: http://localhost/project/deleteStudent.php
Purpose: Delete student from the system.
Send as POST Parameters :
matric : Matriculation number of student.
Response:
JSON object with fields:
status: Status of the deletion will be shown after entering the matric number of student.
message: Additional message related to the deletion status (Student deleted successfully).
10) ADDSTUDENT.java
      Add Student by Admin
Endpoint: http://localhost/project/add_student.php

Purpose: Add student into the system

Request Parameters:
name: Name of the new student.
matric: Matriculation number of the new student.
password: Set as default which is “student”.

Response:
JSON object with fields:
status: Status of the registration will be shown after entering the name and matric number of new students.
message: Additional message related to the registration status (Student added successfully).


F. The database and tables involved in the projects

DATABASE NAME- projectdad
TABLES
admins
register
lecture
student
subject

Presentation link: https://youtu.be/P0gji_9vjsw?si=wH8rMsWrg65g8u1n
