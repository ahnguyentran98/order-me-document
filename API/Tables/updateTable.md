```mermaid
sequenceDiagram


    Client->>TableCtrl: PUT /tables/{id}
    TableCtrl->>TableService: updateTable(id, data)
    TableService->>TableRepo: findById(id)
    TableRepo-->>TableService: return table
    TableService -> TableService: proccess update table
    TableService->>TableRepo: saveAndFlush(table)
    TableService-->>TableCtrl: updatedTable
    TableCtrl-->>Client: 200 OK (updatedTable)