# List of events that triggers distributed transactions

1. Account deletion
    - delete account from user ms
    - delete lottery participation if present
    - delete user from the recipients of messages
    - delete user from notifications

2. Lottery draw
    - update points to users in user microservice