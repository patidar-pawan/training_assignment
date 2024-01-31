Question 8
Find all the orders whose two or more items are completed but the orders are still in the approved status.
```sql
SELECT oh.ORDER_ID,oh.ORDER_NAME,
    COUNT(DISTINCT oi.ORDER_ITEM_SEQ_ID) AS Completed_Items_Count
FROM Order_Header oh
JOIN Order_Item oi ON oh.ORDER_ID = oi.ORDER_ID

WHERE
    oh.STATUS_ID = 'ORDER_APPROVED'
    AND oi.STATUS_ID = 'ITEM_COMPLETED'
GROUP BY
    oh.ORDER_ID
HAVING
    Completed_Items_Count >= 2;
```
