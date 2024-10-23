```mermaid
sequenceDiagram

Client->>TableCtrl: POST /tables
    TableCtrl->>TableService: createTable(data)
    TableService->>TableRepo: save(data)
    TableRepo-->>TableService: confirmation
    TableService-->>TableCtrl: confirmation
    TableCtrl-->>Client: 201 Created