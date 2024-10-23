```mermaid
sequenceDiagram

title Admin remove user /users/{user_id}

UserCtrl -> UserCtrl: validate request data

UserCtrl --> UserService: deleteUser(userId)

UserService --> UserRepo: getUserById(userId)

UserRepo --> UserService: return user

UserService -> UserService: user.setIdDelete(true)

UserService --> UserRepo: saveAndFlush(user)

UserService --> UserCtrl: return success

