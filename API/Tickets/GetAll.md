```mermaid
sequenceDiagram

title Get all Ticket /tickets/

TicketCtrl --> TicketService: GetTickets

TicketService --> TicketRepo: GetTickets

TicketService --> TicketCtrl: return List<Ticket>