```mermaid
sequenceDiagram

title Create Ticket /tickets/

TicketCtrl -> TicketCtrl: Validate request data

TicketCtrl --> TicketService: createTicket(ticketInfo)

TicketService -> TicketService: proccess ticket info

TicketService --> TicketRepo: save(ticket)

TicketService --> TicketCtrl: return ticketInfo