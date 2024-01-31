** Question 8 **
How many orders with a single return were recorded in the last month?
```sql

SELECT oh.order_id,count(ri.return_id) as total
FROM return_header rh
JOIN return_item ri on ri.return_id=rh.return_id
join return_status rs on rs.return_id=ri.return_id and rs.return_item_seq_id=ri.return_item_seq_id
join order_item oi on oi.order_id=ri.order_id
join order_header oh  on oi.order_id=oh.order_id
group by oh.order_id
having total=1
```

