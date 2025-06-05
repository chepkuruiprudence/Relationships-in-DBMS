# Key Relationships in DBMS and Key Constraints

## Introduction
A Database Management System (DBMS) uses keys and relationships to organize, retrieve, and maintain data efficiently. Understanding these concepts is crucial for designing robust databases.

---

## 1. What are Keys in DBMS?
**Keys** are attributes or sets of attributes that help uniquely identify a record (row) in a table. They ensure that each record can be uniquely retrieved and referenced.

### Types of Keys
- **Primary Key**: Uniquely identifies each record in a table. Cannot have NULL values.
- **Candidate Key**: A set of attributes that can uniquely identify a record. There can be multiple candidate keys in a table.
- **Super Key**: A set of one or more attributes that, taken collectively, can uniquely identify a record. All candidate keys are super keys, but not all super keys are candidate keys.
- **Alternate Key**: Candidate keys that are not chosen as the primary key.
- **Foreign Key**: An attribute in one table that refers to the primary key of another table. Used to establish relationships between tables.
- **Composite Key**: A key that consists of two or more attributes that together uniquely identify a record.

---

---

## 3. Relationships in DBMS
Relationships define how tables are connected to each other.

### Types of Relationships
- **One-to-One (1:1)**: Each record in Table A is related to one and only one record in Table B, and vice versa.
- **One-to-Many (1:N)**: A record in Table A can be related to multiple records in Table B, but a record in Table B is related to only one record in Table A.
- **Many-to-Many (M:N)**: Records in Table A can be related to multiple records in Table B and vice versa. Implemented using a junction (bridge) table.

### Example Codes and Instances

#### 1. One-to-One Relationship
**Example:** Each person has one passport, and each passport is assigned to one person.

```sql
CREATE TABLE Person (
    person_id INT PRIMARY KEY,
    name VARCHAR(100)
);

CREATE TABLE Passport (
    passport_id INT PRIMARY KEY,
    person_id INT UNIQUE,
    FOREIGN KEY (person_id) REFERENCES Person(person_id)
);
```

#### 2. One-to-Many Relationship
**Example:** A customer can place many orders, but each order is placed by one customer.

```sql
CREATE TABLE Customer (
    customer_id INT PRIMARY KEY,
    name VARCHAR(100)
);

CREATE TABLE Orders (
    order_id INT PRIMARY KEY,
    order_date DATE,
    customer_id INT,
    FOREIGN KEY (customer_id) REFERENCES Customer(customer_id)
);
```

#### 3. Many-to-Many Relationship
**Example:** Students and courses. A student can enroll in many courses, and a course can have many students.

```sql
CREATE TABLE Student (
    student_id INT PRIMARY KEY,
    name VARCHAR(100)
);

CREATE TABLE Course (
    course_id INT PRIMARY KEY,
    course_name VARCHAR(100)
);

-- Junction table to implement many-to-many
CREATE TABLE StudentCourse (
    student_id INT,
    course_id INT,
    PRIMARY KEY (student_id, course_id),
    FOREIGN KEY (student_id) REFERENCES Student(student_id),
    FOREIGN KEY (course_id) REFERENCES Course(course_id)
);
```

---

## 4. Importance of Keys and Relationships
- **Data Integrity**: Keys and constraints prevent duplicate and inconsistent data.
- **Efficient Data Retrieval**: Keys help in quickly locating records.
- **Referential Integrity**: Relationships ensure that data across tables remains consistent.

---



*Prepared for: Presentation on Key Relationships and Key Constraints in DBMS*