### Part 2

```
CREATE TABLE Cars (
    VIN int unsigned,
    make varchar(255), 
    model varchar(255),
    color varchar(255), 
    year int unsigned,
    PRIMARY KEY (VIN)
);

CREATE TABLE Salespeople (
    SSN int unsigned,
    assignedCars varchar(255),
    PRIMARY KEY (SSN)
);

CREATE TABLE DealershipIntenvory (
    SSN int unsigned,
    VIN int unsigned,
    FOREIGN KEY (VIN) REFERENCES Cars(VIN),
    FOREIGN KEY (SSN) REFERENCES Salespeople(SSN),
    PRIMARY KEY (SSN, VIN)
);

INSERT INTO Cars (VIN, make, model, color, year)
VALUES
    (12847912, 'Toyota', 'Tacoma', 'Red', 2008),
    (38571242, 'Toyota', 'Tacoma', 'Green', 1999),
    (02582305, 'Tesla', '3', 'White',	2018),
    (81283957, 'Subaru', 'WRX', 'Blue', 2016),
    (10957463, 'Ford ',	'F150', 'Red', 2004)
;

INSERT INTO Salespeople (SSN, assignedCars)
VALUES
    (8679980, 'all Toyota cars'),
    (3452123, 'all red cars'),
    (3245671, 'Tesla')
;

INSERT INTO DealershipIntenvory (VIN, SSN)
VALUES
    (12847912, 8679980),
    (12847912, 3452123),
    (38571242, 8679980),
    (02582305, 3245671),
    (10957463, 3452123)
;
```

### Part 3

```
SELECT Title FROM Titles WHERE Author = '<Author>';

SELECT ISBN FROM Titles WHERE Author = '<Author>';

SELECT *
FROM CheckedOut
INNER JOIN Patrons ON CheckedOut.CardNum = Patrons.CardNum
INNER JOIN Inventory ON CheckedOut.Serial = Inventory.Serial
INNER JOIN Titles ON Inventory.ISBN = Titles.ISBN
WHERE Name = '<Patron's name>';

SELECT Phones.Phone
FROM Patrons
INNER JOIN Phones ON Phones.CardNum = Patrons.CardNum
INNER JOIN CheckedOut ON CheckedOut.CardNum = Patrons.CardNum
INNER JOIN Inventory ON CheckedOut.Serial = Inventory.Serial
INNER JOIN Titles ON Inventory.ISBN = Titles.ISBN
WHERE Title = '<Title>';
```

### Part 4

```
SELECT Titles.Title
FROM Titles 
INNER JOIN Inventory ON Titles.ISBN = Inventory.ISBN
ORDER BY Inventory.Serial ASC
LIMIT <N>;

SELECT Patrons.Name
FROM Patrons
INNER JOIN CheckedOut ON Patrons.CardNum = CheckedOut.CardNum
ORDER BY CheckedOut.Serial DESC
LIMIT 1;

SELECT Patrons.Name
FROM Patrons
WHERE Patrons.CardNum NOT IN (SELECT CheckedOut.CardNum 
FROM CheckedOut);

SELECT DISTINCT Titles.Title, Titles.ISBN
FROM Titles
INNER JOIN Inventory ON Titles.ISBN = Inventory.ISBN;
```

### Part 5

```
SELECT Players.Name
FROM Players
WHERE Elo >= 2850;

SELECT Players.Name
FROM Players
INNER JOIN Games ON Players.pID = Games.WhitePlayer;

SELECT Players.Name
FROM Players
INNER JOIN Games ON Players.pID = Games.WhitePlayer
WHERE Result = 'W';

SELECT DISTINCT Players.Name
FROM Players
WHERE pID IN (
    SELECT WhitePlayer
    FROM Games
    INNER JOIN Events ON Games.eID = Events.eID
    WHERE Year(Events.Date) = 2018
)
OR pID IN (
    SELECT BlackPlayer
    FROM Games
    INNER JOIN Events ON Games.eID = Events.eID
    WHERE Year(Events.Date) = 2018
);

SELECT *
FROM 
(
    SELECT Events.Name, Events.Date
    FROM Players
    INNER JOIN Games ON Games.WhitePlayer = Players.pID
    INNER JOIN Events ON Events.eID = Games.eID
    WHERE Players.Name = 'Carlsen, Magnus' AND Result = 'B'
) AS A
UNION
(
    SELECT Events.Name, Events.Date
    FROM Players
    INNER JOIN Games ON Games.BlackPlayer = Players.pID
    INNER JOIN Events ON Events.eID = Games.eID
    WHERE Players.Name = 'Carlsen, Magnus' AND Result = 'W'
);

SELECT DISTINCT *
FROM 
(
    SELECT black.Name
    FROM Games
    INNER JOIN Players AS white ON Games.WhitePlayer = white.pID
    INNER JOIN Players AS black ON Games.BlackPlayer = black.pID
    WHERE white.Name = 'Carlsen, Magnus'
) AS A
UNION
(
    SELECT white.Name
    FROM Games
    INNER JOIN Players AS white ON Games.WhitePlayer = white.pID
    INNER JOIN Players AS black ON Games.BlackPlayer = black.pID
    WHERE black.Name = 'Carlsen, Magnus'    
);

```

### Part 6
