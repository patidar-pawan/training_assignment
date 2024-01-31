Question 10
Fetch all the order items that are in the created status and the order type should be a sales order
ORDER_ID
PRODUCT_TYPE_ID
ORDER_LINE_ID
EXTERNAL_ID
SALES_CHANNEL
QUANTITY
ITEM_STATUS 
PRODUCT_ID
BILL_CITY
BILL_COUNTRY
BILL_POSTALCODE
BILL_ADDRESS1
BILL_ADDRESS2
SHIP_CITY
SHIP_COUNTRY
SHIP_POSTALCODE
SHIP_ADDRESS1
SHIP_ADDRESS2
```sql
SELECT oh.order_id,p.product_type_id,oi.order_item_seq_id,oh.external_id,oh.SALES_CHANNEL_ENUM_ID,oi.quantity,oi.status_id,p.product_id,
pa1.city,pa1.county_geo_id,pa1.address1,pa1.address2,pa2.city,pa2.county_geo_id,pa2.address1,pa2.address2
FROM 
  order_header oh
  JOIN order_item oi ON oi.order_id = oh.order_id
  JOIN product p ON p.product_id = oi.product_id
  JOIN order_contact_mech ocm ON oh.order_id = ocm.order_id
  JOIN contact_mech cm ON ocm.contact_mech_id = cm.contact_mech_id
  LEFT JOIN postal_address pa1 ON cm.contact_mech_id = pa1.contact_mech_id AND ocm.contact_mech_purpose_type_id = 'BILLING_LOCATION'
  LEFT JOIN postal_address pa2 ON pa1.contact_mech_id=pa2.contact_mech_id AND ocm.contact_mech_purpose_type_id = 'SHIPPING_LOCATION'
WHERE oi.status_id='ITEM_CREATED'
and oh.order_type_id='SALES_ORDER';
```
