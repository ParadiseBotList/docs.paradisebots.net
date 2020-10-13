---
title: Paradise Python Library
---

This is our official Python Library for Paradise Bots, if you have any issues please submit an issue on our github or join our discord
* [Github Link](https://github.com/ParadiseBotList)
* [Discord Link](https://discord.gg/Cqy99Pt)

---
To start using server counts on a bot, 
* Go to your bot edit page, 
* Click the Authorization Token link at the bottom of the page. This will generate an auth token.

---

## Example
Example with Automatic Server Count
```Python
url = "https://paradisebots.net/api/v1/bot/:botid" # Replace :botid with your bot ID

payload = "{\"server_count\": 1500}" # Replace this number with the server count
headers = {
  'authorization': 'YOUR_AUTH_TOKEN',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)
print(response.text.encode('utf8'))

```

---

## User-Made API

There is a user-made API for Python as well. The gist (with an example) is found here: https://gist.github.com/Aryamaan08/6833f31218b00f7792dc900728b0db01

---

## User-Made API Example

Copy the code in the gist and save it as `paradise.py`.
```
from paradise import Paradise
@client.command()
async def votecount(ctx):
  b = Paradise(client.user.id)
  await ctx.send(f"I have `{b.votes}` votes. Vote for me at https://paradisebots.net/bots/{client.user.id} now!")
```
