**Question 1:**
How many single-item orders were fulfilled from warehouses in the last month?
**Query:**
```sql
SELECT oi.order_id, oi.order_item_seq_id,count(oi.order_id) as total
FROM order_item oi  
JOIN order_status os on os.ORDER_ID=oi.order_id and os.ORDER_ITEM_SEQ_ID=oi.ORDER_ITEM_SEQ_ID
JOIN order_item_ship_group_assoc oisga ON oi.order_id = oisga.order_id AND oi.order_item_seq_id = oisga.order_item_seq_id
JOIN order_item_ship_group oisg ON oisga.order_id = oisg.order_id AND oisga.ship_group_seq_id = oisg.ship_group_seq_id
JOIN facility f ON oisg.facility_id = f.facility_id
WHERE f.facility_type_id = 'WAREHOUSE' 
and os.status_id='ITEM_COMPLETED' AND 
os.status_datetime>=DATE_SUB(curdate(),INTERVAL 1 MONTH)
GROUP BY  oi.order_id
HAVING total = 1;
```
