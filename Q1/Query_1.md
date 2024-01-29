Question:
Fetch the following columns for completed order items for sales orders of SM_STORE product store and that are physical items.
ORDER_ID
ORDER_ITEM_SEQ_ID
PRODUCT_ID
PRODUCT_TYPE_ID
IS_PHYSICAL
IS_DIGITAL
SALES_CHANNEL_ENUM_ID
ORDER_DATE
ENTRY_DATE
STATUS_ID
STATUS_DATETIME
ORDER_TYPE_ID
PRODUCT_STORE_ID 
```sql
select oh.order_id,oi.order_item_seq_id,p.product_id,p.product_type_id,pt.is_physical,pt.is_digital,
oh.sales_channel_enum_id,oh.order_date,oh.entry_date,oh.status_id,oh.order_type_id,oh.product_store_id
from order_header as oh
join order_item as oi using(order_id)
join order_status  as os ON oi.order_id=os.order_id AND oi.order_item_seq_id=os.order_item_seq_id
join product p using(product_id)
join product_type pt using(product_type_id)
where os.STATUS_ID='ITEM_COMPLETED'
 AND  oh.ORDER_TYPE_ID='SALES_ORDER'
 AND pt.IS_PHYSICAL ='Y' 
 AND oh.product_store_id='SM_STORE';
 ```
