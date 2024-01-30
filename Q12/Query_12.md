Quetion 12 
Get all the appeasements in July month.
How do we differentiate between returns and appeasements?
Get all the below fields 
RETURN_ID
ENTRY_DATE 
RETURN_ADJUSTMENT_TYPE_ID
AMOUNT
COMMENTS 
ORDER_ID
ORDER_DATE 
RH.RETURN_DATE, 
PRODUCT_STORE_ID
```sql

select rh.return_id,rh.entry_date,ra.return_adjustment_id,ra.amount,ra.comments,oh.order_id
,oh.order_date,rh.return_date,oh.product_store_id
from return_header rh
join return_adjustment ra on rh.return_id=ra.return_id
join order_header oh on oh.ORDER_ID=ra.order_id
WHERE ra.return_adjustment_type_id='APPEASEMENT'
 AND MONTH(rh.return_date) = 7
  AND YEAR(rh.return_date) = 2023;
```
