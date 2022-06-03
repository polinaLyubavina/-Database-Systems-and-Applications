# Lab 1

## Part 1: English to Schema

### Grocery Store Inventory 

- `GroceryStoreInventory [ __SKU(int)__, productName(string), quantity(int), price(float) ]`

### Grocery Store Aisly Inventory

- `GroceryAisleInventory [ __SKU(int)__, productName(string), price(float)]`

- `Location [__SKU(int)__, aisle(int), aisleDisplayCase(int)]`

Combine inventory and location by SKU to get all locations for a product.

### Car Dealership

- `Cars [ __VIN(int)__, make(string), model(string), color(string), year(int) ]` 

- `Salespeople [ __SSN(int)__, assignedCars(string) ]`

- `DealershipIntenvory [ __VIN(int)__ , __SSN(int)__]`

Combine all tables using VIN and SSN to get all salespeople/car combos.

## Part 2: SQL Table Declarations

### SQL-like Table Descriptions of a Library Database

```
CREATE TABLE Patrons (
    Name(string),
    CardNum(int),
    PRIMARY KEY(CardNum)
)

CREATE TABLE Inventory (
    UNIQUE Serial(int),
    ISBN(int),
    PRIMARY KEY(ISBN)
)

CREATE TABLE CheckedOut (
    CardNum(int),
    Serial(int)
    PRIMARY KEY(Serial)
)

CREATE TABLE Phones (
    CardNum(int),
    Phone(string)
    PRIMARY KEY(CardNum, Phone)
)

CREATE TABLE Titles (
    ISBN(int),
    Title(string),
    Author(string),
    PRIMARY KEY(ISBN)
)
```

## Part 3: Fill in Tables

### Cars:

- `Cars [ __VIN(int)__, make(string), model(string), color(string), year(int) ]`

|    VIN   |  Make  |  Model | Color | Year |
| -------- | ------ | ------ | ----- | ---- |
| 12847912 | Toyota | Tacoma | Red   | 2008 |
| 38571242 | Toyota | Tacoma | Green | 1999 |
| 02582305 | Tesla  | 3      | White | 2018 |
| 81283957 | Subaru | WRX    | Blue  | 2016 |
| 10957463 | Ford   | F150   | Red   | 2004 |

### Salespeople:

- `Salespeople [ __SSN(int)__, assignedCars(string) ]`

|   SSN   |  Assigned Cars  |
| ------- | --------------- |
| 8679980 | all Toyota cars |
| 3452123 | all red cars    |
| 3245671 | Tesla           |

### Dealership Inventory:

- `DealershipIntenvory [ __VIN(int)__ , __SSN(int)__]`

|    VIN   |   SSN   |
| -------- | ------- |
| 12847912 | 8679980, 3452123 |
| 38571242 | 8679980 |
| 02582305 | 3245671 |
| 81283957 |         |
| 10957463 | 3452123 |


## Part 4: Keys and Superkeys

| Attribute Sets | Superkey? |   Proper Subsets | Key?  |
| -------------- | --------- | ---------------- | ----- |
| {A1}           | No        | {}               | No    |
| {A2}           | No        | {}               | No    |
| {A3}           | No        | {}               | No    |
| {A1, A2}       | Yes       | {A1}, {A2}       | Yes   |
| {A1, A3}       | No        | {A1}, {A3}       | No    |
| {A2, A3}       | No        | {A2}, {A3}       | No    |
| {A1, A2, A3}   | Yes       | {A1}, {A2}, {A3}, {A1, A2}, {A1, A3} {A2, A3} | No    |


## Part 5: Abstract Reasoning

- True. A superkey might include extra columns that aren't required to uniquely identify each tuple. 
- False. A key uniquely identifies a tuple, and while multiple columns *can* make up a key, a key should be made from a minimal set of columns.
- True. A superkey and a key can share columns. 
- False. While a superkey can be made up of a maximum number of columns where at least one column is unique, a single column in a superkey *doesn't* have to be unique for the superkey to work. A combination of two or more columns together can also be unique and satisfy the superkey criteria. 
- True. A key must be made of the minimal number of columns that make it unique. If the key has to be made up of the entire schema, then so be it.
