```mermaid
sequenceDiagram

 Client->>TableCtrl: GET /tables/{id}
    TableCtrl->>TableService: getTable(id)
    TableService->>TableRepo: findById(id)
    TableRepo-->>TableService: tableData
    TableService-->>TableCtrl: tableData
    TableCtrl-->>Client: 200 OK (tableData)