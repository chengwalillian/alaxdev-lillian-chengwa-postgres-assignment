````markdown
# PostgreSQL Setup and Students Schema

This guide documents the steps to install PostgreSQL, create a schema, grant privileges to a user, and create a sample table with metadata.

---

## ✅ 1. Install PostgreSQL (Ubuntu 24.04.2 LTS)

```bash
sudo apt update
sudo apt install postgresql postgresql-contrib
````

---

## ✅ 2. Log into PostgreSQL as the default user

```bash
sudo -i -u postgres
psql
```

---

## ✅ 3. Create PostgreSQL User

```sql
CREATE USER lillianchengwa WITH PASSWORD 'lillian_chengwa_students_password';
```

---

## ✅ 4. Create Schema

```sql
CREATE SCHEMA students AUTHORIZATION lillianchengwa;
```

---

## ✅ 5. Grant Privileges to the User

```sql
GRANT USAGE ON SCHEMA students TO lillianchengwa;
GRANT CREATE ON SCHEMA students TO lillianchengwa;
```

---

## ✅ 6. Create Table `student_info` with Metadata

```sql
CREATE TABLE students.student_info (
    id SERIAL PRIMARY KEY,
    firstname VARCHAR(50),
    lastname VARCHAR(50),
    phonenumber VARCHAR(20),
    email VARCHAR(100),
    age INT,
    schoolfees NUMERIC(10,2)
);
```

---

## ✅ 7. Insert Sample Data 

```sql
INSERT INTO students.student_info (firstname, lastname, phonenumber, email, age, schoolfees)
VALUES
('Lillian', 'Chengwa', '0729204204', 'lillianchengwa@gmail.com', 34, 7000.00),
('Nigel', 'Njagi', '0727888701', 'nigelnjagi@gmail.com', 13, 2000.00);
```

---

## ✅ Notes

* The schema `students` is owned by `lillianchengwa`.
* The table `student_info` resides within the `students` schema.
* Use DBeaver or `psql` CLI to view or manage the data.

```
