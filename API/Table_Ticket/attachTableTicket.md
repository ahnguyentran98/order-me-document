```mermaid
sequenceDiagram

title Attach table ticket POST /tables/{table_id}/ticket/{ticket_id}

Client --> TableTicketCtrl: POST /tables/{table_id}/ticket/{ticket_id}

TableTicketCtrl -> TableTicketCtrl: validate request data

TableTicketCtrl --> TableTicketService: AttachTableTicket(tableId, ticketId)

alt get ticket
TableTicketService --> TicketService: getTicketById(ticketId)

TicketService --> TableTicketService: return ticket

alt if ticket not found
TableTicketService --> TableTicketCtrl: return error 
TableTicketCtrl --> Client: 404 Not found
end
end

alt get table
TableTicketService --> TableService: getTableById(tableId)
TableService --> TableTicketService: return table
alt if table not found
TableTicketService --> TableTicketCtrl: return error
TableTicketCtrl --> Client: 404 Not found
end
end

TableTicketService -> TableTicketService: proccess create new tableTicket

TableTicketService --> TableTicketRepo: saveAndFlush(tableTicket)


TableTicketService --> TableTicketCtrl: return success

TableTicketCtrl --> Client: 200 OK



