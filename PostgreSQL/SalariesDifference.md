## Dropbox

### Data Analyst

### Escribe una consulta que calcule la diferencia entre los salarios más altos encontrados en los departamentos de marketing e ingeniería. Busca obtener sólo la diferencia entre los salarios mas altos.

### Solucion

```sql
with marketingsalary AS (
SELECT salary, department
FROM db_employee JOIN db_dept
ON db_employee.department_id = db_dept.id
WHERE department = 'marketing'
ORDER BY salary DESC
LIMIT 1
),

engineeringsalary AS (
SELECT salary, department
FROM db_employee JOIN db_dept
ON db_employee.department_id = db_dept.id
WHERE department = 'engineering'
ORDER BY salary DESC
LIMIT 1
)

SELECT 
    (SELECT marketingsalary.salary FROM marketingsalary) -
    (SELECT engineeringsalary.salary FROM engineeringsalary) AS salary_difference

```

### Resultado

```sql
salary_difference

2400
```