# MIST4610
# Team Name:
21479 Group 5
# Team Members:
1. Derek Quinlan [@derekq111](https://github.com/derekq111)
2. Regan Taylor [@nrt19057](https://github.com/nrt19057)
3. Sydney James [@srj44873](https://github.com/srj44873)
4. Mary Earhart [@mke48687](https://github.com/marykearhart)
# Problem Description:
  Our group handled the task of creating a data model for our franchise "Loaded Tea" company. Our business is operated in various locations around the U.S., each with their own employees lead by department chairs in specialized Human Resources. Additionally, our model accounts for the information stored on the customers at each location, their eligibility for military and student discounts, and the supplier-to-business coordination of supply orders aside from those purchases made by the customers either online or in person. Our overarching goals of this project were to accurately display each relationship between entities, create sample data tables for each entity and its attributes, and test out various queries relevant to the business operations of our organization.
# Data Model:
  We started off our data model by creating a customer entity, indicating all of the relevant data stored on our customers ranging from attributes of name, address, and contact information. For each customer, there are many sales, which we indicated through a one to many relationship with our sales entity. 
  
  The Sales entity displays data on the date, price and the payment method chosen by the customer for each sale. Additionally, the Sales entity contains two foreign keys- CustomerID and ProgramID- to represent the customers making each sale and whether they qualified for any discount programs. This then brings us to the Discount Programs table, which contains the program name and the percentage discount offered for each. In this scenario, our company only offers Military and Student discounts, with military granting a 30% decrease in prices and Student granting a 20% decrease. For the sake of the complexity of our data model, we assume that all customers' sales will apply for one of these discounts. This Discount Program table also connects to the customers table as each customer can qualify for many discount programs in a one-to-many relationship.
  
  Similar to the relationship between sales and customers, Customer Orders and Customers also experience a one-to-many relationship as each customer can have many orders, but each order can only belong to one customer. This entity is differentiated from the sales table as those purchases were made online rather than at a specific franchise location. As an individual entity, Customer Orders stores the monetary amount of each order and the date the order was placed. 

  Considering that many orders can contain many products, we developed the associative identity labeled Customer Order Details to indicate this relationship between Customer Orders and Products. In this entity, we have the product ID and order ID for each, as well as the shipping date, status of the order, price, and quantity of items in the order. For this project, we assume that the customer orders all have a scheduled date of which they will be shipped out, even if they are still being processed and have not yet shipped. We also assume that orders which are cancelled will not appear in the table any longer, and that customers are limited to the purchase of 20 items when choosing to buy online instead of in person.
  
  Next is our product entity which keeps track of the different flavors and types of drinks offered by our company, specifically either Loaded Teas or Beauty Shakes in various fruity flavors. This table indicates a many-to-many relationship with the sales table as many sales can contain many different products, and vice versa. This relationship is held together by an associative identity labeled product line which is non-identifiable and serves as a holding place for each entity's foreign keys.

  Many products in the product entity can also go to many store locations, hence the many-to-many connection between Store Location and Products. Since our Loaded Tea company functions as a franchise with many different locations across the United States, the Store Locations entity is comprised of attributes including each store's area code, city, and state to differentiate between each shop. This entity is also connected with the Employees table signifying that many employees can work at one store location, while each employee can only work at one location. 
  
  Together these two tables form the associative identity labeled "Supplier Orders", which contains the foreign keys of each individual entity with no other salient attributes. This entity specifically refers to the franchises purchasing more inventory to sell to customers. For completeness, we specify Supplier Orders as to differentiate from Customer orders that come directly from the stock at the store locations. Since the supplies in these orders must come from a home base, we also created a Supplier entity containing individual supplier IDs for each company, as well as their company name.

  Last, the Employees entity is the most complex of our entities, containing information on each employee's name, email, department name, and foreign keys identifying their respective store location and department chair. The department chair identifier is represented by a one-to-many recursive relationship, as one department chair can observe many employees. We will assume in this case that each employee contains a departmentChair ID which refers to the specific department chair that oversees their work at their respective location.

<img width="952" height="441" alt="Screenshot 2026-03-30 at 11 27 29 AM" src="https://github.com/user-attachments/assets/678fd0a4-afc8-430f-9e32-6d5b40012a24" />

# Data Dictionary:
<img width="678" height="502" alt="Screenshot 2026-03-31 at 9 22 49 AM" src="https://github.com/user-attachments/assets/b8d092b2-2dc4-46a6-8d24-54f2be88862c" />
<img width="678" height="408" alt="Screenshot 2026-03-31 at 9 22 23 AM" src="https://github.com/user-attachments/assets/a13ce5d0-cebe-4cc3-a1de-721e72c78cb1" />
<img width="678" height="455" alt="Screenshot 2026-03-31 at 9 23 20 AM" src="https://github.com/user-attachments/assets/fa5b8401-d572-4179-8d01-1e9686f5939d" />
<img width="678" height="417" alt="Screenshot 2026-03-31 at 9 23 53 AM" src="https://github.com/user-attachments/assets/c3809abb-e126-45ff-b130-d003afebfbb6" />
<img width="678" height="698" alt="Screenshot 2026-03-31 at 9 24 29 AM" src="https://github.com/user-attachments/assets/89f85b29-29c1-4d58-b6c4-e61f0bd2cc6d" />
<img width="678" height="582" alt="Screenshot 2026-03-31 at 9 25 34 AM" src="https://github.com/user-attachments/assets/49e4a3e1-679f-48cf-950e-80fd1561d1cb" />
<img width="678" height="548" alt="Screenshot 2026-03-31 at 9 26 29 AM" src="https://github.com/user-attachments/assets/fe556930-744d-4c0f-8e1f-85d7a35c0858" />
<img width="678" height="699" alt="Screenshot 2026-03-31 at 9 27 10 AM" src="https://github.com/user-attachments/assets/929d0c26-8eb3-466c-b9bb-0e5935eecceb" />
<img width="678" height="252" alt="Screenshot 2026-03-31 at 9 27 43 AM" src="https://github.com/user-attachments/assets/923cf6e0-c984-48c9-9f04-f312a3143bb2" />

# Queries:
<img width="717" height="336" alt="Screenshot 2026-03-29 at 5 16 21 PM" src="https://github.com/user-attachments/assets/980bfdf3-5a8b-468f-bc49-639a2e572fc1" />


  1. Query 1 - Simple Question: What customers are currently in the database? Why it matters: A manager may want a full customer list for outreach, customer service, or record review.

SELECT customerID, firstName, lastName, emailAddress, phoneNumber FROM Customers ORDER BY lastName, firstName;

Query Response:<img width="539" height="362" alt="Q1" src="https://github.com/user-attachments/assets/c2ee7f04-aa37-4391-99eb-7483eadc4860" />

Natural Language Description: This query retrieves all customers in the database, displaying their ID, first name, last name, email address, and phone number. The results are sorted alphabetically by last name and first name.

Managerial Relevance: Managers use this query to maintain an up-to-date customer directory. It supports customer outreach, verifies stored contact information, and helps ensure accurate records for communication and service.

  2. Query 2 - Simple Question: What products does the business carry? Why it matters: A manager may want a current list of products for catalog review, sales planning, or inventory coordination.

SELECT productID, productName, productType FROM Products ORDER BY productType, productName;

Query Response: <img width="404" height="326" alt="Screenshot 2026-03-30 203739" src="https://github.com/user-attachments/assets/2ab0b99f-55be-48aa-831e-21b82668f7ec" />

Natural Language Description: This query lists<img width="678" height="408" alt="Screenshot 2026-03-31 at 9 21 56 AM" src="https://github.com/user-attachments/assets/b420b970-99b2-44c4-a61b-cb6129fcbdef" />
 all products, including product ID, name, and type. The results are organized by product type and then alphabetically by product name.

Managerial Relevance: Managers can review the full product catalog to support sales planning, marketing strategies, and inventory management. It ensures the business has a clear understanding of its offerings.

  3. Query 3 - Simple Question: What suppliers are in the system? Why it matters: A manager may need a supplier directory when reviewing vendor relationships or sourcing issues.

SELECT SupplierID, supName FROM Suppliers ORDER BY supName;

Query Response: <img width="367" height="269" alt="Q3" src="https://github.com/user-attachments/assets/cee84f2b-31e0-4cac-bbee-d89d3cb2bd73" />

Natural Language Description: This query retrieves all suppliers along with their IDs and names, sorted alphabetically.

Managerial Relevance: Managers use this to evaluate vendor relationships, identify sourcing options, and confirm supplier records when making purchasing or supply chain decisions.

  4. Query 4 - Simple Question: What store locations are recorded in the database? Why it matters: A manager may want to review all operating locations for staffing or supplier coordination.

SELECT LocationID, city, state, areaCode FROM Store Location ORDER BY state, city;

Query Response: <img width="395" height="161" alt="Q4" src="https://github.com/user-attachments/assets/42f280db-44da-4867-bd04-1f343655fbf6" />

Natural Language Description: This query returns all store locations, including location ID, city, state, and area code. Results are sorted geographically.

Managerial Relevance: Managers can use this to analyze regional operations, allocate resources, coordinate staffing, and ensure all store locations are properly tracked.

5. Query 5 - Complex Question: Which customers have generated the most total order revenue? Why it matters: A manager can use this to identify the highest-value customers and focus retention efforts on them.

SELECT c.customerID, c.firstName, c.lastName, SUM(o.amount) AS total_spent FROM Customers c JOIN Orders o ON c.customerID = o.customerID GROUP BY c.customerID, c.firstName, c.lastName ORDER BY total_spent DESC;

Query Response: <img width="464" height="281" alt="Q5" src="https://github.com/user-attachments/assets/8e14a444-fbf2-4893-bdae-c7d33c5ff13c" />

Natural Language Description: This query joins Customers and Orders to calculate total spending per customer using SUM. Results are grouped by customer and sorted from highest to lowest spending.

Managerial Relevance: Managers can identify high-value customers and prioritize retention strategies, loyalty programs, and personalized marketing to maximize long-term revenue.

  6. Query 6 - Complex Question: Which products have sold the highest total quantity? Why it matters: A manager can use this to identify top-selling products and make pricing, stocking, and promotion decisions.

SELECT p.productID, p.productName, p.productType, SUM(od.orderqty) AS total_quantity_sold FROM Products p JOIN Order Details od ON p.productID = od.productID GROUP BY p.productID, p.productName, p.productType ORDER BY total_quantity_sold DESC;

Query Response:  <img width="539" height="312" alt="Q6" src="https://github.com/user-attachments/assets/a8f9db3e-e745-463a-95b4-d654365cd77a" />

Natural Language Description: This query joins Products and Order Details and calculates the total quantity sold for each product using SUM. Results are grouped and ranked by quantity sold.

Managerial Relevance: Managers use this to identify high-demand products, optimize inventory levels, and ensure popular products remain in stock.

  7. Query 7 - Complex Question: Which products have generated the most order revenue? Why it matters: A manager can use this to distinguish products that drive revenue, not just volume.

SELECT p.productID, p.productName, SUM(od.orderPrice * od.orderqty) AS total_product_revenue FROM Products p JOIN Order Details od ON p.productID = od.productID GROUP BY p.productID, p.productName ORDER BY total_product_revenue DESC;

Query Response: <img width="600" height="315" alt="Q7" src="https://github.com/user-attachments/assets/56b07101-7173-41a0-8db2-048ed7b6c502" />

Natural Language Description: This query calculates total revenue per product by multiplying price and quantity, then summing across all orders. Results are grouped and sorted by revenue.

Managerial Relevance: Managers can distinguish between products that sell frequently and those that generate the most profit, helping guide pricing, promotions, and product prioritization.

  8. Query 8 - Complex Question: Which products have never been included in any order? Why it matters: A manager can use this to identify underperforming or unused products that may need promotion or discontinuation.

SELECT p.productID, p.productName, p.productType FROM Products p WHERE NOT EXISTS ( SELECT 1 FROM Order Details od WHERE od.productID = p.productID ) ORDER BY p.productName;

Query Response:  <img width="571" height="304" alt="Q8" src="https://github.com/user-attachments/assets/234f0ec1-aa3f-418f-8a59-922fc7967857" />

Natural Language Description: This query uses a NOT EXISTS subquery to identify products that do not appear in any order records.

Managerial Relevance: Managers can identify underperforming or inactive products. This helps in deciding whether to promote, discount, or discontinue these items.

  9. Query 9 - Complex Question: Which customers have spent more than the average order amount in total? Why it matters: A manager can use this to identify above-average customers for loyalty offers or targeted marketing.

SELECT c.customerID, c.firstName, c.lastName, SUM(o.amount) AS total_customer_spent FROM Customers c JOIN Orders o ON c.customerID = o.customerID GROUP BY c.customerID, c.firstName, c.lastName HAVING SUM(o.amount) > ( SELECT AVG(amount) FROM Orders ) ORDER BY total_customer_spent DESC;

Query Response  <img width="536" height="279" alt="Q9" src="https://github.com/user-attachments/assets/ab2af1ba-c118-4e59-8a06-9dce792da22f" />

Natural Language Description: This query calculates total spending per customer and uses a subquery with AVG to filter customers whose total exceeds the average order amount. It also uses HAVING.

Managerial Relevance: Managers can identify above-average customers for targeted marketing campaigns, loyalty rewards, and upselling opportunities.

  10. Query 10 - Complex Question: How many products does each supplier provide to each store location? Why it matters: A manager can use this to evaluate supplier coverage by location and spot sourcing concentration or gaps.

SELECT s.supName, sl.city, sl.state, COUNT(so.productID) AS products_supplied FROM Suppliers s JOIN Supplier Orders so ON s.SupplierID = so.SupplierID JOIN Store Location sl ON so.LocationID = sl.LocationID GROUP BY s.supName, sl.city, sl.state ORDER BY s.supName, sl.state, sl.city;

Query Response: <img width="520" height="377" alt="Q10" src="https://github.com/user-attachments/assets/cb8e46d3-d774-4593-ab4f-ea3e8901c9be" />

Natural Language Description: This query joins Suppliers, Supplier Orders, and Store Location tables and counts how many products each supplier provides to each location.

Managerial Relevance: Managers can evaluate supplier coverage across locations, identify over-reliance on certain suppliers, and detect gaps in supply chain distribution.

# Database Information:
Database Name: Group_21479_G5
