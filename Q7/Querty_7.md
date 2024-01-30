** Question 7 **
 On a city-wise basis, what is the analysis of returns?
```sql
select distinct pa.city
from return_header rh
join return_item ri on rh.return_id=ri.return_id
join order_item oi on  ri.order_id=oi.ORDER_ID and ri.RETURN_ITEM_SEQ_ID=oi.ORDER_ITEM_SEQ_ID
join order_header  oh on oh.order_id=oi.order_id
join order_contact_mech ocm on ocm.order_id=oh.order_id
join contact_mech cm on ocm.contact_mech_id=cm.contact_mech_id
join postal_address pa on cm.contact_mech_id=pa.contact_mech_id
where rh.STATUS_ID='RETURN_COMPLETED'
group by pa.city;
```
