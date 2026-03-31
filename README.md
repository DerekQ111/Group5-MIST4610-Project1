
# Team Name

21479 Group 5




## Team Members
Sydney James -  [@srj44873](https://github.com/srj44873)

Mary Earhart -  [@marykearhart](https://github.com/marykearhart)

Derek Quinlan - [@derekq111](https://github.com/derekq111)

Regan Taylor - [@nrt19057](https://github.com/nrt19057)
## Problem Description
  Our group handled the task of creating a data model for our franchise "Loaded Tea" company. Our business is operated in variious locations around the US, each with their own employees lead by department chairs in Human Resources and Franchise Coordination. Additionally, our model accounts for the unformation stored on the customers at each location, their eligibility for military and student discounts, and the supplier-to-business coordination of supply orders aside from those purchases made directly from the location by the customer. Our overarching goals of this project were to accurately display each relationship between entities, create sample data tables for each entity and its attributes, and finally test out various queries relevant tov the business operations of our organization.

## Data Model
<img width="1060" height="413" alt="Screenshot 2026-03-29 at 4 11 20 PM" src="https://github.com/user-attachments/assets/47a9a5a7-d151-457f-a64f-f658ee9c2f93" />

# Data Model:
  Our data model focuses on a Loaded Tea company that functions as a franchise with many different locations across the United States. We started with our customer entity, indicating all of the relevant data stored on our customers ranging from atibutes of name, address, and contact information. For each customer, there are many sales, which we indicated through a one to many relationship with our sales entity. 
  
  The Sales entity displays data on the date, price and the payment method chosen by the customer for each sale. Additionally, the Sales entity contains two foreign keys- CustomerID and ProgramID- to represent the customers making each sale and whether they qualified for any discount programs (Military or Student). This then brings is to the Discount Programs table, which contains the program name and the percentage discount for each program offered for each. In this scenario, our company only offers Military and Student discounts, with military granting a 30% decrease in prices and Student granting a 20% decrease. For the sake of the complexity of our data model, we assume that all customers' sales will apply for one of these discounts. This Discount Program table also connects to the customers table as each customer can qualify for many discount programs in a one-to-many relationship.
  
  Similar to the relationship between sales and customers, Customer Orders and Customers also experience a one-to-many relationship as each customer can have many orders, but each order can only belong to one customer. This entity is differentiated from the sales table as those purchases were made online rather than at a specific franchise location. As an individual entity, Customer Orders stores the monetary amount of each order and the date the order was placed. 

  Considering that many orders can contain many products, we developed the associative identity labeled Customer Order Details to indicate this relationship between Customer Orders and Products. In this entity, we have the product ID and order ID for each, as well as the shipping date, status of the order, price, and quantity of items in the order. For the sake of this data model, we assume that the customer orders all have a scheduled date of which they will be shipped out, even if they are still being processed and have not yet shipped. We also assume that orders which are cancelled will not appear in the table any longer, and that customers are limited to the purchase of 20 items when choosing to by online instead of in person.
  
  Next is our product entity which keeps track of the different flavors and types of drinks offered by our company, specifically either Loaded Teas or Beauty Shakes in various fruity flavors. This table indicates a many-to-many relationship with the sales table as many sales can contain many different products, and vice versa. This relationship is held together by an associative identity labeled product line. This entity is non-identifiable and serves as a holding place for each identifiable entity's foreign keys.

  Many products in the product entity can also go to many store locations, hence the many-to-many connection between Store Location and Products.  The Store Locations entity is comprised of attributes including each store's area code, city, and state. This entity is also connected with the Employees table signifying that many employees can work at one store location, while each employee can only work at one location. 
  
  Together these two tables form the associative identity labeled "Supplier Orders", which contains the foreign keys of each individual entity with no other salient attributes. For completeness, we specify Supplier Orders as to differentiate from orders placed by the customers that come directly from the stock at the store locations versus the franchises purchasing more inventory to sell to customers. But the supplies in these orders must come from a home base, which brings us to our Supplier entity containing individual supplier IDs for each company, as well as their company name.

  Last, the Employees entity is the most complex of our entities, containing information on each employee's name, email, department name, and foreign keys identifying their respective store location and department chair. The department chair identifier is represented by a one-to-many recursive relationship, as one department chair can observe many employees.

## Data Dictionary
<img width="641" height="496" alt="Screenshot 2026-03-29 at 4 27 11 PM" src="https://github.com/user-attachments/assets/87ed6a7b-8bb0-4e4d-9598-0fc36a83eaca" />

<img width="660" height="406" alt="Screenshot 2026-03-29 at 4 27 44 PM" src="https://github.com/user-attachments/assets/eb48391b-9752-47ca-a987-a6ded5e32890" />

<img width="652" height="440" alt="Screenshot 2026-03-29 at 4 25 25 PM" src="https://github.com/user-attachments/assets/3300f454-2628-4774-832d-78c5da00fea1" />

<img width="648" height="264" alt="Screenshot 2026-03-29 at 4 25 57 PM" src="https://github.com/user-attachments/assets/90f29817-b8ce-4632-bb81-f2c1181f3fd2" />

<img width="680" height="566" alt="Screenshot 2026-03-29 at 4 26 39 PM" src="https://github.com/user-attachments/assets/8ead3a2f-e988-4ded-a997-73f47b4c66b1" />

<img width="673" height="685" alt="Screenshot 2026-03-29 at 4 26 20 PM" src="https://github.com/user-attachments/assets/63f8986b-b936-4e76-9c21-830cc839aa62" />

<img width="656" height="336" alt="Screenshot 2026-03-29 at 4 28 03 PM" src="https://github.com/user-attachments/assets/0b8bd174-71bf-406c-b746-5a77ca98df96" />

<img width="641" height="289" alt="Screenshot 2026-03-29 at 4 29 28 PM" src="https://github.com/user-attachments/assets/8644030b-9c52-47d1-9a65-352731a57021" />

<img width="642" height="430" alt="Screenshot 2026-03-29 at 4 29 48 PM" src="https://github.com/user-attachments/assets/00ad1f08-dbdf-4336-ab01-91adb75bb999" />

<img width="645" height="365" alt="Screenshot 2026-03-29 at 4 30 06 PM" src="https://github.com/user-attachments/assets/ff9e33d1-d6cb-41e4-be94-07d7e1d14c5d" />

<img width="643" height="302" alt="Screenshot 2026-03-29 at 4 30 29 PM" src="https://github.com/user-attachments/assets/c5a17fa4-2fda-4eed-8b50-e705278b1f6c" />

<img width="659" height="248" alt="Screenshot 2026-03-29 at 4 30 49 PM" src="https://github.com/user-attachments/assets/acc3165a-544e-4fab-9658-6e9513fba186" />

## Queries
<img width="717" height="336" alt="Screenshot 2026-03-29 at 5 16 21 PM" src="https://github.com/user-attachments/assets/980bfdf3-5a8b-468f-bc49-639a2e572fc1" />


  1. Query 1 - Simple Question: What customers are currently in the database? Why it matters: A manager may want a full customer list for outreach, customer service, or record review.

SELECT customerID, firstName, lastName, emailAddress, phoneNumber FROM Customers ORDER BY lastName, firstName;

Query Response: <img width="539" height="362" alt="Q1" src="https://github.com/user-attachments/assets/c2ee7f04-aa37-4391-99eb-7483eadc4860" />


Natural Language Description: This query retrieves all customers in the database, displaying their ID, first name, last name, email address, and phone number. The results are sorted alphabetically by last name and first name.

Managerial Relevance: Managers use this query to maintain an up-to-date customer directory. It supports customer outreach, verifies stored contact information, and helps ensure accurate records for communication and service.

  2. Query 2 - Simple Question: What products does the business carry? Why it matters: A manager may want a current list of products for catalog review, sales planning, or inventory coordination.

SELECT productID, productName, productType FROM Products ORDER BY productType, productName;

Query Response: <img width="404" height="326" alt="Screenshot 2026-03-30 203739" src="https://github.com/user-attachments/assets/2ab0b99f-55be-48aa-831e-21b82668f7ec" />


Natural Language Description:This query lists all products, including product ID, name, and type. The results are organized by product type and then alphabetically by product name.

Managerial Relevance:Managers can review the full product catalog to support sales planning, marketing strategies, and inventory management. It ensures the business has a clear understanding of its offerings.

  3. Query 3 - Simple Question: What suppliers are in the system? Why it matters: A manager may need a supplier directory when reviewing vendor relationships or sourcing issues.

SELECT SupplierID, supName FROM Suppliers ORDER BY supName;

Query Response:<img width="367" height="269" alt="Q3" src="https://github.com/user-attachments/assets/cee84f2b-31e0-4cac-bbee-d89d3cb2bd73" />


Natural Language Description:This query retrieves all suppliers along with their IDs and names, sorted alphabetically.

Managerial Relevance:Managers use this to evaluate vendor relationships, identify sourcing options, and confirm supplier records when making purchasing or supply chain decisions.

  4. Query 4 - Simple Question: What store locations are recorded in the database? Why it matters: A manager may want to review all operating locations for staffing or supplier coordination.

SELECT LocationID, city, state, areaCode FROM Store Location ORDER BY state, city;

Query Response: <img width="395" height="161" alt="Q4" src="https://github.com/user-attachments/assets/42f280db-44da-4867-bd04-1f343655fbf6" />


Natural Language Description:This query returns all store locations, including location ID, city, state, and area code. Results are sorted geographically.

Managerial Relevance:Managers can use this to analyze regional operations, allocate resources, coordinate staffing, and ensure all store locations are properly tracked.

5. Query 5 - Complex Question: Which customers have generated the most total order revenue? Why it matters: A manager can use this to identify the highest-value customers and focus retention efforts on them.

SELECT c.customerID, c.firstName, c.lastName, SUM(o.amount) AS total_spent FROM Customers c JOIN Orders o ON c.customerID = o.customerID GROUP BY c.customerID, c.firstName, c.lastName ORDER BY total_spent DESC;

Query Response: <img width="464" height="281" alt="Q5" src="https://github.com/user-attachments/assets/8e14a444-fbf2-4893-bdae-c7d33c5ff13c" />


Natural Language Description:This query joins Customers and Orders to calculate total spending per customer using SUM. Results are grouped by customer and sorted from highest to lowest spending.

Managerial Relevance:Managers can identify high-value customers and prioritize retention strategies, loyalty programs, and personalized marketing to maximize long-term revenue.

  6. Query 6 - Complex Question: Which products have sold the highest total quantity? Why it matters: A manager can use this to identify top-selling products and make pricing, stocking, and promotion decisions.

SELECT p.productID, p.productName, p.productType, SUM(od.orderqty) AS total_quantity_sold FROM Products p JOIN Order Details od ON p.productID = od.productID GROUP BY p.productID, p.productName, p.productType ORDER BY total_quantity_sold DESC;

Query Response:  <img width="539" height="312" alt="Q6" src="https://github.com/user-attachments/assets/a8f9db3e-e745-463a-95b4-d654365cd77a" />


Natural Language Description:This query joins Products and Order Details and calculates the total quantity sold for each product using SUM. Results are grouped and ranked by quantity sold.

Managerial Relevance:Managers use this to identify high-demand products, optimize inventory levels, and ensure popular products remain in stock.

  7. Query 7 - Complex Question: Which products have generated the most order revenue? Why it matters: A manager can use this to distinguish products that drive revenue, not just volume.

SELECT p.productID, p.productName, SUM(od.orderPrice * od.orderqty) AS total_product_revenue FROM Products p JOIN Order Details od ON p.productID = od.productID GROUP BY p.productID, p.productName ORDER BY total_product_revenue DESC;

Query Response:  <img width="600" height="315" alt="Q7" src="https://github.com/user-attachments/assets/56b07101-7173-41a0-8db2-048ed7b6c502" />


Natural Language Description:This query calculates total revenue per product by multiplying price and quantity, then summing across all orders. Results are grouped and sorted by revenue.

Managerial Relevance:Managers can distinguish between products that sell frequently and those that generate the most profit, helping guide pricing, promotions, and product prioritization.

  8. QQuery 8 - Complex Question: Which products have been ordered less frequently than average? Why it matters: A manager can use this to identify underperforming products that may need promotion, discounting, or discontinuation.

SELECT p.productID, p.productName, p.productType, COUNT(od.orderID) AS order_count
FROM Products p
LEFT JOIN CustomerOrderDetails od ON p.productID = od.productID
GROUP BY p.productID, p.productName, p.productType
HAVING COUNT(od.orderID) < (SELECT AVG(cnt) FROM (SELECT COUNT(orderID) AS cnt FROM CustomerOrderDetails GROUP BY productID) AS avg_table)
ORDER BY order_count ASC;

Query Response:  <img width="571" height="304" alt="Q8" src="https://github.com/user-attachments/assets/234f0ec1-aa3f-418f-8a59-922fc7967857" />


Natural Language Description: This query uses a LEFT JOIN and HAVING clause with a subquery to find products whose order count falls below the average order count across all products.
Managerial Relevance: Managers can identify underperforming products relative to the rest of the catalog. This helps in deciding whether to promote, discount, bundle, or discontinue low-demand items.

  9. Query 9 - Complex Question: Which customers have spent more than the average order amount in total? Why it matters: A manager can use this to identify above-average customers for loyalty offers or targeted marketing.

SELECT c.customerID, c.firstName, c.lastName, SUM(o.amount) AS total_customer_spent FROM Customers c JOIN Orders o ON c.customerID = o.customerID GROUP BY c.customerID, c.firstName, c.lastName HAVING SUM(o.amount) > ( SELECT AVG(amount) FROM Orders ) ORDER BY total_customer_spent DESC;

Query Response: <img width="536" height="279" alt="Q9" src="https://github.com/user-attachments/assets/ab2af1ba-c118-4e59-8a06-9dce792da22f" />


Natural Language Description: This query calculates total spending per customer and uses a subquery with AVG to filter customers whose total exceeds the average order amount. It also uses HAVING.

Managerial Relevance: Managers can identify above-average customers for targeted marketing campaigns, loyalty rewards, and upselling opportunities.

  10. Query 10 - Complex Question: How many products does each supplier provide to each store location? Why it matters: A manager can use this to evaluate supplier coverage by location and spot sourcing concentration or gaps.

SELECT s.supName, sl.city, sl.state, COUNT(so.productID) AS products_supplied FROM Suppliers s JOIN Supplier Orders so ON s.SupplierID = so.SupplierID JOIN Store Location sl ON so.LocationID = sl.LocationID GROUP BY s.supName, sl.city, sl.state ORDER BY s.supName, sl.state, sl.city;

Query Response: <img width="520" height="377" alt="Q10" src="https://github.com/user-attachments/assets/cb8e46d3-d774-4593-ab4f-ea3e8901c9be" />


Natural Language Description:This query joins Suppliers, Supplier Orders, and Store Location tables and counts how many products each supplier provides to each location.

Managerial Relevance:Managers can evaluate supplier coverage across locations, identify over-reliance on certain suppliers, and detect gaps in supply chain distribution.

## Database Information
Database Name: Group_21479_G5
