# Inventory Management System API

A RESTful API for managing inventory items and stock levels with asynchronous stock updates using message brokers.

## Features

- **Item Management**: Create, read, update, and delete inventory items
- **Stock Management**: Increase or decrease stock with validation
- **Stock History**: Automatic logging of all stock changes
- **Asynchronous Updates**: Stock updates processed via message broker (RabbitMQ/Redis/NATS)

# EndPoint

# ========================================

# ITEM MANAGEMENT

# ========================================

# Create Item

```
    curl -X POST http://localhost:3000/item \
    -H "Content-Type: application/json" \
    -d '{
    "name": "mie goreng",
    "stock": 1000
    }'
```

200 OK

```
{
    "status" : "Ok",
    "data" : {
        "id" : "uuid",
        "name"  : "mie goreng",
        "stock" : 1000,
        "created_at" : "2024-01-01T00:00:00Z",
        "updated_at" : "2024-01-01T00:00:00Z",
    },
    "message" : "ok"
}
```

# Get All Items

```
curl -X GET http://localhost:3000/item
```

200 OK

```
{
    "status" : "Ok",
    "data" : [
        {
            "id" : "uuid",
            "name"  : "mie goreng",
            "stock" : 1000,
            "created_at" : "2024-01-01T00:00:00Z",
            "updated_at" : "2024-01-01T00:00:00Z",
        }
    ],
    "message": "ok"
}
```

# Get Item Detail

```
curl -X GET http://localhost:3000/item/{id}
```

200 OK

```
{
    "status" : "Ok",
    "data" : {
        "id" : "uuid",
        "name"  : "mie goreng",
        "stock" : 1000,
        "created_at" : "2024-01-01T00:00:00Z",
        "updated_at" : "2024-01-01T00:00:00Z",
    },
    "message" : "ok"
}
```

# Update Item

```
curl -X PUT http://localhost:3000/item/{id} \
 -H "Content-Type: application/json" \
 -d '{
"name": "mie goreng updated"
}'
```

200 OK

```
{
    "status" : "Ok",
    "data" : {
        "id" : "uuid",
        "name"  : "mie goreng",
        "stock" : 1000,
        "created_at" : "2024-01-01T00:00:00Z",
        "updated_at" : "2024-01-01T00:00:00Z",
    },
    "message" : "ok"
}
```

# Delete Item

```
curl -X DELETE http://localhost:3000/item/{id}
```

200 OK

```
    "status" : "Ok",
    "message" : "berhasil menghapus item."
```

# ========================================

# STOCK MANAGEMENT

# ========================================

# Increase Stock

```
    curl -X PUT http://localhost:3000/item/{id}/stock/increase \
    -H "Content-Type: application/json" \
    -d '{
    "qty": 20
    }'
```

200 OK

```
{
    "status" : "Ok",
    "data" : {
        "id" : "uuid",
        "name"  : "mie goreng",
        "stock" : 1000,
        "created_at" : "2024-01-01T00:00:00Z",
        "updated_at" : "2024-01-01T00:00:00Z",
    },
    "message" : "ok"
}
```

# Reduce Stock

```
curl -X PUT http://localhost:3000/item/{id}/stock/reduce \
 -H "Content-Type: application/json" \
 -d '{
"qty": 20
}'
```

200 OK

```
{
    "status" : "Ok",
    "data" : {
        "id" : "uuid",
        "name"  : "mie goreng",
        "stock" : 1000,
        "created_at" : "2024-01-01T00:00:00Z",
        "updated_at" : "2024-01-01T00:00:00Z",
    },
    "message" : "ok"
}
```

400 Bad Request

```
{
    "status" : "Ok",
    "message" : "stock tidak boleh minus",
}
```

## Tech Stack

- **Runtime**: Golang
- **Database**: PostgreSQL
- **Message Broker**: RabbitMQ / Redis / NATS
