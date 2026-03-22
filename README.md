# Furniture Rental Database System — Oracle SQL

A relational database designed for a multi-branch furniture rental business. Built as part of a Data and Distributed Systems module at the University of Staffordshire.

## Overview

The database models the core operations of a furniture rental company: customers renting individual furniture items across multiple branches, with staff, suppliers, inventory, and membership tracking all linked together.

The schema was designed from scratch — starting with an ERD, normalised to 3rd Normal Form (3NF), then implemented in Oracle SQL with full referential integrity.

## ERD

![Entity Relationship Diagram](erd.png)

## Schema — Tables & Purpose

| Table            | Purpose                                                                 |
|------------------|-------------------------------------------------------------------------|
| `CUSTOMER`       | Stores customer personal details                                        |
| `RENTALS`        | Records rental transactions per customer                                |
| `FURNITURE`      | Holds furniture product types (e.g. Chair, Table)                      |
| `FURNITURE_ITEM` | Represents individual physical items with availability, colour, and size|
| `SUPPLIER`       | Supplier contact details                                                |
| `BRANCHES`       | Branch locations and contact info                                       |
| `MEMBERSHIP`     | Links customers to branches with a join date                            |
| `INVENTORY`      | Tracks stock quantity per furniture type per branch                     |
| `STAFF`          | Staff records linked to branches with roles and line managers           |

## Relationships

- A **Customer** can have many **Rentals** and many **Memberships**
- A **Furniture** type can have many **Furniture Items** (individual physical units)
- A **Supplier** can supply many **Furniture** types
- A **Branch** can have many **Staff**, **Memberships**, and **Inventory** entries

## Key SQL Concepts Demonstrated

- **Schema design** — primary keys, foreign keys, NOT NULL constraints, referential integrity
- **Normalisation** — schema in 3NF: no repeating groups, all non-key attributes depend on the primary key, no transitive dependencies
- **Views** — three reporting views created:
  - `FURNITURE_STOCK_VIEW` — stock levels per branch
  - `FURNITURE_FEATURES_VIEW` — item colour, size, and availability
  - `RENTAL_HISTORY_VIEW` — full rental history per customer

## How to Run

1. Open Oracle SQL Developer (or any Oracle-compatible SQL environment)
2. Run `schema.sql` to create all tables, insert sample data, and create views
3. Query any table or view directly — e.g.:

```sql
SELECT * FROM FURNITURE_STOCK_VIEW;
SELECT * FROM RENTAL_HISTORY_VIEW;
```

## Tech

- Oracle SQL (PL/SQL syntax)
- Designed and tested in Oracle SQL Developer
