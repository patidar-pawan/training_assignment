Question 4
Fetch the following columns for created orders. These should be sales orders.
ORDER_ID
TOTAL_AMOUNT
PAYMENT_METHOD
SHOPIFY_ORDER_NAME
NOTE: 
The total amount represents the total amount of the order.
The payment method is the metho

```sql
SELECT oh.order_id, oh.grand_total, opp.payment_method_id, oid.order_identification_type_id 
FROM ORDER_HEADER as oh
JOIN order_payment_preference as opp USING(order_id)
JOIN order_identification AS oid USING(order_id)
WHERE oh.order_type_id = 'SALES_ORDER' AND
      oid.order_identification_type_id = 'SHOPIFY_ORD_NAME' AND
      oh.status_id = 'order_created'
      GROUP BY oh.order_id;
```
