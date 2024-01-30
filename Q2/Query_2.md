** Question 2 **
 Leading up to the New Year, what is the count of orders shipped from stores in the 25 days preceding the New Year?
 ``` sql
 select count(*)
 from order_item oi
 JOIN order_item_ship_group_assoc oisga ON oi.order_id = oisga.order_id AND oi.order_item_seq_id = oisga.order_item_seq_id
JOIN order_item_ship_group oisg ON oisga.order_id = oisg.order_id AND oisga.ship_group_seq_id = oisg.ship_group_seq_id
join shipment s on oisg.order_id=s.primary_order_id and oisg.ship_group_seq_id=s.primary_ship_group_seq_id
 join shipment_status ss on s.shipment_id=ss.shipment_id
JOIN facility f ON oisg.facility_id = f.facility_id
join facility_type ft on f.FACILITY_TYPE_ID=ft.FACILITY_TYPE_ID
where ft.PARENT_TYPE_ID='PHYSICAL_STORE'
and ss.status_id='SHIPMENT_SHIPPED'
and ss.status_date >= '2023-12-07'
  AND ss.status_date < '2024-01-01';
```
 
