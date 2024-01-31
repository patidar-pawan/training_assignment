Question 13
Fetch all the products with their total quantity in August 2023.
PRODUCT_ID
PRODUCT_TYPE_ID
PRODUCT_STORE_ID, 
PRODUCT_ID, 
TOTAL_QUANTITY, 
INTERNAL_NAME, 
FACILITY_ID, 
EXTERNAL_ID, 
FACILITY_TYPE_ID, 
ORDER_HISTORY_ID, 
ORDER_ID, 
ORDER_ITEM_SEQ_ID, 
SHIP_GROUP_SEQ_ID

```sql
select p.product_id,p.PRODUCT_TYPE_ID,oh.PRODUCT_STORE_ID,count(oi.QUANTITY),p.INTERNAL_NAME,f.facility_id,f.FACILITY_TYPE_ID,oh.order_id,oi.ORDER_ITEM_SEQ_ID,oi.SHIP_GROUP_SEQ_ID
from order_header as oh
join order_item as oi using(order_id)
join order_status os using(order_id)
join order_item_ship_group_assoc as oisga on oi.ORDER_ID=oisga.ORDER_ID and oi.ORDER_ITEM_SEQ_ID=oisga.ORDER_ITEM_SEQ_ID
join order_item_ship_group as oisg on oisga.ORDER_ID=oisg.ORDER_ID and oisg.SHIP_GROUP_SEQ_ID=oisga.SHIP_GROUP_SEQ_ID
join facility as f using(facility_id)
join product as p using(product_id)
join product_type pt using(product_type_id)
where
   MONTH(os.status_datetime) = 8
  AND YEAR(os.status_datetime) = 2023
  group by p.product_id
```
