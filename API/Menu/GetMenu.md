```mermaid
sequenceDiagram
    participant Client
    participant MenuCtrl
    participant MenuService
    participant MenuRepo

    Client->>MenuCtrl: GET /menu
    MenuCtrl->>MenuService: getMenu()
    MenuService->>MenuRepo: findAll()
    MenuRepo-->>MenuService: menuData
    MenuService-->>MenuCtrl: menuData
    MenuCtrl-->>Client: 200 OK (menuData)