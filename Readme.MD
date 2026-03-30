# Inventory Management System API

A RESTful API for managing inventory items and stock levels with asynchronous stock updates using message brokers.

## Features

- **Item Management**: Create, read, update, and delete inventory items
- **Stock Management**: Increase or decrease stock with validation
- **Stock History**: Automatic logging of all stock changes
- **Asynchronous Updates**: Stock updates processed via message broker (RabbitMQ/Redis/NATS)

## Tech Stack

- **Runtime**: Golang
- **Database**: PostgreSQL
- **Message Broker**: RabbitMQ / Redis / NATS
