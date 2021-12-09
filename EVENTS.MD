# List of events that triggers asynchronous communication

- Account deletion

  1. An account is deleted from user ms

  2. The service publishes a message  {"user_id":id} on redis channel USER_DELETE, where id is the id of the deleted account

  3. The lottery service listens for messages on USER_DELETE and cancel the participant from its db if present.

  4. The same is done in the messages service, where the user is deleted from every recipient list where it was present (since we want sent messages to still arrive we ignore those where the deleted user,and in every message where the sender was the deleted account the id_sender field is put to None .

  5. the same is done in the notifications service, where every notification for the user is deleted.

- Lottery draw

  1. The lottery celery task draws the winners

  2. The lottery service publishes the event on channel POINTS_UPDATE, the message format will be {"users": < list of objects like {"id":points}>}

  3. The lottery service publishes a message on ADD_NOTIFY, the message format will be 

     {"notifications":list of objects like: 

     ​    {"id_message":None, 

     ​    "id_user":< winner>,

     ​    "for_sender":False,

     ​    "for_recipient":False,

     ​    "for_lottery":True,

     ​    "from_recipient":None}

     }

  3. the user service subscribes to POINTS_UPDATE and add the points to the winners when a message arrives
  4. The notification service subscribes to ADD_NOTIFY and add all the notifications arrived to its db

- Message withdraw

  1. When a message is withdrew, the message service publishes a message {"users":[{"id":points}]} with negative points on POINTS_UPDATE 
  2. The user service is subscribed to POINTS_UPDATE, and decrease the points of the user specified by id

- Delivered message

  1. The celery task checks which messages must be delivered 

  2. It publishes a message  on ADD_NOTIFY, the message format will be:

  ​    {"notifications":list of objects like: 

  ​       {"id_message": id of message delivered, 

  ​       "id_user":recipient,

  ​      "for_sender":False,

  ​      "for_recipient":True,

  ​       "for_lottery":False,

  ​       "from_recipient":None}

  ​     }

  3. The notification service is subscribed to ADD_NOTIFY and add all the notifications in the message to its db

- Read message

  1. A recipient reads a delivered message

  2. When this happens the message service publishes a message on ADD_NOTIFY with only one notification in the list  with 

     the format {"id_message":id of read message,"id_user":sender,"for_sender":True,"for_recipient":False,"for_lottery":False, "from_recipient":recipient that read the message}

  3. The notification service gets the message and adds the notification for the sender