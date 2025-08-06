# Day 04 – Article Views I

## Problem: [1148. Article Views I](https://leetcode.com/problems/article-views-i/)

### SQL Schema

Table: `Views`

| Column Name | Type |
|-------------|------|
| article_id  | int  |
| author_id   | int  |
| viewer_id   | int  |
| view_date   | date |

- This table may contain duplicate rows.
- Each row shows that `viewer_id` viewed an article written by `author_id` on `view_date`.
- If `author_id = viewer_id`, it means the author viewed their **own** article.

---

## Task

Write a SQL query to find the IDs of all authors who **viewed at least one of their own articles**.

Return the result sorted by `id` in ascending order.

---

## Example

**Input:**

| article_id | author_id | viewer_id | view_date  |
|------------|-----------|-----------|------------|
| 1          | 3         | 5         | 2019-08-01 |
| 1          | 3         | 6         | 2019-08-02 |
| 2          | 7         | 7         | 2019-08-01 |
| 2          | 7         | 6         | 2019-08-02 |
| 4          | 7         | 1         | 2019-07-22 |
| 3          | 4         | 4         | 2019-07-21 |
| 3          | 4         | 4         | 2019-07-21 |

**Output:**

| id  |
|-----|
| 4   |
| 7   |

---

## Solution

```sql
SELECT DISTINCT author_id AS id
FROM Views
WHERE author_id = viewer_id
ORDER BY id ASC;
