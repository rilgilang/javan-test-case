# Inventory Management System API

A RESTful API for managing inventory items and stock levels with asynchronous stock updates using message brokers.

## Features

- **Item Management**: Create, read, update, and delete inventory items
- **Stock Management**: Increase or decrease stock with validation
- **Stock History**: Automatic logging of all stock changes
- **Asynchronous Updates**: Stock updates processed via message broker (RabbitMQ/Redis/NATS)

# ============================================

# ITEM MANAGEMENT

# ============================================

# Create Item

curl -X POST http://localhost:3000/item \
 -H "Content-Type: application/json" \
 -d '{
"name": "mie goreng",
"stock": 1000
}'

# Get All Items

curl -X GET http://localhost:3000/item

# Get Item Detail

curl -X GET http://localhost:3000/item/{id}

# Update Item

curl -X PUT http://localhost:3000/item/{id} \
 -H "Content-Type: application/json" \
 -d '{
"name": "mie goreng updated"
}'

# Delete Item

curl -X DELETE http://localhost:3000/item/{id}

# ============================================

# STOCK MANAGEMENT

# ============================================

# Increase Stock

curl -X POST http://localhost:3000/item/{id}/stock/increase \
 -H "Content-Type: application/json" \
 -d '{
"qty": 20
}'

# Reduce Stock

curl -X POST http://localhost:3000/item/{id}/stock/reduce \
 -H "Content-Type: application/json" \
 -d '{
"qty": 20
}'

## Tech Stack

- **Runtime**: Golang
- **Database**: PostgreSQL
- **Message Broker**: RabbitMQ / Redis / NATS
