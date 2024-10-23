```mermaid
sequenceDiagram

title Update Ticket /tickets/{id}

TicketCtrl -> TicketCtrl: validate reuqest data

TicketCtrl --> TicketService: updateTicket(ticketInfo, ticketId)

TicketService -> TicketService: getTicketById(ticketId)

TicketService --> TicketRepo: getTicketById(ticketId)

TicketRepo --> TicketService: return ticket

TicketService -> TicketService: updateTicketInfo

TicketService --> TicketRepo: saveAndFlush(ticket)

TicketService --> TicketCtrl: return ticket