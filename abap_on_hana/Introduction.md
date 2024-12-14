# Introduction to ABAP on HANA

As we all know SAP hass a 3 tier architecture.
- Application layer
- Presentation layer
- Database Layer

In ABAP, we used db as Oracle, db6 and others but in ABAP on HANA, SAP came up with there own db. 

In this db, it is pwerful than other legacy db's. Some need to change programming as well. 

Previously, with the old dbs and ABAP , we were doing things on APplication layer. With ABAP on HNA and new db m complex part and process can be handled at db level itself and should be perform there. 

## Why SAP came up with new db ? 
Due to various hardware and software innovations. 
As more efficent hardware are now availble at lower price,, and softwares are also evolving with time more computational power can be achieved. 

## HANA Magic Words :  
- [Hardware Innovations](https://github.com/pcyph8r/abap_development_s4hana/blob/0f63d0059ea2b10ed51d29b1cddf92a7a2a1d942/abap_on_hana/Hardware%20Innovations.md)
  - In Memory Database 
- [Software Innovations](https://github.com/pcyph8r/abap_development_s4hana/blob/7bb1f13fb1094d32f6d76cca0556788058d725f8/abap_on_hana/Software%20Innovations.md)
   - Column Store & Row Store
   - Data Compression
   - OLTP vs OLAP
   - Table Partioning
   - Insert Only Approach
   - Code Push Down 

