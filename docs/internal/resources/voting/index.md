---
title: Voting
---

## Voting Structure
| Field	| Type | Description
|--------------|----------|--------------|
user | Snowflake |	The ID of the User voting.
client | Snowflake	| The ID of the Bot being voted for.
date | Number | The date of the vote. 

---

## Voting Endpoint (Linked to Bot)

<Route method="GET" path="api/v1/bots/:botid/vote" />

---

## Voting
Paradise Bots allows users to Vote for bots, Bots with the highest number of Votes are featured on our home page and also have a chance at certification (if they meet the requirements)

* Users can vote for your bot by visiting your bots page and clicking the "Vote" button.
---

## Ratelimits
Users can currently vote every 12 hours for each bot.

---

# Voting API Rules.

Unacceptable use of our API (breaking these rules will result in appropriate punishments):

1. "Vote locking" a large percentage AND/OR majority of your bots commands AND/OR features.
2. Punishing users of your bot AND/OR community for not voting.
3. Bots should not be rewarding users for voting for another bot. E.g if a User votes for Bot A they should not be receiving Bot B's currency

---

## Acceptable use of our API:
1. Reward users of your bot for voting.
2. Try to limit voting required commands to 2-3

---

## Consequences of breaking these rules:
* First Offence - A stern warning from one of our beautiful moderators and possible reverting of bot votes.
* Second Offence - If you haven't changed your ways after your first offence, or you are caught breaking these rules a second time, we will lock your access to the voting endpoint(s) and reset your votes.
* We reserve the right to not follow these consequences in the exact order they are laid out here and take action how we see fit dependant on the scenario

---
