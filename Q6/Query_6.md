Question 6
Fetch all the physical items completed from Warehouse in September of 2023.

```sql
select *
from order_item oi
JOIN order_status as os ON os.order_id=oi.order_id and os.order_item_seq_id= oi.order_item_seq_id
JOIN order_item_ship_group_assoc as oisga on oisga.order_id=oi.ORDER_ID and oisga.ORDER_ITEM_SEQ_ID=oisga.ORDER_ITEM_SEQ_ID
JOIN order_item_ship_group as oisg on oisg.order_id=oisga.ORDER_ID and oisg.SHIP_GROUP_SEQ_ID=oisga.SHIP_GROUP_SEQ_ID
JOIN facility as f on f.FACILITY_ID=oisg.FACILITY_ID
JOIN product as p on p.product_id = oi.product_id
JOIN product_type pt on p.product_type_id= pt.product_type_id
where  pt.IS_PHYSICAL ='Y' AND
        os.status_id='item_completed'
        and   (MONTH(os.status_datetime) = 9 AND YEAR(os.status_datetime) = 2023)
         and     f.facility_type_id='WAREHOUSE';


```
