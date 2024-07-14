<br> <br>
# Database Project for **Academia** <br> <br> <br> 
The scope of this project is to use all the SQL knowledge gained throught the Software Testing course and apply them in practice. <br> 

Application under test: **Academia**

Tools used: MySQL Workbench <br>

Database description:  **Academia** is a virtual platform where students can register and learn for free from the materials recorded on the academy's website and also the students can enroll to live and paid courses with active participation. <br> <br> <br> <br>
## Database Schema

You can find below the database schema that was generated through Reverse Engineer and which contains all the tables and the relationships between them. <br> <br> <br> <br> <br> <br>

   
  
 ### The tables are connected in the following way: <br> <br> <br>

**Users** is connected with **Courses** through a **one to many or one to one** relationship which was implemented through **Users.UsersID** as a primary key and **Courses.InstructorID** as a foreign key <BR> <BR>

**nume tabela 3** is connected with **nume tabela 4** through a **tip relatie** relationship which was implemented through **nume_tabela.nume_coloana_cheie_primara** as a primary key and **nume_tabela.nume_coloana_cheie_secundara** as a foreign key <BR> <BR>

**nume tabela 5** is connected with **nume tabela 6** through a **tip relatie** relationship which was implemented through **nume_tabela.nume_coloana_cheie_primara** as a primary key and **nume_tabela.nume_coloana_cheie_secundara** as a foreign key <BR> <BR><br> <br> <br> <br> <br>




### Database Queries <br> <br> <br> <br>

DDL (Data Definition Language)  <br> <br>

The following instructions were written in the scope of CREATING the structure of the database (CREATE INSTRUCTIONS)

#### Creating a MySQL database for online learning platform named Academia <br> <br>

* CREATE DATABASE Academia;




#### This table will store information about all users (students, instructors and admins) <br> <br>

* CREATE TABLE Users (
    UserID INT AUTO_INCREMENT PRIMARY KEY,
    Username VARCHAR(50) NOT NULL UNIQUE,
    Password VARCHAR(255) NOT NULL,
    Email VARCHAR(100) NOT NULL UNIQUE,
    FullName VARCHAR(100),
    UserType ENUM('Student', 'Instructor', 'Admin') NOT NULL,
    CreatedAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
 <br> <br>


#### This table will store information about the available courses on the platform
* CREATE TABLE Courses (
    CourseID INT AUTO_INCREMENT PRIMARY KEY,
    CourseName VARCHAR(100) NOT NULL,
    Description TEXT,
    InstructorID INT,
    CreatedAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (InstructorID) REFERENCES Users(UserID)
);
 <br> <br>

#### This table records which students are enrolled in which courses

* CREATE TABLE Enrollments (
    EnrollmentID INT AUTO_INCREMENT PRIMARY KEY,
    CourseID INT,
    StudentID INT,
    EnrollmentDate TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (CourseID) REFERENCES Courses(CourseID),
    FOREIGN KEY (StudentID) REFERENCES Users(UserID)
);


 <br> <br>
#### This table will store information about assignments for each course
* CREATE TABLE Assignments (
    AssignmentID INT AUTO_INCREMENT PRIMARY KEY,
    CourseID INT,
    Title VARCHAR(100) NOT NULL,
    Description TEXT,
    DueDate DATE,
    CreatedAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (CourseID) REFERENCES Courses(CourseID)
);

 <br> <br>
#### This table will store the submissions of assignments of the students
* CREATE TABLE Submissions (
    SubmissionID INT AUTO_INCREMENT PRIMARY KEY,
    AssignmentID INT,
    StudentID INT,
    SubmissionDate TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    Grade DECIMAL(5, 2),
    Feedback TEXT,
    FOREIGN KEY (AssignmentID) REFERENCES Assignments(AssignmentID),
    FOREIGN KEY (StudentID) REFERENCES Users(UserID)
);


 <br> <br>  <br> <br>  <br> 
After the database and the tables have been created, a few ALTER instructions were written in order to update the structure of the database, as described below:<br> <br><br> <br>

Inserati aici toate instructiunile de ALTER pe care le-ati scris. Incercati sa includeti instructiuni cat mai variate cum ar fi: - schimbare nume tabela - adaugare sau stergere coloana - redenumire coloana - adaugare proprietati coloana (ex: adaugare auto-increment) - modificare proprietati coloana (ex: modificare tip de data, modificare pozitie coloana etc) - adaugare cheie primara sau secundara (daca nu a fost deja adaugata la crearea tabelei)

DML (Data Manipulation Language)
In order to be able to use the database I populated the tables with various data necessary in order to perform queries and manipulate the data. In the testing process, this necessary data is identified in the Test Design phase and created in the Test Implementation phase.

Below you can find all the insert instructions that were created in the scope of this project:

Inserati aici toate instructiunile de INSERT pe care le-ati scris. Incercati sa folositi atat insert pe toate coloanele (fara sa precizati pe ce coloane se face insert) cat si insert pe cateva coloane (care necesita mentionarea explicita a coloanelor pe care se face insert). De asemenea, incercati sa acoperiti situatia in care inserati mai multe randuri in acelasi timp

After the insert, in order to prepare the data to be better suited for the testing process, I updated some data in the following way:

Inserati aici toate instructiunile de UPDATE pe care le-ati scris folosind filtrarile necesare astfel incat sa actualizati doar datele de care aveti nevoie

DQL (Data Query Language)
After the testing process, I deleted the data that was no longer relevant in order to preserve the database clean:

Inserati aici toate instructiunile de DELETE pe care le-ati scris folosind filtrarile necesare astfel incat sa stergeti doar datele de care aveti nevoie

In order to simulate various scenarios that might happen in real life I created the following queries that would cover multiple potential real-life situations:

Inserati aici toate instructiunile de SELECT pe care le-ati scris folosind filtrarile necesare astfel incat sa extrageti doar datele de care aveti nevoie Incercati sa acoperiti urmatoarele:
- where
- AND
- OR
- NOT
- like
- inner join
- left join
- OPTIONAL: right join
- OPTIONAL: cross join
- functii agregate
- group by
- having
- OPTIONAL DAR RECOMANDAT: Subqueries - nu au fost in scopul cursului. Puteti sa consultati tutorialul asta si daca nu intelegeti ceva contactati fie trainerul, fie coordonatorul de grupa

Conclusions  <br> <br> <br>

     
     I have created the database for an online learning platform named Academia and this way I have been learning to create tables, populate them with data, make connections between tables, update some information, delete some data and return the data both at once and with various filters. 
     Thank you for your time!
