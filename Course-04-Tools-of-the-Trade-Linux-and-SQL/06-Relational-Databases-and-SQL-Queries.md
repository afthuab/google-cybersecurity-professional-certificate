# Relational Databases and SQL Queries

## 1. Relational databases in security work

Organizations store employee records, device inventories, authentication logs, and vulnerability scan results in relational databases. **Structured Query Language (SQL)** allows analysts to retrieve and filter specific records from large tables.

| Concept | Meaning | Example |
|---|---|---|
| Table | Structured collection of related records organized into rows and columns | `log_in_attempts` |
| Row (record) | A single entry in a table | One specific login event |
| Column (field) | A specific attribute tracked for every record | `username`, `login_date`, `ip_address` |
| Primary key | A column (or set of columns) that uniquely identifies each row | `event_id` or `employee_id` |
| Foreign key | A column that links a row in one table to a primary key in another table | `employee_id` inside `machines` |

## 2. Linux filtering vs. SQL filtering

| Aspect | Linux filtering (`grep`, `find`, pipes) | SQL filtering (`SELECT`, `WHERE`) |
|---|---|---|
| Data format | Unstructured or line-based text files (such as `/var/log/auth.log`) | Structured relational database tables with defined columns |
| Query approach | Pattern matching across lines of text | Column-specific queries with exact types (strings, dates, numbers) |
| Combining sources | Piping output between CLI utilities | Joining multiple tables on shared keys (`JOIN`) |

## 3. Basic SQL query structure

Every basic retrieval query specifies which columns to return (`SELECT`), which table to read (`FROM`), and optional conditions (`WHERE`) or sorting (`ORDER BY`):

```sql
SELECT event_id, username, login_date, login_time, ip_address
FROM log_in_attempts
WHERE success = 0
ORDER BY login_date DESC, login_time DESC
LIMIT 20;
```

## 4. Filtering with `WHERE` and operators

| Operator | Purpose | Example |
|---|---|---|
| `=` / `!=` (or `<>`) | Exact match or not equal | `WHERE country != 'US'` |
| `<`, `>`, `<=`, `>=` | Compare numbers, dates, or times | `WHERE login_time > '18:00:00'` |
| `BETWEEN` | Match values within an inclusive range | `WHERE login_date BETWEEN '2022-05-08' AND '2022-05-09'` |
| `LIKE` | Pattern matching with `%` (any characters) and `_` (single character) | `WHERE office LIKE 'East%'` |
| `AND` | Both conditions must be true | `WHERE success = 0 AND country = 'CA'` |
| `OR` | Either condition can be true | `WHERE department = 'Finance' OR department = 'Sales'` |
| `NOT` | Negates a condition | `WHERE NOT country LIKE 'MEX%'` |

## 5. Key point

Using `WHERE` with comparison and logical operators (`AND`, `OR`, `NOT`, `LIKE`) lets an analyst isolate specific time windows, departments, or failed authentication events without manually scanning thousands of database rows.

## References

- [PostgreSQL Documentation – Queries](https://www.postgresql.org/docs/current/queries.html)
- [W3Schools – SQL Tutorial](https://www.w3schools.com/sql/)
