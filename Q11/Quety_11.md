Question 11
Fetch all the customers in June 2023.
```sql
select pt.party_id,pt.party_type_id,pr.ROLE_TYPE_ID
from party as pt
join party_role as pr using(party_id)
where pt.status_id ='PARTY_ENABLED'AND  pr.ROLE_TYPE_ID='CUSTOMER'
AND 
MONTH(pt.created_date) = 6 AND YEAR(pt.created_date) = 2023;
```
