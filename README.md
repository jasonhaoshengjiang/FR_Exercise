# FR_Exercise


![Database ER diagram](https://user-images.githubusercontent.com/107166610/189266332-26175a38-e857-4220-a50e-23a2d9f4238d.jpeg)


MySQL query:
select 
    average_spend_Accepted, average_spend_Rejected, total_number_items_Accepted, total_number_items_Rejected 
from 
    (select 
        sum(totalSpent)/count(_id) as average_spend_Accepted, sum(purchasedItemCount) as total_number_items_Accepted 
      from 
        receipts 
      where 
        rewardsReceiptStatus == 'FINISHED' or rewardsReceiptStatus == 'FLAGGED') as a 
 cross join 
      (select 
          sum(totalSpent)/count(_id) as average_spend_Rejected, sum(purchasedItemCount) as total_number_items_Rejected 
       from 
          receipts 
       where 
          rewardsReceiptStatus == 'REJECTED') as b"
