![SQL Server](https://img.shields.io/badge/SQL%20Server-CC2927?style=for-the-badge&logo=microsoftsqlserver&logoColor=white)
![T-SQL](https://img.shields.io/badge/T--SQL-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![Database Design](https://img.shields.io/badge/Database%20Design-3rd%20Normal%20Form-blue?style=for-the-badge)

# XYZ Trucking Database

SQL Server database prototype for managing trucking fleet operations, including drivers, trucks, trailers, haul records, cargo manifests, and truck maintenance.

---

## Tech Stack

- **Database:** Microsoft SQL Server
- **Language:** T-SQL
- **Tools:** SQL Server Management Studio
- **Design:** Relational database design, 3rd normal form, lookup tables
- **Access Layer:** Stored procedures

---

## Core Features

- Driver, truck, trailer, haul, cargo manifest, and maintenance tracking
- Lookup tables for controlled values such as cargo type, truck type, truck body type, trailer type, maintenance type, and maintenance code
- Stored procedures for inserts, updates, deletes, queries, and reports
- Primary keys, foreign keys, and unique indexes for data integrity
- Create scripts and insert scripts with sample data for testing

---

## Database Design

The database is designed around a simplified trucking workflow where each haul is associated with one driver, one truck, and, when applicable, one trailer. Haul records connect operational details such as client, cargo type, start date, delivery date, mileage, and notes. Haul line items store the delivered inventory for each haul.

Lookup tables are used for repeated controlled values, including cargo types, truck types, truck body types, trailer types, maintenance types, and maintenance codes. This keeps the design normalized and reduces duplicated text across operational tables.

| Area | Tables |
|---|---|
| Fleet | Truck, Trailer |
| People | Driver |
| Hauls | HaulRecord, HaulLineItem |
| Maintenance | Maintenance |
| Lookup Data | LUCargoType, LUItem, LUMaintenanceCode, LUMaintenanceType, LUTrailerType, LUTruckBodyType, LUTruckType |

---

## Project Requirements

This project was created for a database design course. The assignment required a prototype database system for XYZ Trucking, a fictional company managing fleet movement, cargo delivery, driver assignments, and truck maintenance.

The final project required:

- Tables in 3rd normal form
- Lookup tables
- Stored procedures for query, insert, update, delete, and report operations
- Create scripts
- Insert scripts for lookup and sample data
- Sample data so the system could be tested

---

## Stored Procedures

The database uses stored procedures as the access layer for data manipulation and reporting. This supports the project requirement that a future web-based front end would interact with the database through stored procedures instead of direct table access.

Report procedures include:

- Truck maintenance by date range
- Haul records by truck and date range
- Haul inventory by truck and date range
- Shipment weight reporting

---

## Project Structure

```text
XYZTruckingDatabase/
    XYZTruckingDatabase.sql      Database creation, schema, sample data, constraints, and procedures
    README.md                    Project overview and setup instructions
```

---

## Getting Started

**Prerequisites**

- Microsoft SQL Server
- SQL Server Management Studio or another SQL Server client
- Permission to create and execute a database script

**Setup**

1. Open SQL Server Management Studio.
2. Connect to a SQL Server instance.
3. Open `XYZTruckingDatabase.sql`.
4. Review the database file path in the `CREATE DATABASE` statement and update it if needed.
5. Execute the script.
6. Confirm that the database, tables, sample data, indexes, keys, and stored procedures were created.

**Example report execution**

```sql
USE XYZTruckingDatabase;
GO

EXEC dbo.ReportMaintenance
    @StartDate = '2021-01-01',
    @EndDate = '2021-12-31';
GO
```

---

## Author

LV Marlowe
