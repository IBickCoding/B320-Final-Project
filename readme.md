# USCB Course Registration & Academic Database

A relational database project designed to model the University of South Carolina Beaufort's course catalog, course offerings, student enrollment, academic records, and instructor information using Microsoft SQL Server.

The project was developed as the final project for B320: Database Management Systems I and was completed as a team project.

Rather than relying entirely on fabricated data, the database was populated using real-world registrar data provided by USCB, including Spring 2024 course catalog and course schedule data. Synthetic student enrollment and academic data were then used to demonstrate how the database could support common university information and registration tasks.

> **Data Privacy Notice:** University course information used in this project comes from publicly available/institutionally provided course data. All student records used for enrollment and scheduling are fictional and were created specifically for this project. No real student information is stored in the database.

---

## 🎯 Purpose

The goal of this project was to design and implement a relational database capable of representing the relationships between university courses, course offerings, instructors, students, enrollments, grades, and academic terms.

The project demonstrates the process of moving from real-world institutional data to a structured relational database while maintaining data integrity through keys, constraints, relationships, and database views.

The project was designed to demonstrate:

- Relational database design
- SQL Server development
- Entity-relationship modeling
- Database normalization
- Data loading and transformation
- Primary and foreign keys
- Referential integrity
- Check constraints
- Database views
- Complex SQL queries
- Aggregation and calculated values
- Student enrollment modeling
- GPA calculation
- Instructor performance analysis

---

## 🏗️ Database Design

The database was designed using an Entity Relationship Diagram (ERD) created with Lucidchart.

The design separates the major entities involved in a university registration and academic-record system and establishes relationships between those entities.

The database includes entities for areas such as:

- Students
- Instructors
- Course catalog
- Course offerings
- Academic terms
- Enrollments
- Grade information

The resulting relational structure allows information to be queried across multiple related tables rather than storing all university information in a single table.

### Entity Relationship Diagram

The project's ERD is available in the repository:

**B320_Team_03_ERD.pdf**

---

## 🗄️ Database Components

### Course Catalog

The course catalog represents the university's available courses and their associated academic information.

The catalog is separated from individual course offerings so that a course can exist independently of when or how many times it is offered.

### Course Offerings

Course offerings represent specific instances of courses being offered during an academic term.

This allows the database to distinguish between a course and a particular semester's offering of that course.

### Students

Student records are used to demonstrate enrollment and academic-record functionality.

The student records used for testing are synthetic and do not represent real USCB students.

### Enrollments

The enrollment relationship connects students with specific course offerings.

This allows:

- One student to enroll in multiple courses.
- One course offering to contain multiple students.
- Grades to be associated with a student's enrollment in a specific course.

### Grade Information

A dedicated grade table is used to associate grades with grade points and provide controlled values for enrollment records.

This approach allows academic calculations such as GPA to be performed using relational data rather than storing a pre-calculated GPA for each student.

### Instructors

Instructor records are associated with course offerings, allowing the database to analyze teaching assignments and student populations.

### Academic Terms

Academic term information represents the semester or term associated with course offerings.

The database uses constraints to restrict valid values for attributes such as term season and term length.

---

## 🛠️ Technologies Used

- **SQL Server Management Studio (SSMS)**
- **Lucidchart** — Entity Relationship Diagram
- **Microsoft Excel** — Source data files
- **Git/GitHub**

The SQL scripts in this repository follow Microsoft SQL Server / SSMS syntax.

---

## 📊 Real-World Data

One of the major components of this project was working with real-world registrar data rather than an entirely fabricated dataset.

The repository contains:

- `CourseCatalog-Spring 2024.xlsx`
- `CourseSchedules-Spring2024.xlsx`

These datasets were provided as USCB registrar data dumps and were used as the basis for the course catalog and scheduling information.

Working with this data introduced practical challenges that are not always present in simplified classroom datasets, including determining how source data should be organized and mapped into a normalized relational structure.

### Data Privacy

The project does **not** use real student information for its demonstration enrollment records.

Student and enrollment information used for database testing and demonstration is synthetic.

---

## 🔄 Data Loading

The primary database creation and loading process is contained in:

`B320_Team_03_CreateLoad.sql`

This script contains the SQL required to create and populate the database.

The script creates the database structure and loads the required data into the appropriate tables.

---

## 🔐 Data Integrity & Constraints

Data integrity was an important part of the database design.

The project uses SQL constraints to prevent invalid values from being entered into certain tables.

For example, the `AcademicTerm` table contains constraints restricting valid values for:

### Term Length

- Full
- Half 1st
- Half 2nd
- May

### Season

- Summer
- Spring
- Fall

These constraints help ensure that invalid academic-term values cannot be inserted into the database.

The project also uses a dedicated `GradeInfo` table to control valid grade values rather than relying on unrestricted text input for enrollment grades.

Primary and foreign keys are also used to maintain relationships between related entities and preserve referential integrity.

---

## 👁️ Database Views

The project includes several SQL views designed to make complex academic information easier to query.

These views are contained in:

`B320_Team_03_ViewsConstraints.sql`

### `vwGPA`

Calculates a student's GPA and cumulative credits based on their enrollment and grade information.

The view also classifies students based on accumulated credits, such as:

- 1st Year
- 2nd Year
- 3rd Year
- 4th Year
- Graduate

The GPA calculation uses grade points and course credits to calculate a student's weighted GPA.

### `vwInstructorInfo`

Provides instructor information and the number of courses associated with each instructor.

### `vwInstructorAverage`

Calculates average grade information associated with instructors.

### `vwInstructorStudentsTaught`

Calculates the number of students associated with each instructor through course enrollments.

### `vwInstructorPerformance`

Combines the instructor views to provide a higher-level representation of instructor performance, including:

- Instructor identification
- Instructor name
- Number of courses taught
- Number of students taught
- Average grade

These views demonstrate how complex SQL queries can be abstracted into reusable database objects.

---

## 🧠 What I Learned

This project significantly expanded my understanding of relational database design and SQL Server.

### Relational Database Design

I learned how to translate a real-world system into a relational model by identifying:

- Entities
- Attributes
- Relationships
- Primary keys
- Foreign keys
- Cardinality
- Many-to-many relationships

### Working With Real-World Data

Working with actual university registrar data demonstrated that real-world datasets are significantly more complicated than the simplified datasets typically used in introductory SQL exercises.

I gained experience identifying inconsistencies, determining which information was actually useful, and transforming raw data into a structure suitable for a relational database.

### SQL Server

The project provided practical experience with Microsoft SQL Server and SSMS, including:

- Table creation
- Data insertion
- Primary keys
- Foreign keys
- Constraints
- JOIN operations
- Aggregation
- GROUP BY
- Calculated fields
- Views
- Conditional logic
- Data validation

### Database Views

Creating views was particularly useful because it demonstrated how complex queries can be packaged into reusable database objects.

Rather than repeatedly writing the same complicated joins and calculations, a view can provide a consistent interface for accessing derived information.

### Data Integrity

I also gained a better understanding of why database constraints are important.

A database should not simply accept whatever data an application attempts to insert. The database itself should enforce appropriate rules to protect the integrity of the data.

---

## 🚀 Installation & Setup

### Prerequisites

You will need:

- Microsoft SQL Server
- SQL Server Management Studio (SSMS)
- Git

The repository's SQL scripts use Microsoft SQL Server syntax.

### Clone the Repository

    git clone https://github.com/IBickCoding/B320_SQL_Project.git

    cd B320_SQL_Project

### Create and Load the Database

Open:

`B320_Team_03_CreateLoad.sql`

in SQL Server Management Studio.

Execute the script to create and populate the database.

### Apply Constraints and Views

After creating and loading the database, execute:

`B320_Team_03_ViewsConstraints.sql`

This script adds the appropriate constraints and creates the project's database views.

> **Note:** The constraints/views script contains statements intended to be run against the course database after the primary database creation/load script has been executed.

---

## 📁 Repository Structure

    B320_SQL_Project/
    │
    ├── B320_Team_03_CreateLoad.sql
    │   └── Database creation and data-loading script
    │
    ├── B320_Team_03_ViewsConstraints.sql
    │   └── Database constraints and SQL views
    │
    ├── B320_Team_03_ERD.pdf
    │   └── Entity Relationship Diagram
    │
    ├── B320_Team_03_ProjectDocumentation.docx
    │   └── Original project documentation
    │
    ├── CourseCatalog-Spring 2024.xlsx
    │   └── USCB course catalog source data
    │
    ├── CourseSchedules-Spring2024.xlsx
    │   └── USCB course schedule source data
    │
    └── README.md

---

## 👥 Team

This project was completed as a team-based final project for **B320: Database Management Systems I**.

### Team Members

- **Ian Bickford**
- **Houston Henderson**

---

## 📚 Project Documentation

Additional project documentation is available in the repository:

- **ERD:** `B320_Team_03_ERD.pdf`
- **Project Documentation:** `B320_Team_03_ProjectDocumentation.docx`
- **Database Creation/Load:** `B320_Team_03_CreateLoad.sql`
- **Views & Constraints:** `B320_Team_03_ViewsConstraints.sql`
