
# MedSure — Database Schema

## 1. Purpose

This document describes the proposed database structure for storing medicine information and price records.

## 2. Medicines Table

| Field | Type | Description |
|---|---|---|
| medicine_id | INTEGER / UUID | Unique medicine identifier |
| brand_name | VARCHAR | Brand or product name |
| active_ingredients | TEXT | Active ingredient information |
| strength | VARCHAR | Labeled strength |
| dosage_form | VARCHAR | Tablet, capsule, syrup, etc. |
| manufacturer | VARCHAR | Manufacturer name |

## 3. Price Records Table

| Field | Type | Description |
|---|---|---|
| price_id | INTEGER / UUID | Unique price record identifier |
| medicine_id | INTEGER / UUID | Reference to the medicine |
| source_name | VARCHAR | Store or data provider |
| product_url | TEXT | Link to the listed product |
| price | DECIMAL | Listed price |
| currency | VARCHAR | Currency code, such as INR |
| checked_at | TIMESTAMP | Time the price was checked |

## 4. Relationships

- Each medicine has a unique medicine identifier.
- A medicine can have multiple price records from different sources.
- Each price record refers to one medicine.
- Price records should retain their source and timestamp so users can understand how current the information is.

## 5. Data Validation

- Store prices as decimal values.
- Validate required fields before inserting records.
- Keep ingredient, strength, and dosage-form data structured wherever possible.
- Do not assume products are interchangeable solely because their names are similar.

## 6. Implementation Status

This is a proposed schema for planning. It has not been tested against a live database.
