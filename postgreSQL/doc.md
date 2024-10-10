# PostgreSQL

## SQL commands
```SQL
INSERT INTO users (name, email) VALUES ('Ted', 'ted@gmail.com');
DELETE FROM users WHERE email='ted@gmail.com';
UPDATE users SET name='Charles' WHERE email='asdf@gmail.com';
SELECT * FROM users WHERE email='asdf@gmail.com';
SELECT * FROM users ORDER BY email;
SELECT * FROM users WHERE name LIKE '%e%';
SELECT * FROM users ORDER BY email OFFSET 1 LIMIT 2;
SELECT COUNT(*) FROM users WHERE email='asdf@gmail.com';
```
## Data types
