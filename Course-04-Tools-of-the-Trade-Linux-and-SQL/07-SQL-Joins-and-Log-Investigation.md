# SQL Joins and Security Log Investigation

## 1. Why join tables?

Security data is often split across multiple tables to avoid duplication—for example, `employees` holds user names and departments, while `machines` holds workstation hostnames and operating systems, and `log_in_attempts` holds authentication events.

A **SQL `JOIN`** combines rows from two or more tables based on a related column (such as `employee_id`).

## 2. Types of SQL joins

| Join type | What rows are returned | When an analyst uses it |
|---|---|---|
| `INNER JOIN` | Only rows where the key matches in **both** tables | Correlating employees who currently have an assigned workstation |
| `LEFT JOIN` | All rows from the **left** table, plus matching rows from the right table (`NULL` if no match) | Listing all employees and spotting anyone missing an assigned device |
| `RIGHT JOIN` | All rows from the **right** table, plus matching rows from the left table (`NULL` if no match) | Listing all registered machines and finding unassigned devices |
| `FULL OUTER JOIN` | All rows from **both** tables, matching where possible and filling `NULL` otherwise | Auditing mismatches between HR employee rosters and IT asset tables |

## 3. Worked SQL join examples (simulated tables)

Assume two fictional tables:
- `employees` (`employee_id`, `username`, `department`, `office`)
- `machines` (`device_id`, `hostname`, `operating_system`, `employee_id`)

### Find all employees and their assigned computers (`INNER JOIN`)

```sql
SELECT
    employees.employee_id,
    employees.username,
    employees.department,
    machines.hostname,
    machines.operating_system
FROM employees
INNER JOIN machines
    ON employees.employee_id = machines.employee_id;
```

### Find machines that are not assigned to any employee (`RIGHT JOIN` with `IS NULL`)

```sql
SELECT
    machines.device_id,
    machines.hostname,
    machines.operating_system
FROM employees
RIGHT JOIN machines
    ON employees.employee_id = machines.employee_id
WHERE employees.employee_id IS NULL;
```

Unassigned machines still active on the network can represent forgotten test hosts or rogue devices that need investigation.

### Find employees in Engineering running an outdated OS (`INNER JOIN` + `WHERE`)

```sql
SELECT
    employees.username,
    employees.department,
    machines.hostname,
    machines.operating_system
FROM employees
INNER JOIN machines
    ON employees.employee_id = machines.employee_id
WHERE employees.department = 'Engineering'
  AND machines.operating_system LIKE 'Windows 10%';
```

## 4. Key point

`INNER JOIN` narrows results to matched records across tables, while `LEFT JOIN` and `RIGHT JOIN` help surface gaps such as unmonitored endpoints or orphaned accounts.

## References

- [PostgreSQL Documentation – Joins Between Tables](https://www.postgresql.org/docs/current/tutorial-join.html)
- [SQLite Documentation – SELECT and JOIN](https://www.sqlite.org/lang_select.html)
