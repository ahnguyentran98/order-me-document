```mermaid
sequenceDiagram

title Admin create user /users/

UserCtrl -> UserCtrl: validate request data

UserCtrl --> UserService: createUser(userInfo)

UserService -> UserService: validate existed user

UserService --> UserRepo: saveAndFlush(user)

UserService --> UserCtrl: return success

