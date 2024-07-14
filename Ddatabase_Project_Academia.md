<br> <br>
# Database Project for **'Academia'** <br> <br> <br> 
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

- schimbare nume tabela - adaugare sau stergere coloana - redenumire coloana - adaugare proprietati coloana (ex: adaugare auto-increment) - modificare proprietati coloana (ex: modificare tip de data, modificare pozitie coloana etc)
- 
  <br> <br>  <br> <br>  <br> <br>



  
DML (Data Manipulation Language)  <br> <br>  <br> <br>  <br> 



In order to be able to use the database I populated the tables with various data necessary in order to perform queries and manipulate the data. In the testing process, this necessary data is identified in the Test Design phase and created in the Test Implementation phase.  <br> <br>  <br> <br>



 <br> <br>  
 
### Below you can find all the insert instructions that were created in the scope of this project:
 <br> <br> <br> <br> <br> 


  <

#### Examples of how to insert data into Users table <br> <br>  
* INSERT INTO Users (Username, Password, Email, FullName, UserType)
VALUES 
('maria_verga', 'password111', 'maria@gmail.com', 'Maria Verga', 'Student'),
('cris_marton', 'password123', 'cris@gmail.com', 'Cris Marton', 'Instructor'),
('roxana_admin', 'adminpassword', 'admin@yahoo.com', 'Admin Roxana', 'Admin');
<br> 


#### Examples of how to insert data into Courses table  <br> <br>  
* INSERT INTO Courses (CourseName, Description, InstructorID)
VALUES 
('mysql', 'cybersec', 2),
('python', 'mongodb', 2);

<br> 

#### Enroll Students in Courses <br> <br>  
* INSERT INTO Enrollments (CourseID, StudentID)
VALUES 
(1, 1),
(2, 1);

<br> 

#### Create Assignments  <br>  
* INSERT INTO Assignments (CourseID, Title, Description, DueDate)
VALUES 
(1, 'mysql basics', 'cybersec basics', '2024-08-01'),
(2, 'python basics', 'mongo db basics', '2024-08-15');


<br> 

#### Submitting Assignments  <br>  
* INSERT INTO Submissions (AssignmentID, StudentID, SubmissionDate, Grade, Feedback)
VALUES 
(1, 1, '2024-07-14', 85.5, 'Good job!'),
(2, 1, '2024-07-13', 90.0, 'Excellent work!');
<br>  

 We have one student more, his name is Marcel
so we have to add another entry to our database  <br> 
* INSERT INTO Users (Username, Password, Email, FullName, UserType)
VALUES ('colegul_Marcel', '12345', 'marcel@yahoo.com', 'Marcel', 'Student');

<br> <br>   <br> <br>  

De asemenea, incercati sa acoperiti situatia in care inserati mai multe randuri in acelasi timp




 <br> <br>  

After the insert, in order to prepare the data to be better suited for the testing process, I updated some data in the following way:  <br> <br>  


 
instructiunile de UPDATE pe care le-ati scris folosind filtrarile necesare astfel incat sa actualizati doar datele de care aveti nevoie




 <br> <br>    <br> <br>    
 

### DQL (Data Query Language)   <br> <br>    <br> <br>  

After the testing process, I deleted the data that was no longer relevant in order to preserve the database clean:



Iinstructiunile de DELETE pe care le-ati scris folosind filtrarile necesare astfel incat sa stergeti doar datele de care aveti nevoie  <br> <br>   <br> <br>  







 <br> <br>   <br> <br>   <br> <br>  

In order to simulate various scenarios that might happen in real life I created the following queries that would cover multiple potential real-life situations:  <br> <br>   <br> 



Instructiunile de SELECT pe care le-ati scris folosind filtrarile necesare astfel incat sa extrageti doar datele de care aveti nevoie Incercati sa acoperiti urmatoarele:
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
-  <br> <br>    <br> <br>  

## Conclusions  <br> <br> <br>

     
     I have created the database for an online learning platform named Academia and this way I have been learning to create tables, populate them with data, make connections between tables, update some information, delete some data and return the data both at once and with various filters. 
     Thank you for your time!
