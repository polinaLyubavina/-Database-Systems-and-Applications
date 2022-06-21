## Lab 5

#### 1
```
SELECT Patrons.Name, count(*)
From Patrons
INNER JOIN CheckedOut ON Patrons.CardNum = CheckedOut.CardNum
GROUP BY Patrons.Name
ORDER BY count(*) DESC
LIMIT 1
;
```

#### 2
```
SELECT Titles.Author
FROM Titles
GROUP BY Titles.Author
HAVING count(*) > 1
;
```

#### 3
```
SELECT Titles.Author
FROM Inventory
INNER JOIN Titles ON Inventory.ISBN = Titles.ISBN
GROUP BY Titles.Author
HAVING count(*) > 1
;
```

#### 4
```
SELECT
    Patrons.Name, 
    count(CheckedOut.Serial),
    CASE 
        WHEN count(CheckedOut.Serial) > 2 THEN 'Platinum' 
        WHEN count(CheckedOut.Serial) = 2 THEN 'Gold'
        WHEN count(CheckedOut.Serial) = 1 THEN 'Silver'
        WHEN count(CheckedOut.Serial) = 0 THEN 'Bronze'
        END AS Loyalty
FROM Patrons
LEFT JOIN CheckedOut ON Patrons.CardNum = CheckedOut.CardNum
GROUP BY Patrons.Name
;
```
