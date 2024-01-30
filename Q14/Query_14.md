Quetion 14 
Fetch the inventory of the products where the reason is ‘VAR_LOST’ or VAR_DAMAGED.
```sql
select p.product_id
from product p
join inventory_item  ii using(product_id)
join inventory_item_detail iid using(inventory_item_id)
where iid.reason_enum_id='VAR_LOST' or iid.reason_enum_id='VAR_DAMAGED'
```
