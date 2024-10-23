```mermaid
sequenceDiagram

title Admin get user /users/

UserCtrl --> UserService:  GetUsers

UserService --> UserRepo: GetUser

UserRepo --> UserService: return userList

UserService --> UserCtrl: return userList

