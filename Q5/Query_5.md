Questioin 5
Fetch the following data for completed order items in July of 2023
ORDER_ID
ORDER_ITEM_SEQ_ID
SHOPIFY_ORDER_ID
SHOPIFY_PRODUCT_ID

```sql
SELECT oh.order_id, oi.order_item_seq_id, oid.order_identification_type_id, gi.GOOD_IDENTIFICATION_TYPE_ID
FROM order_header oh
JOIN order_item oi USING(order_id)
JOIN order_identification oid USING(order_id)
JOIN good_identification gi USING(product_id)
JOIN order_status os USING(order_id)
WHERE os.status_id = 'order_completed' AND 
      oid.order_identification_type_id = 'SHOPIFY_ORD_ID' AND
      gi.good_identification_type_id = 'SHOPIFY_PROD_ID'
      GROUP BY oh.order_id;
```
