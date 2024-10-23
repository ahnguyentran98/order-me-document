```mermaid
sequenceDiagram
    participant Client
    participant MenuCtrl
    participant MenuService
    participant MenuRepo

    Client->>MenuCtrl: POST /menu
    MenuCtrl->>MenuService: createMenu(data)
    MenuService->>MenuRepo: save(data)
    MenuRepo-->>MenuService: confirmation
    MenuService-->>MenuCtrl: confirmation
    MenuCtrl-->>Client: 201 Created