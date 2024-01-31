Question 2
Fetch the following columns for completed return items of SM_STORE for ecom return channel.
RETURN_ID 
ORDER_ID
PRODUCT_STORE_ID 
STATUS_DATETIME
ORDER_NAME 
FROM_PARTY_ID 
RETURN_DATE 
ENTRY_DATE
RETURN_CHANNEL_ENUM_ID

```sql
SELECT rh.return_id, oi.order_id, oh.product_store_id,
rs.status_datetime,oh.order_name,rh.return_date,rh.entry_date,rh.return_channel_enum_id,rh.from_party_id
FROM return_header AS rh
JOIN return_adjustment AS ra ON rh.return_id = ra.return_id
JOIN return_item AS ri ON rh.return_id = ri.return_id
JOIN order_item AS oi ON ri.order_id = oi.order_id and ri.order_item_seq_id=oi.order_item_seq_id
JOIN order_header AS oh ON oi.order_id = oh.order_id
JOIN return_status AS rs ON rs.return_id = ri.return_id and ri.return_item_seq_id=rs.RETURN_ITEM_SEQ_ID
where rs.status_id='RETURN_COMPLETED'
AND oh.product_store_id='SM_STORE'
AND rh.return_channel_enum_id ='ECOM_RTN_CHANNEL'
```
