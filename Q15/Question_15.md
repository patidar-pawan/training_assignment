Question 15
Find all the orders that have more than one return.

```sql
SELECT order_id, COUNT(return_id) AS return_count
FROM return_item
GROUP BY order_id
HAVING
    return_count > 1;
```
