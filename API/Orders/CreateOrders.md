```mermaid
sequenceDiagram
    participant Client
    participant OrdersCtrl
    participant OrdersService
    participant OrdersRepo

    Client->>OrdersCtrl: POST /orders/{table_id}
    OrdersCtrl->>OrdersService: createOrder(table_id, data)
    OrdersService -> OrdersService: proccess create order
    OrdersService->>OrdersRepo: saveAndFlush(order)
    OrdersRepo-->>OrdersService: confirmation
    OrdersService-->>OrdersCtrl: confirmation
    OrdersCtrl-->>Client: 201 Created
