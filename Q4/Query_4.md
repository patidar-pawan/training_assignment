** Question 4 **
 What is the total number of orders originating from New York?
```sql
SELECT count(*)
FROM order_header oh
JOIN order_contact_mech ocm on oh.ORDER_ID=ocm.ORDER_ID
JOIN contact_mech cm on ocm.CONTACT_MECH_ID=cm.CONTACT_MECH_ID
JOIN postal_address pa on cm.contact_mech_id=pa.contact_mech_id
WHERE pa.CITY='NEW YORK'
AND ocm.CONTACT_MECH_PURPOSE_TYPE_ID='SHIPPING_LOCATION';
```
