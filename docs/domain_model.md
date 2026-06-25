# Domain Model v1

## Domain Entities

### Customer

Represents a buyer within the Olist marketplace.

### Order

Represents a purchase transaction initiated by a customer.

### OrderItem

Represents an individual line item within an order.

### Payment

Represents one or more payment transactions associated with an order.

### Review

Represents customer feedback submitted for an order.

### Product

Represents an item available for purchase.

### Seller

Represents a merchant offering products through the marketplace.

### Category

Represents the classification of products.

---

# Relationship Model

## Customer → Orders

Relationship:

```text
Customer 1:N Orders
```

A customer can place multiple orders.

---

## Order → OrderItems

Relationship:

```text
Order 1:N OrderItems
```

An order may contain multiple products.

---

## Order → Payments

Relationship:

```text
Order 1:N Payments
```

An order may have multiple payment records.

---

## Order → Reviews

Relationship:

```text
Order 1:N Reviews
```

An order may receive multiple reviews.

---

## Product → OrderItems

Relationship:

```text
Product 1:N OrderItems
```

A product can appear in multiple orders.

---

## Seller → OrderItems

Relationship:

```text
Seller 1:N OrderItems
```

A seller can sell many products across many orders.

---

## Category → Products

Relationship:

```text
Category 1:N Products
```

A category can contain multiple products.

---

# Complete Domain Graph

```text
Customer
    │
    │ 1:N
    ▼

Order
    │
    ├──────────────┐
    │              │
    │ 1:N          │ 1:N
    ▼              ▼

OrderItem      Payment

    │
    │ N:1
    ▼

Product

    │
    │ N:1
    ▼

Category

Order
    │
    │ 1:N
    ▼

Review

Seller
    │
    │ 1:N
    ▼

OrderItem
```

---

# Core Business Flow

```text
Customer
   ↓

Order
   ↓

OrderItem
   ↓

Product
   ↓

Seller

Order
   ↓

Payment

Order
   ↓

Review
```

This domain model serves as the canonical business model for the MySQL operational layer and will be used as the foundation for downstream PostgreSQL transformations, Snowflake dimensional modeling, and BigQuery analytical datasets.
