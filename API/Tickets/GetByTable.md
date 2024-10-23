```mermaid
sequenceDiagram

title Get by Table /tickets/tables/{tables_id}

TicketCtrl -> TicketCtrl: validate reuqest data

TicketCtrl --> TicketService: GetByTable(tableId)

TicketService -> TableTicketService: GetTicketIDByTable(tableId)

TableTicketService --> TableTicketRepo: getByTable(tableId)

TableTicketRepo --> TableTicketService: return tableTicket

TableTicketService --> TicketService: return ticketId

TicketService --> TicketRepo: getTicketById(ticketId)

TicketRepo --> TicketService: return ticket

TicketService --> TicketCtrl: return ticket