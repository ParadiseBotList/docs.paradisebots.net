---
title: Python Library
---

## paradiseapi.py

This is a user made Python Library used for interacting with the Paradise API.

---
## Support

* [Discord](https://paradisebots.net/join)

* [GitHub](https://gist.github.com/TheUndeadBowman/9882928e04900c9b5bef4d236693a43d)

* [Bug Report](https://paradisebots.net/bug)

---

## Ratelimits
You can POST Server and Shard Count stats once every 5 minutes

---

###### Rate Limit Structure
| Route	| Request | Requests Allowed Per 5 Minutes | Punishment if Exceeded
|--------------|----------|--------------|--------------|
/api/v1/bot/:botid | POST | 1 | 1 Hour Block

---

###### test_example.py
```python
p = Paradise(client.user.id)
@client.command()
async def content(ctx):
  if p.has_voted(ctx.author.id):
    await ctx.send("Premium, voters-only content")
  else:
    await ctx.send("Normie content")

@client.command()
async def votes(ctx):
  await ctx.send(f"I have {p.votes} votes.")
```

---

## Posting Stats

<Route method="POST" path="/api/v1/bot/:botid" auth /> 

---

###### paradise.py
```python
import requests, json

class Paradise:
    def __init__(self, bot_id, token):
        self.bot_id = bot_id
        self.token = token

    def is_owner(self, user_id):
        try:
            if str(user_id) in self.additional_owners or user_id == self.owner:
                return True
            else:
                print(self.owner)
                return False
        except:
            raise ValueError("Invalid Bot ID.")
    
    
    def post_stats(self):
        data = {
            "server_count": len(client.guilds),
            "shard_count": client.shard_count
        }
        headers = {
            "Content-Type": "application/json",
            "Authorization": self.token
        }
        ## If you have issues set "data=data" as "body=data"
        requests.post(f"https://paradisebots.net/api/v1/bot/{self.bot_id}", data=data, headers=headers) // If you have issues set "data=data" as "body=data"
```

## Getting Stats

<Route method="GET" path="/api/v1/bots/:botid" /> 

---

###### paradise.py
```python
import requests, json

def basic_return(bot_id, q):
    r = requests.get(f"https://paradisebots.net/api/v1/bots/{bot_id}")
    try:
        return json.loads(r.content)[q]
    except:
        raise ValueError("Invalid Bot ID.")

class Paradise:
    def __init__(self, bot_id):
        self.bot_id = bot_id
        self.tags = basic_return(bot_id, "tags").split(", ")
        self.votes = basic_return(bot_id, "totalUsersVoted")
        self.users_voted = basic_return(bot_id, "usersVoted").split(", ")
        self.owner = int(basic_return(bot_id, "owner"))
        self.additional_owners = basic_return(bot_id, "additionalOwners")
        self.prefix = basic_return(bot_id, "prefix")
        self.description = basic_return(bot_id, "shortDescription")
        self.long_description = basic_return(bot_id, "longDescription")
        self.username = basic_return(bot_id, "username")
        self.website = basic_return(bot_id, "website")
        self.github = basic_return(bot_id, "github")
        self.donations = basic_return(bot_id, "donate")
        self.support_server = basic_return(bot_id, "server")
        self.bot_library = basic_return(bot_id, "library")
        self.total_servers = basic_return(bot_id, "servers")
        self.total_shards = basic_return(bot_id, "shards")

    def is_owner(self, user_id):
        try:
            if str(user_id) in self.additional_owners or user_id == self.owner:
                return True
            else:
                print(self.owner)
                return False
        except:
            raise ValueError("Invalid Bot ID.")
    
    def has_voted(self, user_id):
        if user_id in [int(x) for x in self.users_voted]:
            return True
        else:
            return False
```

---

## Full Wrapper

###### paradise.py
```python

import requests, json

def basic_return(bot_id, q):
    r = requests.get(f"https://paradisebots.net/api/v1/bots/{bot_id}")
    try:
        return json.loads(r.content)[q]
    except:
        raise ValueError("Invalid Bot ID.")

class Paradise:
    def __init__(self, bot_id, token):
        self.bot_id = bot_id
        self.token = token
        self.tags = basic_return(bot_id, "tags").split(", ")
        self.votes = basic_return(bot_id, "totalUsersVoted")
        self.users_voted = basic_return(bot_id, "usersVoted").split(", ")
        self.owner = int(basic_return(bot_id, "owner"))
        self.additional_owners = basic_return(bot_id, "additionalOwners")
        self.prefix = basic_return(bot_id, "prefix")
        self.description = basic_return(bot_id, "shortDescription")
        self.long_description = basic_return(bot_id, "longDescription")
        self.username = basic_return(bot_id, "username")
        self.website = basic_return(bot_id, "website")
        self.github = basic_return(bot_id, "github")
        self.donations = basic_return(bot_id, "donate")
        self.support_server = basic_return(bot_id, "server")
        self.bot_library = basic_return(bot_id, "library")
        self.total_servers = basic_return(bot_id, "servers")
        self.total_shards = basic_return(bot_id, "shards")

    def is_owner(self, user_id):
        try:
            if str(user_id) in self.additional_owners or user_id == self.owner:
                return True
            else:
                print(self.owner)
                return False
        except:
            raise ValueError("Invalid Bot ID.")
    
    def has_voted(self, user_id):
        if user_id in [int(x) for x in self.users_voted]:
            return True
        else:
            return False
    
    def post_stats(self):
        data = {
            "server_count": len(client.guilds),
            "shard_count": client.shard_count
        }
        headers = {
            "Content-Type": "application/json",
            "Authorization": self.token
        }
        ## If you have issues set "data=data" as "body=data"
        requests.post(f"https://paradisebots.net/api/v1/bots/{self.bot_id}", data=data, headers=headers)

```
