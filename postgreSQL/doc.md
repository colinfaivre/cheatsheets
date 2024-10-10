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
- Character sets: indexable for searching
   - CHAR(n) allocates the entire space (faster for small strings where length is known)
   - VARCHAR(n) allocates a variable amount of space depending on the data length (less space)
- Text fields: paragraphs or HTML pages - not used for indexing or sorting
  - TEXT varying length 
- Binary fields
  - BYTEA(n) up to 255 bytes
- Numeric fields
  - integer numbers
    - SMALLINT (-32768, +32768)
    - INTEGER (2 billion)
    - BIGINT (10**18 ish)
  - floating point number
    - REAL (32-bit)
    - DOUBLE PRECISION (64-bit)
    - NUMERIC(accuracy, decimal)
- Dates
  - TIMESTAMP - 'YYYY-MM-DD HH:MM:SS'
  - DATE - 'YYYY-MM-DD'
  - TIME - 'HH:MM:SS'
  - Built-in postgres function NOW()
- AUTO_INCREMENT fields
