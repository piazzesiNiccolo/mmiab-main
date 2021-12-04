# List of events that triggers distributed transactions

1. Account deletion
    - delete account from user ms
    - publishes '{"user_id":id}' on redis channel USER_DELETE, where id is the id of the deleted account
    - the lottery microservice listens for messages on USER_DELETE and cancel the participant from its db if present
    - the same is done in the messages microservice, where the id is deleted from every recipient list where it was present
    - the same is done in the notifications microservice

2. Lottery draw
    - update points to users in user microservice
    - publishes the event on channel POINTS_UPDATE, the message format will be '{"users": < list of objects like {"id":points}>}'
    - the user microservice subscribes to this channel and add the points to the winners when a message arrives

3. Message withdraw
    - same as lottery draw, excepts in this case the points will be negative