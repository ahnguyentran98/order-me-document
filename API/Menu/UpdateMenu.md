```mermaid
sequenceDiagram
    participant Client
    participant MenuCtrl
    participant MenuService
    participant MenuRepo

    Client->>MenuCtrl: PUT /menu/{id}
    MenuCtrl->>MenuService: updateMenu(id, data)
    MenuService->>MenuRepo: findById(id)
    MenuRepo-->>MenuService: existingMenu
    MenuService->>MenuRepo: update(id, data)
    MenuRepo-->>MenuService: updatedMenu
    MenuService-->>MenuCtrl: updatedMenu
    MenuCtrl-->>Client: 200 OK (updatedMenu)