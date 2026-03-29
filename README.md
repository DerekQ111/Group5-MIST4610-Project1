# Group5-MIST4610-Project1
# Team Name
Group 5

## Team Members
- Derek Quinlan – [GitHub Repo](https://github.com/DerekQ111)
- Mary Earhat – [GitHub Repo](https://github.com/marykearhart)
- Natalie Taylor – [GitHub Repo](https://github.com/nrt19057/MIS-Project-1)
- Sydney James [GitHub Repo](https://github.com/srj44873)


## 10 Queries
Query 1 - Simple
Question: What customers are currently in the database?
Why it matters: A manager may want a full customer list for outreach, customer service, or record review.

SELECT customerID, firstName, lastName, emailAddress, phoneNumber
FROM Customers
ORDER BY lastName, firstName;

Query 2 - Simple
Question: What products does the business carry?
Why it matters: A manager may want a current list of products for catalog review, sales planning, or inventory coordination.

SELECT productID, productName, productType
FROM Products
ORDER BY productType, productName;

Query 3 - Simple
Question: What suppliers are in the system?
Why it matters: A manager may need a supplier directory when reviewing vendor relationships or sourcing issues.

SELECT SupplierID, supName
FROM Suppliers
ORDER BY supName;

Query 4 - Simple
Question: What store locations are recorded in the database?
Why it matters: A manager may want to review all operating locations for staffing or supplier coordination.

SELECT LocationID, city, state, areaCode
FROM `Store Location`
ORDER BY state, city;

Query 5 - Complex
Question: Which customers have generated the most total order revenue?
Why it matters: A manager can use this to identify the highest-value customers and focus retention efforts on them.

SELECT 
    c.customerID,
    c.firstName,
    c.lastName,
    SUM(o.amount) AS total_spent
FROM Customers c
JOIN Orders o
    ON c.customerID = o.customerID
GROUP BY c.customerID, c.firstName, c.lastName
ORDER BY total_spent DESC;

Query 6 - Complex
Question: Which products have sold the highest total quantity?
Why it matters: A manager can use this to identify top-selling products and make pricing, stocking, and promotion decisions.

SELECT 
    p.productID,
    p.productName,
    p.productType,
    SUM(od.orderqty) AS total_quantity_sold
FROM Products p
JOIN `Order Details` od
    ON p.productID = od.productID
GROUP BY p.productID, p.productName, p.productType
ORDER BY total_quantity_sold DESC;

Query 7 - Complex
Question: Which products have generated the most order revenue?
Why it matters: A manager can use this to distinguish products that drive revenue, not just volume.

SELECT 
    p.productID,
    p.productName,
    SUM(od.orderPrice * od.orderqty) AS total_product_revenue
FROM Products p
JOIN `Order Details` od
    ON p.productID = od.productID
GROUP BY p.productID, p.productName
ORDER BY total_product_revenue DESC;

Query 8 - Complex
Question: Which products have never been included in any order?
Why it matters: A manager can use this to identify underperforming or unused products that may need promotion or discontinuation.

SELECT 
    p.productID,
    p.productName,
    p.productType
FROM Products p
WHERE NOT EXISTS (
    SELECT 1
    FROM `Order Details` od
    WHERE od.productID = p.productID
)
ORDER BY p.productName;

Query 9 - Complex
Question: Which customers have spent more than the average order amount in total?
Why it matters: A manager can use this to identify above-average customers for loyalty offers or targeted marketing.

SELECT 
    c.customerID,
    c.firstName,
    c.lastName,
    SUM(o.amount) AS total_customer_spent
FROM Customers c
JOIN Orders o
    ON c.customerID = o.customerID
GROUP BY c.customerID, c.firstName, c.lastName
HAVING SUM(o.amount) > (
    SELECT AVG(amount)
    FROM Orders
)
ORDER BY total_customer_spent DESC;

Query 10 - Complex
Question: How many products does each supplier provide to each store location?
Why it matters: A manager can use this to evaluate supplier coverage by location and spot sourcing concentration or gaps.

SELECT 
    s.supName,
    sl.city,
    sl.state,
    COUNT(so.productID) AS products_supplied
FROM Suppliers s
JOIN `Supplier Orders` so
    ON s.SupplierID = so.SupplierID
JOIN `Store Location` sl
    ON so.LocationID = sl.LocationID
GROUP BY s.supName, sl.city, sl.state
ORDER BY s.supName, sl.state, sl.city;

