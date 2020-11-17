---
shortTitle: References
title: API References
---

Our API is a HTTPS/REST for general operations such as sending POST requests and receiving GET requests

---

###### Base URL

```markdown
https://paradisebots.net/api/v1
```

---

## Authentication
To access our API you need to authorize yourself, this can be done by using your Paradise Bot List Token. Your token can be obtained from your Bots page when you are logged into the site. 
Authentication is performed with the Authorization HTTP header in the format `"authorization": "TOKEN"`

* Note: The token used below is an example, Please generate your own from your bots edit page.

---

###### Example Authorization Header

<GatewayRoute
  eventName="request_authorization"
  room="OAuth"
  sentFrom="verified_bot"
  requiresAuthorization
  payload={{
    token: {
      type: "authorization: 6jShKo4HBuMIEdTeFUk1",
      description: "Authorization Token"
    }
  }}
/>

---

## Required Data
The following params should be provided as the `body` or `payload` of your request when posting stats to our site.

---

###### Parameters
Param | Type | Optional | Description
|----------|----------|----------|----------|
server_count | Number | No | The Server Count of the bot requesting to post stats.
shard_count | Number | No | The Shard Count of the bot requesting to post stats.

---

## Available Data
The following data is available through our site using GET methods.

---

###### Arguments
Arg | Type | Optional | Description
|----------|----------|----------|----------|
username | String | Yes | The bots username.
botid | Snowflake | Yes | The bots ID.
owner | Snowflake | Yes | The bot owners ID.
additionalOwners | String | Yes | The IDs of all additional owners (if any).
Prefix | String | Yes | The bots listed prefix(s).
shortDescription | String | Yes | The bots short description (Shown on cards).
longDescription | String | Yes | The bots long description (Can be markdown).
votes | Number | Yes | The bots total number of upvotes.
usersVoted | String | Yes |IDs of the last 10 users who voted (May return less).
totalUsersVoted | Number | Yes | Total number of Individual Users who have voted (Each user = 1).
server | String | Yes | Link to the bots support server.
website | String | Yes | Link to the bots website.
github | String | Yes | Link to the bots github.
donate | String | Yes | Link to donate to the bot.
tags | String | Yes | List of the bots tags.
library | String | Yes | The library the bot was made with.
servers | Number | Yes | Number of total servers the bot is in.
shards | Number | Yes | Number of total shards the bot has.
