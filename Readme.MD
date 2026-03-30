Item Management
Get Item
Get Item Detail
Create Item
Update Item
Delete Item

Stock Management
Update Stock

Stock History
Stock history log

Items
ID
Name
Stock
CreatedAt
UpdatedAt

Stock Log
ID
ItemID
Type Enun(In, Out)
Qty
CreatedAt
UpdatedAt

// Create
POST /item
request
{
"name" : "mie goreng",
"stock" : 1000
}

// GET ALL
GET /item
response
[
{
"id" : "uuid",
"name" : "mie goreng",
"stock" : 1000,
"created_at" : timestampz,
"Updated_at" : timestampz,
}
]

// Get Item Detail
GET /item/:id
response
{
"id" : "uuid",
"name" : "mie goreng",
"stock" : 1000,
"created_at" : timestampz,
"Updated_at" : timestampz,
}

// Update Item
PUT /item/:id
request
{
"name" : "mie goreng",
}

response
{
"data": {
"id" : "uuid",
"name" : "mie goreng",
"stock" : 1000,
"created_at" : timestampz,
"Updated_at" : timestampz,
}
"message": "ok"
}

// DELETE Item
DELETE /item/:id

response
{
"status": "ok",
"message": "success"
}

// STOCK MANAGEMENT

//Add stock
POST /item/:id/stock/increase
request
{
"qty" : 20
}

response
{
"data": {
"id" : "uuid",
"name" : "mie goreng",
"stock" : 1000,
"created_at" : timestampz,
"Updated_at" : timestampz,
},
"message": "ok"
}

//Reduce stock
POST /item/:id/stock/reduce
request
{
"qty" : 20
}

response
200
{
"data": {
"id" : "uuid",
"name" : "mie goreng",
"stock" : 1000,
"created_at" : timestampz,
"Updated_at" : timestampz,
},
"message": "ok"
}

// Stock tidak boleh minus
400
{
"status": "error",
"message" : "stock tidak boleh minus",
}

Flow:

1. Update stock
   ketika update stock akan disimpan ke message broker yang kemudian akan diconsume
   dan di update secara asynchronous
   (contoh broker: RabbitMQ, Redis, NATS)
2.
