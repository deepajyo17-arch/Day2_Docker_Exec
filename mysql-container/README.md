# Exercise 1: MySQL Database Using Docker

## Overview
- **Image:** `mysql:8.4`
- **Container name:** `mysql-lab`
- **Database:** `trainingdb`
- **Type:** Relational database
- **Container port:** `3306`

## Step 1: Start MySQL

```powershell
docker run -d `
  --name mysql-lab `
  -e MYSQL_ROOT_PASSWORD=LabPass123! `
  -e MYSQL_DATABASE=trainingdb `
  -p 127.0.0.1:3306:3306 `
  mysql:8.4
```

This command starts a MySQL container in detached mode, configures the root password, creates the database, and publishes the database port to localhost.

## Step 2: Verify the Container

```powershell
docker ps
```

```powershell
docker logs mysql-lab
```

`docker ps` displays running containers. `docker logs mysql-lab` displays the MySQL startup logs. Wait until MySQL is ready for connections.

## Step 3: Open the MySQL Shell

```powershell
docker exec -it mysql-lab mysql -uroot -p
```

Enter the root password when prompted.

## Step 4: Perform SQL Operations

### Display Available Databases

```sql
SHOW DATABASES;
```

### Select the Database

```sql
USE trainingdb;
```

### Create the Students Table

```sql
CREATE TABLE students (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    course VARCHAR(100)
);
```

### Insert Student Records

```sql
INSERT INTO students (name, course)
VALUES ('Arun', 'Docker'),
       ('Priya', 'DevOps');
```

### Read Records

```sql
SELECT * FROM students;
```

### Update a Record

```sql
UPDATE students
SET course = 'Cloud'
WHERE id = 1;
```

### Delete a Record

```sql
DELETE FROM students
WHERE id = 2;
```

### Verify the Final Records

```sql
SELECT * FROM students;
```

If all operations succeed in order, the final table should contain:

| id | name | course |
|---:|---|---|
| 1 | Arun | Cloud |

### Exit the MySQL Shell

```sql
EXIT;
```

