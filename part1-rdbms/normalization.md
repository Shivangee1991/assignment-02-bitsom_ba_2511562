#### Anomaly Analysis

### 1. Insert Anomaly
Example:
In this file, we cannot add a new product unless there is an order for it.

CSV Evidence:
- Columns: product_id, product_name, category, unit_price
- Every row (like row 0: ORD1027, row 1: ORD1114) has an order_id

Problem:
- We cannot store a new product or customer unless an order exists.


### 2. Update Anomaly
Example:
Customer information is repeated in many rows. If something changes, we must update it everywhere.

CSV Evidence:
- Customer C001 (Rohan Mehta) appears in many rows:
  - Row 1 → rohan@gmail.com
  - Row 9 → rohan@gmail.com

Problem:
- If we update one row and miss others, data becomes incorrect.


### 3. Delete Anomaly
Example:
If we delete an order, we might also lose important information.

CSV Evidence:
- If a product appears only once (like in row 0), deleting that row removes all its details.

Problem:
- Important data can be lost when deleting an order.


## Summary
- Insert problem → Cannot add data without an order  
- Update problem → Repeated data can become inconsistent  
- Delete problem → Data may get deleted accidentally  

## Normalization Justification

At first, keeping everything in one table might feel easier and simpler to manage. But in reality, it creates a lot of problems as the data increases. In this dataset, customer, product, order, and sales rep details are all mixed together, which leads to repeated data.

For example, the same customer (like C001) appears in many rows with the same email and city. If the customer updates their email, we have to change it in multiple places. If we miss even one row, the data becomes inconsistent. This clearly shows why keeping everything in one table is not practical.

There is also a problem when adding new data. If we want to add a new product that hasn’t been ordered yet, we can’t do it without creating a dummy order. That doesn’t make sense in a real system.

Deleting data is also risky. If we delete a row that contains the only record of a product or customer, we lose that information completely.

By splitting the data into separate tables like customers, products, orders, and sales reps, we avoid all these issues. Each piece of information is stored only once, making updates easier and safer.

So, normalization is not over-engineering. It actually makes the database cleaner, more organized, and much easier to maintain.