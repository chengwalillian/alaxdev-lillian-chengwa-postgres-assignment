
# PostgreSQL Setup and Students Schema

This guide documents Luxdev tutorial steps on 30th and 31st July 2025 to install PostgreSQL, create a schema, grant privileges to a user, and create a sample table with metadata.

 1. Install PostgreSQL (Ubuntu 24.04.2 LTS)

sudo apt update
sudo apt install postgresql postgresql-contrib

 2. Log into PostgreSQL as the default user
sudo -i -u postgres
psql

 3. Create PostgreSQL User

CREATE USER lillianchengwa WITH PASSWORD 'lillian_chengwa_students_password';


 4. Create Schema

CREATE SCHEMA students AUTHORIZATION lillianchengwa;

 5. Grant Privileges to the User

Grant usagee on schema students TO lillianchengwa;
Grant create students TO lillianchengwa;

 6. create table students

  (first_name varchar (50),
  last_name varchar (50),
  phone_number char(10),
  email text unique not null,
  age int,
  fee_paid numeric);


 7. Insert Sample Data 

Insert into students 
(first_name,last_name,phone_number,email,age,fee_paid)
values
('Patrick', 'Mwenda', '0707959533', 'patrickm@gmail.com',50, 12500),
('Stella', 'Mweni', '0721546357', 'stellatheone@gmail.com', 18, 35000),
('Lillian','Chengwa','0729204304',' chen@gmail.com',22, 30000);

8.alter table students
add column comments varchar(50);

select * from students;


 
