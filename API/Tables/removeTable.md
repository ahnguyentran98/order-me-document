```mermaid
sequenceDiagram

Client->>TableCtrl: DELETE /tables/{id}
    TableCtrl->>TableService: deleteTable(id)
    TableService->>TableRepo: getTableById(id)
    TableRepo-->>TableService: return table
    TableService -> TableService: table.setIsDelete(true)
    TableService->>TableRepo: saveAndFlush(table)
    TableService-->>TableCtrl: deletionConfirmed
    TableCtrl-->>Client: 204 No Content