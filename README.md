![SQL Server](https://img.shields.io/badge/SQL%20Server-CC2927?style=for-the-badge&logo=microsoftsqlserver&logoColor=white)
![T-SQL](https://img.shields.io/badge/T--SQL-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![Database Design](https://img.shields.io/badge/Database%20Design-Relational%20Schema-blue?style=for-the-badge)

# XYZ Trucking Database

SQL Server database prototype for managing trucking fleet operations, including drivers, trucks, trailers, haul records, cargo manifests, and truck maintenance.

---

## Tech Stack

- **Database:** Microsoft SQL Server
- **Tools:** Microsoft SQL Server Management Studio
- **Language:** T-SQL
- **Design:** Relational database design with lookup tables
- **Access Layer:** Stored procedures
- **Integrity:** Primary keys, foreign keys, unique indexes, and check constraints

---

## Core Features

- Driver, truck, trailer, haul, cargo manifest, and maintenance tracking
- Lookup tables for controlled values such as cargo type, item, truck type, truck body type, trailer type, maintenance type, and maintenance code
- Sample data for drivers, trucks, trailers, haul records, haul line items, lookup values, and maintenance records
- Stored procedures for inserting records into core and lookup tables
- Stored procedures for deleting records from core and lookup tables
- Stored procedures for selected update operations
- Report stored procedures for maintenance, haul records, haul inventory, and shipment weight
- Primary keys, foreign keys, unique indexes, and check constraints for data integrity

---

## Database Design

The database is designed around a simplified trucking workflow where each haul record is associated with one driver and one truck. Trucks may be single-unit vehicles or tractor-trailer vehicles, and tractor-trailer trucks are required to have trailer information.

Haul records store client, cargo type, start date, delivery date, mileage, and notes. Haul line items connect delivered inventory to a specific haul record. Maintenance records connect trucks to maintenance date ranges, maintenance types, and maintenance codes.

| Area | Tables |
|---|---|
| Fleet | `Truck`, `Trailer` |
| People | `Driver` |
| Hauls | `HaulRecord`, `HaulLineItem` |
| Maintenance | `Maintenance` |
| Lookup Data | `LUCargoType`, `LUItem`, `LUMaintenanceCode`, `LUMaintenanceType`, `LUTrailerType`, `LUTruckBodyType`, `LUTruckType` |

---

## Assignment Context

This project was created for a database design final project. The assignment required a prototype database system for XYZ Trucking, a fictional company managing fleet movement, cargo delivery, driver assignments, trailer information, and truck maintenance.

The project requirements included system design documents, tables in 3rd normal form, lookup tables, stored procedures for query, insert, and delete operations, in-code comments, create scripts, and insert scripts with lookup and sample data.

---

## Stored Procedures

The SQL script includes stored procedures for database operations and reports. Insert procedures add records to core and lookup tables. Delete procedures remove records by identifiers or record-specific values. Update procedures support selected changes, including driver commercial license status, truck mileage, trailer mileage, and haul record dates.

Report procedures include:

- `ReportMaintenance`
- `ReportHaulRecord`
- `ReportHaulRecordInventory`
- `ReportHaulShipmentWeight`

---

## Example Report Executions

```sql
USE XYZTruckingDatabase;
GO

EXEC dbo.ReportMaintenance
    @StartDate = '2021-01-01',
    @EndDate = '2021-12-31';
GO
```

```sql
USE XYZTruckingDatabase;
GO

EXEC dbo.ReportHaulShipmentWeight
    @HaulRecordID = 2;
GO
```

---

## Project Structure

```text
XYZTruckingDatabase/
    XYZTruckingDatabase.sql      Database creation, schema, sample data, constraints, and stored procedures
```

---

## Author

LV Marlowe
