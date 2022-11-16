### sql notes

### Content classification: mssql vs. mysql, adventureworks, northwind, 

 [awesome chocolates](awechoco.md) | [sakila](sakila.md) | [employees](employees.md) |

SO let us try some sql notes.

create table 

create table Houses(
id,district,address,bedrooms,rent)

insert into Houses(
id,district,address,bedrooms,rent)

values(
1,South,Rose Street, 5,4,3000.00
2,North,Main Street, 12,3,2250.00
3,South,Rose Street, 5,4,3000.00
4,West,Nice Street, 3,2,1750.00
5,West,Park Avenue, 10,4,3500.00
6,South,Little Street, 7,4,3000.00
7,North,Main Street, 8,3,2100.00


create table Renters(
id,name,preferred_district,min_bedrooms,min_rent,max_rent)

insert into Renters(
id,name,preferred_district,min_bedrooms,min_rent,max_rent)

values(
1,Helen Boss,South,3,2500.00,3200.00
2,Michael Lane,West,2,1500.00,2500.00
3,Susan Sanders,West,4,2500.00,4000.00
4,Tom White,North,3,2200.00,2500.00
5,Sofia Brown,North,3,1800.00,2300.00

create table Deals(
id,date,renter_id,house_id,agent_fee)

insert into Deals(id,date,renter_id,house_id,agent_fee)

values(
1,2020-01-30,1,1,600.00
2,2020-02-03,2,4,350.00
3,2020-03-12,3,5,700.00
4,2020-04-10,4,2,450.00
)


```
select a.id, a.name 
from employees as a 
group by a.id 
having a.id > 100;
```

==========================

CREATE TABLE `sales` (
  'customer_id' VARCHAR(1),
  'order_date' DATE,
  'product_id' INTEGER
);

Learnings: Only use backtick or no tick for field names. double or single quotes will not do.
======================


https://web.archive.org/web/20160130220207/https://dev.mysql.com/doc/refman/5.5/en/use.html


If you want to get back to the condition of having no default database then do something like the following:

mysql> CREATE DATABASE SomeWeirdName;
mysql> USE SomeWeirdName;
mysql> DROP SomeWeirdName;

=================

> My transactions table is missing the txn_date column, I am using the schema provided

For MySQL, you can execute the following statements to get the job done.

1. Create a new column `txn_date` of type DATE.
```sql
ALTER TABLE transactions
ADD COLUMN txn_date DATE AFTER ticker;
```
2. Copy over the date part of `txn_time` to `txn_date`
```sql
UPDATE transactions txn_date
SET txn_date = date(txn_time);
```

3. Check if the transaction is done.

```sql
mysql> describe transactions;                                 
+----------------+------------+------+-----+---------+-------+
| Field          | Type       | Null | Key | Default | Extra |
+----------------+------------+------+-----+---------+-------+
| txn_id         | int        | YES  |     | NULL    |       |
| member_id      | varchar(6) | YES  |     | NULL    |       |
| ticker         | varchar(3) | YES  |     | NULL    |       |
| txn_date       | date       | YES  |     | NULL    |       |
| txn_time       | timestamp  | YES  |     | NULL    |       |
| txn_type       | varchar(4) | YES  |     | NULL    |       |
| quantity       | float      | YES  |     | NULL    |       |
| percentage_fee | float      | YES  |     | NULL    |       |
+----------------+------------+------+-----+---------+-------+
8 rows in set (0.00 sec)                                      
                                                              
mysql> select txn_id from transactions where txn_date is null;
Empty set (0.03 sec)                                          

mysql> select txn_id,txn_date,txn_time from transactions limit 20;
+--------+------------+---------------------+                     
| txn_id | txn_date   | txn_time            |                     
+--------+------------+---------------------+                     
|      1 | 2017-01-01 | 2017-01-01 06:22:20 |                     
|      2 | 2017-01-01 | 2017-01-01 06:40:49 |                     
|      3 | 2017-01-01 | 2017-01-01 07:13:52 |                     
|      4 | 2017-01-01 | 2017-01-01 10:04:32 |                     
|      5 | 2017-01-01 | 2017-01-01 11:00:14 |                     
|      6 | 2017-01-01 | 2017-01-01 12:03:33 |                     
|      7 | 2017-01-01 | 2017-01-01 13:23:06 |                     
|      8 | 2017-01-01 | 2017-01-01 16:15:42 |                     
|      9 | 2017-01-01 | 2017-01-01 16:23:17 |                     
|     10 | 2017-01-01 | 2017-01-01 17:39:11 |                     
|     11 | 2017-01-01 | 2017-01-01 22:08:30 |                     
|     12 | 2017-01-01 | 2017-01-01 22:19:47 |                     
|     13 | 2017-01-01 | 2017-01-01 22:44:57 |                     
|     14 | 2017-01-02 | 2017-01-02 00:36:35 |                     
|     15 | 2017-01-02 | 2017-01-02 01:32:37 |                     
|     16 | 2017-01-02 | 2017-01-02 04:48:50 |                     
|     17 | 2017-01-02 | 2017-01-02 05:47:53 |                     
|     18 | 2017-01-02 | 2017-01-02 08:23:56 |                     
|     19 | 2017-01-02 | 2017-01-02 08:36:55 |                     
|     20 | 2017-01-02 | 2017-01-02 09:55:27 |                     
+--------+------------+---------------------+                     
20 rows in set (0.00 sec)                                         
```


$$\Gamma(z) = \int_0^\infty t^{z-1}e^{-t}dt\,.$$ \[\Gamma(z) = \int_0^\infty t^{z-1}e^{-t}dt\,.\]

$$x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}$$ \[x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}\]

$${x}_{1,2}=\frac{-b\pm \sqrt{b^2-4ac}}{2a}$$ \[{x}_{1,2}=\frac{-b\pm \sqrt{b^2-4ac}}{2a}\]

$$f(x) = \int_{-\infty}^\infty\hat f(\xi)\,e^{2 \pi i \xi x}\,d\xi$$ \[f(x) = \int_{-\infty}^\infty\hat f(\xi)\,e^{2 \pi i \xi x}\,d\xi\]
    
This apartment has an area of $100m^2$, one must consider the value of $x_z$ This apartment has an area of $100m^2$ One must consider the value of $x_z$
    y^(a+b)^ then something like x~y,z~ y^(a+b)^ then something like x~y,z~
    
This formula $f(x) = x^2$ is an example. This formula $f(x) = x^2$ is an example.
         
   $\sum_{i=0}^n i^2 = \frac{(n^2+n)(2n+1)}{6}$

$\sum_{i=0}^n i^2 = \frac{(n^2+n)(2n+1)}{6}$
