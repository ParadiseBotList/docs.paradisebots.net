---
title: Webhooks
---

Instead of requesting our API to see the users who have voted for your bot, we now have webhooks! Webhooks will send a post request to a URL of your choice when your bot has been voted for.

---

## Getting Started
Start by setting up your webhook URL in the edit form of your bot on this site, it can be found at `https://paradisebots.net/bots/:BOTID/edit` once you have entered the URL you want the webhook to be sent to, you're all set! If you need help setting up webhooks inside of your bot don't be afraid to ask in our discord servers `#api-support` channel.

---

## Data Format

<Route method="POST" path="/api/v1/bot/:botid/vote" /> 

The format of the data your webhook URL will receive in a POST request

###### JSON Params
Field | Type | Description
|--------|--------|--------|
avatar | String | The avatar of the bot that received a vote.
bot | String | Username of the bot that received a vote.
user | String | Username of the user who voted.
userID | Snowflake | ID of the user who voted.
vote_count | Number | The updated vote count for the bot.
