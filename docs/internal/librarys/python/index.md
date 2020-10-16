---
title: Paradise Python Library
---

This is our official User Made Python Library for Paradise Bots, if you have any issues please submit an issue on our github or join our discord

* [Github Link](https://gist.github.com/Aryamaan08/6833f31218b00f7792dc900728b0db01)
* [Discord Link](https://paradisebots.net/join)

---

## Wrapper Example

Copy the code below and save it as `paradise.py`.

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
        self.id = bot_id
        self.tags = basic_return(bot_id, "tags").split(", ")
        self.votes = basic_return(bot_id, "votes")
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
```

## Fetching Stats Example

```python
from paradise import Paradise
@client.command()
async def votecount(ctx):
  b = Paradise(client.user.id)
  await ctx.send(f"I have `{b.votes}` votes. Vote for me at https://paradisebots.net/bots/{client.user.id} now!")
```

