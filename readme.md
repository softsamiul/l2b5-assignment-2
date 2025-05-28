<!-- Assignment 2 -->
#### 3. Explain the Primary Key and Foreign Key concepts in PostgreSQL.

Ans: 
- ```Primary Key```: Primary key হলো একটি বা কয়েকটি কলামের কম্বিনেশন যেটা একটা টেবিলের রো কে Uniquely আইডেন্টিফাই করে।

বৈশিষ্ট্য: 
১. Primary key কে অবশ্যয় unique হতে হবে।
২. এটা NULL হতে পারবে না।
৩. একটা টেবিলের একটিই Primary key থাকবে।
৪. এটা অটোমেটিক্যালি unique index তৈরি করে।

```sql
---Example code:
CREATE TABLE customers(
    customer_id SERIAL PRIMARY KEY,
    "name" VARCHAR(25),
    email VARCHAR(50)
)
```
এখানে customer_id হল Primary key.

- ```Foriegn key:``` Foriegn key হল একটি বা কয়েকটি কলামের কম্বিনেশন যেটা অন্য কোনো টেবিলের Primary key এবং এটা দুটো টেবিলের সাথে relation তৈরি করে।

বৈশিষ্ট্য:
১. দুটো টেবিলের মধ্যে সম্পর্ক তৈরি করে।
২. এটা NULL হবে না।
৩. এটা অবশ্যয় অন্য টেবিলের Primary key।

```sql
---Example Code:
CREATE TABLE orders (
    oder_id SERIAL PRIMARY KEY,
    customer_id INT REFERENCES customers(customer_id),
    order_date DATE NOT NULL
)
```
এখানে customer_id হল Foriegn key.

#### 4. What is the difference between the VARCHAR and CHAR data types?

Ans: 
VARCHAR ও CHAR এর মধ্যে মুল পার্থক্য হল যে কিভাবে তারা ডাটা store করে। 

- ```VARCHAR:``` VARCHAR স্ট্রিং টাইপের ডাটা store করে এবং এখানে character length store করে n নম্বর পর্যন্ত। এখানে টেবিল তৈরি করার সময় বলে দেওয়া যাই যে আমরা maximum কত লেংথের ডাটা রাখতে পারব। যেই লেংথ দেওয়া হবে maximum সেই পর্যন্ত ডাটা রাখা যাবে। তার কম দিলে ও সমস্যা 
```sql
--- VARCHAR 
VARCHAR(5)
```

- ```CHAR:``` CHAR মূলত VARCHAR এর মতই স্ট্রিং টাইপের ডাটা store করে কিন্তু এখানে CHAR define করার সময় যেই লেংথ দেওয়া হবে সেই exact লেংথের ডাটা রাখেতে হবে কম বেশি রাখা যাবে না। 
```sql
--- CHAR
CHAR(5)
```
#### 5. Explain the purpose of the WHERE clause in a SELECT statement.

Ans: 
SELECT : SELECT মূলত ব্যবহার করা হয় ডাটা query করে ফিল্টার করে নিয়ে আসতে। 
WHERE: WHERE ব্যবহার করা হয় ডাটা query করে ফিল্টার করার সময় লজিক build করতে।  নিচে কোড example দেওয়া হল।
```sql
-- SELECT
SELECT * FROM customer;

-- WHERE
SELECT "name", email FROM customer
    WHERE "name" = 'Sam'

-- Here we can use
-- Comparison operators: =, !=, <, >, <=, >=
-- Logical operators: AND, OR, NOT
-- Pattern matching: LIKE, ILIKE
-- Range checking: BETWEEN, IN
-- Null checking: IS NULL, IS NOT NULL
```

#### 6. What are the LIMIT and OFFSET clauses used for?

Ans:  LIMIT ও OFFSET

- `LIMIT` : নির্দিষ্ট সংখ্যক সারি (row) রিটার্ন করতে ব্যবহার হয়।
- `OFFSET` : কতটি সারি স্কিপ করে তারপর ফলাফল দেখাবে তা নির্ধারণ করে।

উদাহরণ (Pagination):
```sql
SELECT * FROM products
LIMIT 5 OFFSET 10;
```

#### 7. How can you modify data using UPDATE statements?
Ans: UPDATE দিয়ে ডেটা পরিবর্তন

`UPDATE` স্টেটমেন্ট ব্যবহার করে টেবিলের বিদ্যমান ডেটা পরিবর্তন করা হয়।

```sql
UPDATE table_name
SET column1 = value1,
    column2 = value2
WHERE condition;
```


