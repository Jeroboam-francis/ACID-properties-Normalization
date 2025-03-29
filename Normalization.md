
# Database Normalization – Normal Forms 1NF 2NF 3NF Table Examples

In relational databases, especially large ones, you need to arrange entries so that other maintainers and administrators can read them and work on them. This is why database normalization is important.

## What is Database Normalization?

Database normalization is a database design principle for organizing data in an organized and consistent way. It helps you avoid redundancy and maintain the integrity of the database. It also helps you eliminate undesirable characteristics associated with insertion, deletion, and updating.

## What is the Purpose of Normalization?

The main purpose of database normalization is to avoid complexities, eliminate duplicates, and organize data in a consistent way. In normalization, the data is divided into several tables linked together with relationships. Database administrators achieve these relationships using primary keys, foreign keys, and composite keys.

- **Primary key**: Uniquely identifies the rows of data in a table (e.g., employee ID, student ID, VIN).
- **Foreign key**: Relates to the primary key in another table.
- **Composite key**: Similar to a primary key, but consists of multiple columns.

## What is 1NF, 2NF, and 3NF?

1NF, 2NF, and 3NF are the first three types of database normalization, with 4NF and 5NF also existing. Each form builds upon the previous one:

- **1NF (First Normal Form)**: Ensures atomicity (single values in each cell), primary key identification, and no duplicate rows or columns.
- **2NF (Second Normal Form)**: Builds on 1NF by ensuring no partial dependency (non-key attributes fully dependent on the primary key).
- **3NF (Third Normal Form)**: Builds on 2NF by eliminating transitive partial dependency (non-prime attributes dependent on other non-prime attributes).

## Examples of 1NF, 2NF, and 3NF

### Example of 1NF

Imagine a table for a restaurant management application:

| employee_id | name  | job_code | job       | state_code | home_state |
|-------------|-------|----------|-----------|------------|------------|
| E001        | Alice | J01      | Chef      | 26         | Michigan   |
| E001        | Alice | J02      | Waiter    | 26         | Michigan   |
| E002        | Bob   | J02      | Waiter    | 56         | Wyoming    |
| E002        | Bob   | J03      | Bartender | 56         | Wyoming    |
| E003        | Alice | J01      | Chef      | 56         | Wyoming    |

All entries are atomic, and there's a composite primary key (`employee_id, job_code`), so this table is in 1NF.

### Example of 2NF

Splitting into separate tables to eliminate partial dependency:

**employee_roles Table**

| employee_id | job_code |
|-------------|----------|
| E001        | J01      |
| E001        | J02      |
| E002        | J02      |
| E002        | J03      |
| E003        | J01      |

**employees Table**

| employee_id | name  | state_code |
|-------------|-------|------------|
| E001        | Alice | 26         |
| E002        | Bob   | 56         |
| E003        | Alice | 56         |

**jobs Table**

| job_code | job       |
|----------|-----------|
| J01      | Chef      |
| J02      | Waiter    |
| J03      | Bartender |

Now, `home_state` is dependent on `state_code`.

### Example of 3NF

Further normalization to remove transitive dependency:

**states Table**

| state_code | home_state |
|------------|------------|
| 26         | Michigan   |
| 56         | Wyoming    |

Now the database is in 3NF.

## Conclusion

Database normalization ensures data is organized efficiently, reducing redundancy and dependency issues. While most databases don’t need normalization beyond 3NF, higher forms like 4NF and 5NF exist for complex data needs.
