# Day 02 – Find Customer Referee

## SQL Schema

Table: `Customer`

| Column Name | Type    |
|-------------|---------|
| id          | int     |
| name        | varchar |
| referee_id  | int     |

- `id` is the primary key for this table.
- `referee_id` is the ID of the customer who referred this customer.
- `referee_id` may be `NULL` if no one referred the customer.

---

## Question

Find the names of customers who are either:
- Not referred by anyone (`referee_id IS NULL`)
- Referred by someone **other than** the customer with ID = 2

Return the result table in any order.

---

## Example 1

**Input:**

| id | name  | referee_id |
|----|-------|------------|
| 1  | Will  | null       |
| 2  | Jane  | null       |
| 3  | Alex  | 2          |
| 4  | Bill  | null       |
| 5  | Zack  | 1          |
| 6  | Mark  | 2          |

**Output:**

| name  |
|--------|
| Will  |
| Jane  |
| Bill  |
| Zack  |

---

## Solution

```sql
SELECT name
FROM Customer
WHERE referee_id != 2 OR referee_id IS NULL;
