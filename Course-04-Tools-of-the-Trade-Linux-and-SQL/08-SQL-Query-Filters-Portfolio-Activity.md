# Portfolio Activity: Apply Filters to SQL Queries

## 1. Purpose

This portfolio activity demonstrates how to filter security-relevant records from relational database tables using `SELECT`, `FROM`, and `WHERE` with `AND`, `OR`, `NOT`, and `LIKE`.

This write-up is an independently documented summary based on the Course 4 Module 4 lab scenario (`Apply filters to SQL queries`). All queries reflect the lab's simulated database tables (`log_in_attempts` and `employees`) and do not access real organizational data.

## 2. Scenario

The organization is investigating suspicious authentication activity and identifying employee workstations that require software updates. To support both tasks, I wrote six SQL queries against two tables in the lab database:

- **`log_in_attempts`:** Contains authentication records including `event_id`, `username`, `login_date`, `login_time`, `country`, `ip_address`, and `success`.
- **`employees`:** Contains staff and location details including `employee_id`, `device_id`, `username`, `department`, and `office`.

## 3. Investigation and asset-scoping queries

### 1. Retrieve after-hours failed login attempts

Identify failed login attempts (`success = FALSE`, or `0` in SQLite/MySQL) occurring after `18:00:00`:

```sql
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00:00'
  AND success = FALSE;
```

**Purpose:** Isolates unsuccessful sign-in attempts outside standard working hours, which can point to automated credential-stuffing or brute-force activity.

---

### 2. Retrieve login attempts on specific dates

Retrieve all login attempts recorded on `2022-05-08` or `2022-05-09` during a suspicious activity window:

```sql
SELECT *
FROM log_in_attempts
WHERE login_date = '2022-05-08'
   OR login_date = '2022-05-09';
```

**Purpose:** Narrows authentication logs to the exact dates of a suspected security incident to review both failed and successful logins.

---

### 3. Retrieve login attempts outside of Mexico

Filter for login attempts originating outside Mexico, accounting for inconsistent country labels (`'MEX'` and `'MEXICO'`) using `NOT` and `LIKE`:

```sql
SELECT *
FROM log_in_attempts
WHERE NOT country LIKE 'MEX%';
```

**Purpose:** Surfaces international login activity that falls outside expected domestic user locations.

---

### 4. Retrieve employees in Marketing located in the East building

Identify employees in the `Marketing` department whose office identifier starts with `East` (such as `East 170` or `East-320`):

```sql
SELECT *
FROM employees
WHERE department = 'Marketing'
  AND office LIKE 'East%';
```

**Purpose:** Scopes targeted workstation updates to a specific department and building wing.

---

### 5. Retrieve employees in Finance or Sales

Identify employees belonging to either the `Finance` or `Sales` departments:

```sql
SELECT *
FROM employees
WHERE department = 'Finance'
   OR department = 'Sales';
```

**Purpose:** Builds a list of staff in `Finance` and `Sales` so IT can roll out scheduled machine updates to those teams.

---

### 6. Retrieve all employees not in IT

Identify all employees outside the `Information Technology` (`IT`) department whose machines have not yet been updated:

```sql
SELECT *
FROM employees
WHERE NOT department = 'IT';
```

**Purpose:** Excludes `IT` staff (whose systems were already patched) and returns the remaining employee records requiring updates.

## 4. Key learning

Combining `WHERE` with `AND`, `OR`, `NOT`, and wildcard patterns (`LIKE 'MEX%'`, `LIKE 'East%'`) handles real-world data variations cleanly and keeps investigation results focused.

## References

- [PostgreSQL Documentation – WHERE Clause](https://www.postgresql.org/docs/current/sql-select.html#SQL-WHERE)
- [OWASP – Logging Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html)
