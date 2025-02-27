# CDS Views 
A set of domain specific language and services for defining and consuming sementically rich data models. 

- Domain Specific Language
  - DDL -> Data Definition Language
  - DQL -> Data Query Language
  - DCL -> Data Control Language
    
- Sementically Rich Data models
  - Simple Data enriched using annotations, expressions and associations.
  -   Apart from tables, extra data and details are there like if CDS is being used for fiori what would be the field descripitons, what F4 help values will come. All infor embedded into CDS


 ## Types of CDS VIews 

 There are mutliple types of CDS views and are diffrentiated as follows : 

  | ABAP CDS | HANA CDS |
  |----------|----------|
  | Developed by ABAP person | Developed by HANA native developers. |
  | Open SQL used | In SAP HANA, only native SQL is used.  |
  | On ABAP application server  | HANA XS |
  | Supports ABAP application| Supports HANA app |
  | Part of DDIC | Not part of DDIC |


  | CDS View | Classical DB View |
  |----------|----------|
  | code push down follow execute code at db level | only join the table dont follow code push down |
  | inner,outerjoin,association | only inner join |
  | union is possible | union is not possible |
  | parameters are allowed | parameters are not allowed |
  | nested view | Not nested view |
