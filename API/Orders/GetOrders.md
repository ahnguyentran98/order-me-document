```mermaid
sequenceDiagram
    participant Client
    participant OrdersCtrl
    participant OrdersService
    participant OrdersRepo

    Client->>OrdersCtrl: GET /orders/{table_id}
    OrdersCtrl->>OrdersService: getOrdersByTable(table_id)
    OrdersService->>OrdersRepo: findByTableId(table_id)
    OrdersRepo-->>OrdersService: orderData
    OrdersService-->>OrdersCtrl: orderData
    OrdersCtrl-->>Client: 200 OK (orderData)