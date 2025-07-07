
# LINQUIZ - CLI-Based Quiz Application

## 📚 Description

In traditional quiz or test systems, manual operations such as paper preparation, question randomization, evaluation, and result tabulation are 
time-consuming and error-prone. There's also a lack of personalization and instant feedback, which are essential in modern learning systems.

So the question arises - **"How can we create an efficient, reusable, and scalable quiz system using C++ that supports multiple user roles, 
offers secure and personalized interaction, and maintains quiz data persistently using a database?"** 

This quiz system provides a solution to the above problem. It solves :
● The inefficiency of manual quiz management.
● Lack of real-time evaluation and scoring. 
● Absence of centralized records for tracking user performance over time.

**LINQUIZ** is a command-line quiz application built using **C++** with **MySQL integration**, applying Object-Oriented Programming principles. 
This group project was developed using **Dev-C++**, and supports both **Admin** and **Student** roles, enabling dynamic quiz creation, scoring, and persistent data storage.

---

## ✨ Features

- 🔐 **Role-Based Login** for Admins and Students  
- 🧠 **Create/Attempt Quizzes** (50+ quizzes, 200+ attempts supported)  
- 📊 **Real-Time Score Calculation** on submission  
- 🗃️ **Persistent Data Handling** with MySQL (1,000+ records)  
- 🔁 **Modular OOP Design** for easy code maintenance and extension
- ⬆️ **Scalability** i.e to provide a scalable foundation for future upgrades (GUI/web version)

---

## 🛠️ Technologies Used

- **C++ (with STL)**  
- **Dev-C++ IDE**  
- **MySQL**  
- **MySQL C++ Connector**  

---

## 🚀 Getting Started

### 📌 Prerequisites

- Dev-C++ (5.11 or later)  
- MySQL Server & MySQL C++ Connector  
- MySQL DB with relevant tables created (manually or from `schema.sql`)  

---

## 🖥️ Setting Up the Project in Dev-C++

1. **Open Dev-C++**  
2. Go to `File` > `Open Project`  
3. Select `OOPS _Proj.dev` file  
4. Ensure you have added MySQL Connector libraries:  
   - Go to `Project` > `Project Options` > `Parameters` tab  
   - Under `Linker`, add:
     ```
     -lmysql
     -lmysqlcppconn
     ```

5. **Update Database Credentials** in `main.cpp`:
   ```cpp
   const char* host = "localhost";
   const char* user = "root";
   const char* password = "your_password";
   const char* database = "linquiz_db";
   ```

6. **Compile & Run** the project.  

---

## 📁 Project Structure

```
LINQUIZ/
├── OOPS _Proj.dev          # Dev-C++ project file  
├── OOPS _Proj.layout       # Dev-C++ UI layout  
├── main.cpp                # Main application code  
├── main.o                  # Object file (auto-generated)  
├── OOPS _Proj.exe          # Final executable (compiled)  
├── Makefile.win            # Auto-generated Makefile for Dev-C++  
└── schema.sql              # (Optional) SQL file to set up DB schema  
```

---

## 👤 Roles & Functionalities

### Admin
- Create quizzes dynamically.  
- Add/delete questions in a quiz.  
- Remove obsolete or redundant quizzes.  

### Student
- View available quizzes.  
- Take quizzes and get evaluated in real-time.  
- Track scores and rank compared to peers.  

---

## ✅ Sample MySQL Schema

```sql
CREATE DATABASE linquiz_db;
USE linquiz_db;

CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50),
    password VARCHAR(50),
    role ENUM('admin', 'student')
);

CREATE TABLE quizzes (
    id INT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(100)
);

CREATE TABLE questions (
    id INT AUTO_INCREMENT PRIMARY KEY,
    quiz_id INT,
    question TEXT,
    option_a VARCHAR(100),
    option_b VARCHAR(100),
    option_c VARCHAR(100),
    option_d VARCHAR(100),
    correct_option CHAR(1),
    FOREIGN KEY (quiz_id) REFERENCES quizzes(id)
);

CREATE TABLE attempts (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT,
    quiz_id INT,
    score INT,
    attempt_time TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

---

## 🙌 Contributions

Pull requests are welcome. If you'd like to propose major changes, please open an issue first to discuss what you’d like to improve.

---

