```mermaid
sequenceDiagram

title Login /users/login

UserCtrl -> UserCtrl: validate request data

UserCtrl --> UserService: login(userInfo)

UserService --> UserRepo: getUserById(userId)

UserRepo --> UserService: return user

UserService -> UserService: proccess generate JWT token & security permission

UserService --> UserCtrl: return basicUserInfo

