## Software Innovations
 ### 1. Column Store & Row Store

In HANA db,, SAP started using column store along with row store. 
  
  | Row Store | Column Store |
  |-----|---------------|
  |     Data is stored in db row by row. | Data is stored in db column by column. |

#### Example table
 
  | Order | Customer | Curency | Amount |
  |-------|----------|---------|--------|
  |  456  | PK | INR | 50 |
  |  457  | PP | INR | 60 |
  |  458  | VG | INR | 90 |
  |  459  | MK | INR | 500 |
  |  460  | JM | INR | 150 |



+ **Row Store** -
  In the above table, the data will get stored row by row next to each other.
   ##### Allocated Memory
  Each row is stored together in db.  

  | 456  PK  INR  50 | 457  PP  INR  60 | 458  VG  INR  90 | 459  MK  INR  500 |
  |------------------|------------------|------------------|-------------------|

   ##### Advantages
  - If we want to access all the data, then we can get easily.
  Example : IF we are geting all data of order 459, it has to only traverse through first value and it would be easily availble.

   ##### Disadvantages
  - If we want to do sum of amount of order, then it needs to pick the amount by traversing through each value and it will take time.
 
> [!NOTE]
> We create the table, we define primary index, based on that data is sorted and stored in the table. If we create, secondary index, based on those fields data will be sorted and linked to main table for easy access. 

+ **Column Store** -
  In the above table, the data will get stored column wise. Context of column next to each other. 
   ##### Allocated Memory
  Each column is stored together in db.  

  | 456  456  457  458 | PK  PP  VG  MK | INR  INR  INR  INR | 50  60  90  500 |
  |------------------|------------------|------------------|-------------------|

   ##### Advantages
  - If we have to access and sum up, then it its easy to perform
  - Since data is stored in column wise, identical data can be compressed easily, thus releasing high compress rate.
  - Secondary indexes are not needed in most times.
    
   ##### Disadvantages
  - Getting all the data will be performance issue. 

#### How to decide ? 

- Column Store
  - When we have large table with multiple fields.
  - When we use very lesser fields of larger table.
  - When we are performing functions on columns, we aredoing additons, affregations ,search operations.
  - When we are hitting table with secondary indexes and not using primary index.
    
- Row Store
  - Small number of fields or all the fields are required most of times.
  - If we are not going to perform anyu functions or operations such as aggregation and addition
  - If table is fulley buffered on application layer
  - If the records are also very loss
 
#### How to make ? 
- Go to SE11.
- Technical Settings -> DB specific properties.
- Selec the appropriate options

> [!NOTE]
> - Frequently not to be changed.
> - Intitally should be decided and fixed for the table.It overloads the table to convert from one form to another. 

  
### 2. Data Compression 
- Lower memory requried
- Data transfer to CPU is fast
- Fast processing in Integer

It will store all string or text related data in dictionary vectors such as : 

#### Example table
 
  | Record | Name | Location | Gender |
  |-------|----------|---------|--------|
  |  3  | Brown | IN | M |
  |  4  | Brown | IN | M |
  |  5  | Doe | US | F |
  |  6  | Doe | US | F |
  |  7  | Smith | CA | M |


  ###### Name Attribute Vector 
  | Key | Vector |
  |-----|--------|
  | Brown | 7 |
  | Doe | 8 |
  | Smith | 9 |
  

  ###### Gender Attribute Vector 
   | Key | Vector |
  |-----|--------|
  | M | 1 |
  | F | 2 |
  
  ###### Location Attribute Vector 
   | Key | Vector |
  |-----|--------|
  | IN | 5 |
  | US | 6 |
  | CA | 7 |
  

  ###### Compressed Name table
 | Value | 7 | 7 | 8 | 8 | 9 |
 |-------|---|---|---|---|---|
 | Row   | 3 | 4 | 5 | 6 | 7 |


  ###### Compressed Gender table
 | Value | 1 | 1 | 2 | 2 | 1 |
 |-------|---|---|---|---|---|
 | Row   | 3 | 4 | 5 | 6 | 7 |

 
  ###### Compressed Location table
 | Value | 5 | 5 | 6 | 6 | 7 |
 |-------|---|---|---|---|---|
 | Row   | 3 | 4 | 5 | 6 | 7 |


### 3. OLTP vs OLAP 

  | OLTP | OLAP |
  |-----|---------------|
  | Online Transactional Processing | Online Analytic Processing |
  | Day to Day Operations | Decision Making Planning Problem Solving |
  | Less Data compared to OLAP hence fast processing | Huge data hencce slow processing |
  | Current data (6-18 months) | Historic Data (in years) |
  | Read/Update/Add/Delete/Modify  | Read only |
  | Simple Queries | Very Complex Queries |
  | Row Store  | Column Store |

### 4. Table Partioniting 
### 5. Insert Only Approach 
### 6. Code Pushdown 


