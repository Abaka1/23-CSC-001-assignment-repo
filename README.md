# ABAKA, LINUS EBEBE
# 23/CSC/001
# CSC 282
# REGISTRATION SYSTEM


## Project Structure

```
student-registration-app
├── src
│   ├── config
│   │   └── db.php          # Database connection settings
│   ├── process.php         # Handles form submission and data validation
│   ├── view.php            # Displays all registered students
│   ├── delete.php          # Processes deletion of student records
│   └── index.php           # Landing page with registration form
├── README.md               # Project documentation
```

## Setup Instructions

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd abaka_student_system
   ```

2. **Create a MySQL database**:
   Create a database named `abaka_students` and a table named `new_records` with the following structure:
   ```sql
   CREATE TABLE student_records (
       id INT AUTO_INCREMENT PRIMARY KEY,
       full_name VARCHAR(100) NOT NULL,
       email VARCHAR(100) NOT NULL,
       department VARCHAR(100) NOT NULL,
       matric_number VARCHAR(50) NOT NULL
   );
   ```

3. **Configure the database connection**:
   Edit the `db.php` file to include your database credentials:
   ```php
   <?php
   $host = 'localhost';
   $db   = 'student_registration';
   $user = 'your_username';
   $pass = 'your_password';
   $charset = 'utf8mb4';

   $dsn = "mysql:host=$host;dbname=$db;charset=$charset";
   $options = [
       PDO::ATTR_ERRMODE            => PDO::ERRMODE_EXCEPTION,
       PDO::ATTR_DEFAULT_FETCH_MODE => PDO::FETCH_ASSOC,
       PDO::ATTR_EMULATE_PREPARES   => false,
   ];

   try {
       $pdo = new PDO($dsn, $user, $pass, $options);
   } catch (\PDOException $e) {
       throw new \PDOException($e->getMessage(), (int)$e->getCode());
   }
   ```

4. **Run the application**:
   Open `index.php` in your web browser to access the registration form. Fill in the details and submit to register a student.

