# PostgreSQL Basics

This repository contains an overview of basic PostgreSQL commands, installation steps, and common SQL queries. PostgreSQL is a powerful, open-source object-relational database system with a strong reputation for reliability and performance.

## Table of Contents

1. [Download and Install PostgreSQL](#download-and-install-postgresql)
2. [Add PostgreSQL to PATH](#add-postgresql-to-path)
3. [Create Shortcuts for pgAdmin and psql Shell](#create-shortcuts-for-pgadmin-and-psql-shell)
4. [Basic PostgreSQL Commands](#basic-postgresql-commands)
5. [Data Types](#data-types)
6. [Table Management](#table-management)
7. [Query Clauses](#query-clauses-limit-offset-fetch-and-in)
8. [Indexes and Constraints](#indexes-and-constraints)
9. [Transactions](#transactions)
10. [Backup and Restore](#backup-and-restore)
11. [Advanced Queries](#advanced-queries)

## Download and Install PostgreSQL

1. Visit the official [PostgreSQL Downloads](https://www.postgresql.org/download/) page.
2. Select your operating system (Windows, macOS, or Linux).
3. Follow the installation steps provided by the PostgreSQL installer.

## Add PostgreSQL to PATH (for Windows)

1. After installation, locate the PostgreSQL installation directory (usually in `C:\Program Files\PostgreSQL\version\bin`).
2. Add this path to the system's environment variables:
   - Open "System Properties" (Right-click `This PC` → `Properties` → `Advanced system settings`).
   - Under "System Properties" → `Advanced` → Click `Environment Variables`.
   - In the "System Variables" section, find `Path` and click `Edit`.
   - Add the PostgreSQL `bin` folder to the path, and click `OK`.

## Create Shortcuts for pgAdmin and psql Shell

- **For pgAdmin (GUI):**
  1. Locate `pgAdmin 4` in your installed programs or the PostgreSQL folder.
  2. Right-click on the program → `Send to` → `Desktop (create shortcut)`.

- **For psql Shell (CLI):**
  1. Find the `SQL Shell (psql)` in the PostgreSQL directory or Start menu.
  2. Right-click on it → `Send to` → `Desktop (create shortcut)`.

## Basic PostgreSQL Commands

- **Connect to a Database:**
  ```bash
  psql -U username -d dbname
  ```

  Once connected, type `help` for help:
  ```
  You are using psql, the command-line interface to PostgreSQL.
  Type:  \copyright for distribution terms
         \h for help with SQL commands
         \? for help with psql commands
         \g or terminate with semicolon to execute query
         \q to quit
  ```

- **Get help for psql commands before connecting:**
  ```bash
  psql --help
  ```

  This displays a list of available options and their descriptions, such as:
  - `-U username` to specify the user.
  - `-d dbname` to connect to a specific database.
  - `-h host` to connect to a specific host.
  - `-p port` to specify the port number.

## Database Management

- **Create Database:**
  ```sql
  CREATE DATABASE dbname;
  ```
- **Switch to Another Database:**
  ```sql
  \c dbname
  ```
- **List Databases:**
  ```sql
  \l
  ```
- **Delete Database:**
  ```sql
  DROP DATABASE dbname;
  ```
- **Execute SQL Script from a File:**
  ```sql
  \i /path/to/file.sql
  ```

## Data Types

| Data Type         | Description                                          |
|-------------------|------------------------------------------------------|
| `INTEGER`         | Stores whole numbers                                 |
| `SERIAL`          | Auto-incrementing integer                            |
| `BIGINT`          | Stores large whole numbers                           |
| `NUMERIC(p, s)`   | Stores exact numbers with precision and scale         |
| `REAL`            | Stores floating-point numbers                        |
| `DOUBLE PRECISION`| Stores double precision floating-point numbers       |
| `VARCHAR(n)`      | Stores variable-length text, up to `n` characters     |
| `TEXT`            | Stores variable-length text (unlimited)              |
| `BOOLEAN`         | Stores `TRUE` or `FALSE`                             |
| `DATE`            | Stores a date (year, month, day)                     |
| `TIMESTAMP`       | Stores both date and time                            |
| `UUID`            | Stores universally unique identifiers                |

## Table Management

- **Create a Table with `PRIMARY KEY` and `NOT NULL`:**
  ```sql
  CREATE TABLE tablename (
      id SERIAL PRIMARY KEY,
      column1 VARCHAR(255) NOT NULL,
      column2 INTEGER NOT NULL,
      column3 DATE
  );
  ```

## Query Clauses: LIMIT, OFFSET, FETCH, and IN

- **LIMIT Clause:**
  ```sql
  SELECT * FROM tablename LIMIT 10;
  ```
- **OFFSET Clause:**
  ```sql
  SELECT * FROM tablename LIMIT 10 OFFSET 5;
  ```
- **FETCH Clause:**
  ```sql
  SELECT * FROM tablename OFFSET 5 FETCH NEXT 10 ROWS ONLY;
  ```
- **IN Clause:**
  ```sql
  SELECT * FROM tablename WHERE column IN ('value1', 'value2', 'value3');
  ```

## Indexes and Constraints

- **Create Index:**
  ```sql
  CREATE INDEX indexname ON tablename (columnname);
  ```

- **Add Foreign Key:**
  ```sql
  ALTER TABLE tablename ADD CONSTRAINT fk_name FOREIGN KEY (columnname) REFERENCES other_table (columnname);
  ```

## Transactions

- **Begin Transaction:**
  ```sql
  BEGIN;
  ```

- **Commit Transaction:**
  ```sql
  COMMIT;
  ```

- **Rollback Transaction:**
  ```sql
  ROLLBACK;
  ```

## Backup and Restore

- **Backup a Database:**
  ```bash
  pg_dump dbname > backupfile.sql
  ```

- **Restore a Database:**
  ```bash
  psql dbname < backupfile.sql
  ```

## Advanced Queries

- **Join Tables:**
  ```sql
  SELECT * FROM table1 INNER JOIN table2 ON table1.column = table2.column;
  ```

- **Group By:**
  ```sql
  SELECT column, COUNT(*) FROM tablename GROUP BY column;
  ```
