
# API routes
List of endpoints of the API with a brief description


### Home
| monolith                                    | mmiab               | Status | Description |
| ------------------------------------------- | ------------------- | :-: | -------- |
| /                                           | /                   | ? | Home endpoint |

### User
| monolith                                    | mmiab               | Status | Description |
| ------------------------------------------- | ------------------- | :-: | -------- |
| /login                                      | /login                 | ? | Logs the user in |
| /logout                                     | /logout                | ? | Logs the user out |
| /create_user                                | /create_user           | y | Lets the user to create a new account |
| /user/profile                               | /profile               | y | Shows the user profile of the logged user |
| /user/profile/edit                          | /profile/edit          | / | Lets the user edit his own profile |
| /users/{id}                                 | /user/{id}             | y | Shows the user profile of any user |
| /user_list                                  | /users                 | y | Shows a list of users |
| /user/delete                                | /user/delete           | y | Lets the user delete his own account |
| /user/content_filter                        | /content_filter        | y | Lets the user toggle the content filter option |
| /user/report/{id}                           | /report/{id}           | y | Lets the user report another user |
| /user/blacklist                             | /blacklist             | y | Shows the list of blacklisted users by the logged user |
| /user/blacklist/add/{id}                    | /blacklist/{id}/add    | y | Lets the user add a new user to the blacklist |
| /user/blacklist/remove/{id}                 | /blacklist/{id}/remove | y | Lets the user remove a user from the blacklist |

### Notification
| monolith                                    | mmiab               | Status | Description |
| ------------------------------------------- | ------------------- | :-: | -------- |
| /notification                               |                     |   | Returns a JSON with all the notifications for the user |

### Message
| monolith                                    | mmiab               | Status | Description |
| ------------------------------------------- | ------------------- | :-: | -------- |
| /draft                                      |                     |   | Creates a new message as draft |
| /draft/edit/{id}                            |                     |   | Edits a draft |
| /send_message/{id}                          |                     |   | Sends a message |
| /message/{id}/delete                        |                     |   | Lets a recipient delete a read message |
| /draft/{id}/delete                          |                     |   | Lets the creator of a draft delete it |
| /message/{id}/withdraw                      |                     |   | Lets a user withdraw a sent message |
| /message/{id}/reply                         |                     |   | Lets a recipient reply to a received message |
| /forwarding/{id}                            |                     |   | Lets a user forward a sent or received message |
| /recipients                                 |                     |   | Returns a JSON with all available recipients for the current user |
| /timeline                                   |                     |   | Shows the timeline moth view for the current month |
| /timeline/day/{year}/{month}/{day}/sent     |                     |   | Shows the timeline day view of sent messages for a specific day |
| /timeline/day/{year}/{month}/{day}/received |                     |   | Shows the timeline day view of received messages for a specific day |
| /timeline/month/{year}/{month}              |                     |   | Shows the timeline moth view for a specific month |
| /read_message/{id}                          |                     |   | Lets an entitled user to read a specific message |
| /message/list/sent                          |                     |   | Shows the list of sent messages |
| /message/list/received                      |                     |   | Shows the list of received messages |
| /message/list/draft                         |                     |   | Shows the list of drafts |

### Lottery
| monolith                                    | mmiab               | Status | Description |
| ------------------------------------------- | ------------------- | :-: | -------- |
| /lottery/participate                        |                     |   | Lets the user participate to the lottery |
| /lottery                                    |                     |   | Shows the current status of the lottery to the user |

#### Legend
| Symbol | Description |
| :----: | ----------- |
| y      | Completed   |
| /      | Almost completed, small edits required | 
| ?      | Not completed, to edit |
|        | Not implemented | 

