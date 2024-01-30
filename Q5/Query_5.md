** Question 5 **
 In New York, which product has the highest sales?
```sql
SELECT p.product_id,count(p.product_id) as total
FROM order_header oh
JOIN order_item oi using(order_id)
JOIN order_status os using(order_id)
JOIN order_contact_mech ocm on oh.ORDER_ID=ocm.ORDER_ID
JOIN product p on oi.product_id=p.product_id
JOIN contact_mech cm on ocm.CONTACT_MECH_ID=cm.CONTACT_MECH_ID
JOIN postal_address pa on cm.contact_mech_id=pa.contact_mech_id
WHERE pa.CITY='NEW YORK'
AND ocm.CONTACT_MECH_PURPOSE_TYPE_ID='SHIPPING_LOCATION'
AND os.STATUS_ID='ORDER_COMPLETED'
GROUP BY product_id
ORDER BY total DESC
LIMIT 1
```
