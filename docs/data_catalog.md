# 📘 Data Catalog for Gold Layer

## Overview
The **Gold Layer** is the business-level data representation, structured to support analytical and reporting use cases. It consists of **dimension tables** and **fact tables** for specific business metrics.

---

## 1. `gold.dim_customers`

**Purpose**: Stores customer details enriched with demographic and geographic data.

| **Column Name**   | **Data Type**   | **Description**                                                                 |
|-------------------|------------------|----------------------------------------------------------------------------------|
| `customer_key`    | INT              | Surrogate key uniquely identifying each customer record in the dimension table. |
| `customer_id`     | INT              | Unique numerical identifier assigned to each customer.                          |
| `customer_number` | NVARCHAR(50)     | Alphanumeric identifier used for tracking and referencing customers.            |
| `first_name`      | NVARCHAR(50)     | The customer's first name.                                                      |
| `last_name`       | NVARCHAR(50)     | The customer's last name.                                                       |
| `country`         | NVARCHAR(50)     | Country of residence (e.g., `'Australia'`).                                     |
| `marital_status`  | NVARCHAR(50)     | Marital status (e.g., `'Married'`, `'Single'`).                                 |
| `gender`          | NVARCHAR(50)     | Gender (e.g., `'Male'`, `'Female'`, `'n/a'`).                                   |
| `birthdate`       | DATE             | Date of birth (e.g., `1971-10-06`).                                             |
| `create_date`     | DATE             | When the customer record was created in the system.                             |

---

## 2. `gold.dim_products`

**Purpose**: Provides information about the products and their attributes.

| **Column Name**         | **Data Type**   | **Description**                                                                 |
|--------------------------|------------------|----------------------------------------------------------------------------------|
| `product_key`           | INT              | Surrogate key for each product.                                                 |
| `product_id`            | INT              | Unique product ID for internal use.                                             |
| `product_number`        | NVARCHAR(50)     | Alphanumeric code for the product.                                              |
| `product_name`          | NVARCHAR(50)     | Descriptive product name.                                                       |
| `category_id`           | NVARCHAR(50)     | Identifier linking to the product's category.                                   |
| `category`              | NVARCHAR(50)     | High-level classification (e.g., `'Bikes'`, `'Components'`).                    |
| `subcategory`           | NVARCHAR(50)     | Detailed classification within the category.                                    |
| `maintenance_required`  | NVARCHAR(50)     | Whether the product needs maintenance (`'Yes'` / `'No'`).                        |
| `cost`                  | INT              | Base price of the product.                                                      |
| `product_line`          | NVARCHAR(50)     | Series or line the product belongs to (e.g., `'Road'`, `'Mountain'`).           |
| `start_date`            | DATE             | When the product became available.                                              |

---

## 3. `gold.fact_sales`

**Purpose**: Stores transactional sales data for analytical purposes.

| **Column Name**   | **Data Type**   | **Description**                                                                 |
|-------------------|------------------|----------------------------------------------------------------------------------|
| `order_number`    | NVARCHAR(50)     | Unique identifier for each sales order (e.g., `'SO54496'`).                      |
| `product_key`     | INT              | Surrogate key referencing `dim_products`.                                        |
| `customer_key`    | INT              | Surrogate key referencing `dim_customers`.                                       |
| `order_date`      | DATE             | Date when the order was placed.                                                  |
| `shipping_date`   | DATE             | Date when the order was shipped.                                                 |
| `due_date`        | DATE             | Date when payment was due.                                                       |
| `sales_amount`    | INT              | Total sale amount for the line item.                                             |
| `quantity`        | INT              | Number of units ordered.                                                         |
| `price`           | INT              | Price per unit for the product.                                                  |
