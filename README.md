# Database-Teradata-Exercise-Duke

## Exercise 6
## What is the maximum price paid for an item in our database? 
## What is the minimum price paid for an item in our database?

SELECT MAX(SPRICE)
FROM TRNSACT;
# 6017.00

SELECT MIN(SPRICE)
FROM TRNSACT;
# 0.00

## Exercise 7
## How many departments have more than 100 brands associated with them, and what are their descriptions? 

SELECT s.dept, d.deptdesc, COUNT(s.brand)
FROM SKUINFO s, DEPTINFO d
WHERE s.dept=d.dept
GROUP BY s.dept, d.deptdesc
HAVING COUNT(s.brand) > 100
ORDER BY s.dept ASC;
# 60

## Exercise 8
## Write a query that retrieves the department descriptions of each of the skus in the skstinfo table. 

SELECT SKSTINFO.sku, DEPTINFO.deptdesc
FROM (SKSTINFO JOIN SKUINFO
ON SKSTINFO.sku=SKUINFO.sku) 
JOIN DEPTINFO
ON SKUINFO.dept=DEPTINFO.dept
GROUP BY SKSTINFO.sku, DEPTINFO.deptdesc
ORDER BY SKSTINFO.sku ASC;

## Exercise 9
## What department (with department description), brand, style, and color had the greatest total value of returned items? 

