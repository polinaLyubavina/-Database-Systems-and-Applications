# Lab 3: Relational Algebra

## Part 1 - Join

#### 1
`T1[A(int), Q(varchar), R(int), B(varchar), C(int)]`

|A|Q|R|B|C|
|---|---|---|---|---|
|20|a|5|b|6|
|20|a|5|b|5|

#### 2
`T1[A(int), Q(varchar), R(int), B(varchar), C(int)]`

|A|Q|R|B|C|
|---|---|---|---|---|
|25|b|8|b|6|

#### 3
`T1[A(int), Q(char), R(char), B(char), C(int)]`

|A|Q|R|B|C|
|---|---|---|---|---|
|20|a|5|b|6|
|25|b|8|c|3|
|35|a|6|b|5|
|20|a|5|b|6|
|45|b|8|c|3|
|20|a|5|b|5|

#### 4
`T1[A(int), Q(varchar), R(int), B(varchar), C(int)]`

|A|Q|R|B|C|
|---|---|---|---|---|
|20|a|5|b|5|

## Part 2 - Chess Queries

#### 1
$$ \sigma\ (_Players(Elo) >= 280) $$

#### 2
$$\rho\ (_WhitePlayers(pId) \Pi\ wpID (Games)) $$

#### 3
$$ \sigma_\ (_Players(Name) \Pi\ wpID \wedge _Result(1-0) ) $$

#### 4
$$ \sigma\ (_Players(Name) \Pi\ _Year(2018)) $$

#### 5
$$\sigma((\sigma_{Result > 1-0}(Games)/\sigma_{Name}\wedge_{Dates}(Events)\sigma_{pID}(Players)))$$

#### 6
$$  $$

## Part 3 - LMS Queries

### Part 3.1:

#### a)
$$ \rho(C, \pi_{sID}(\sigma_{Grd=C}(Enrolled))) $$ 
$$ \pi_{Name}((\pi_{sID}(Enrolled) - C)\bowtie Students) $$

|Name|
|---|

|sID|Name|DOB|cID|Grd|
|---|---|---|---|---|
|1|Hermione|1980|3500|A|
|1|Hermione|1980|3810|A-|
|1|Hermione|1980|5530|A|
|2|Harry|1979|3810|A|
|2|Harry|1979|5530|B|
|3|Ron|1979|3810|B|

#### b)
The query is searching for students who got above a C grade.

In `Enrolled` table/realtion you select everyone with a Grade of C, then rename their `sID` to `C`. 
Then, you take the `Enrolled` table/realtion and remove everyone with the `sID` of `C` from the table/realtion. You then join this table/relation with the `Students` table/relation, and store the result in the `Name` table/realtion.


### Part 3.2:

#### a)
`S1[sID(int), Name(varchar), DOB(int)]`

|S1|
|---|

|sID|Name|DOB|
|---|---|---|


#### b)
THe query is just renaming the `Student` table/realtion to be the `S1` table/realtion (the name of the table/realtion changes from Student to S1)

### Part 3.3:

#### a)
|Name|
|---|

|cID|sID|Name|
|---|---|---|
|1|3500|SW Practice|
|1|3810|Architecture|
|1|5530|Databases|

#### b)
You match the cID with sID to match against hte Course Name.

You select the `sID` column from the `Students` table/realtion, and select the `sID` and `cID` columns from the `Enrolled` table/realtion, then divide and natural join them against `Courses` table/realtion. The result of this query is stored into the `Name` table/realtion.

### Part 4
$$\sigma((\sigma_{cid > 3000}(Enrolled)/\pi_{Name}(Students)))$$


