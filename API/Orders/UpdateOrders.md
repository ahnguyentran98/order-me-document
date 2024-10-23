```mermaid
sequenceDiagram
    participant Client
    participant OrdersCtrl
    participant OrdersService
    participant OrdersRepo

    Client->>OrdersCtrl: PUT /orders/{order_id}
    OrdersCtrl->>OrdersService: updateOrder(order_id, data)
    OrdersService->>OrdersRepo: findById(order_id)
    OrdersRepo-->>OrdersService: existingOrder
    OrdersService->>OrdersRepo: update(order_id, data)
    OrdersRepo-->>OrdersService: updatedOrder
    OrdersService-->>OrdersCtrl: updatedOrder
    OrdersCtrl-->>Client: 200 OK (updatedOrder)