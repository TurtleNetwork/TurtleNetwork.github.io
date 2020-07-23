Account Balance:

An account balance is the amount of the token that is stored on the account.

One account can store different tokens in different amounts. For example, an account can have 50 TN and 200 DOGE at the same time. The amount of the Y token on the account is called the account balance in Y token. If there is no Y token on the account, it is said that the account balance in Y token is equal to zero.



Account balance types in TurtleNetwork:

These are the four balance types:

    regular
    available
    effective
    generating

In addition to TN that belongs to the account owner, the account may store TN that belong to other accounts — those are leased TN.

The regular balance is the amount of TN on the account belonging directly to the account owner.

To explain the available and effective balances, we will introduce the following designations:

R — regular balance,

Lo — the amount of TN which account leased to other accounts,

Li— the amount of TN which were leased to the account by other accounts.

The available balance is:

R - Lo

The effective balance is:

R - Lo + Li

The generating balance is the minimum value of the effective balance during the last 1000 blocks.



You can view your account balance in wallet.turtlenetwork.eu or in the TurtleShell browser extension.
or
explorer.turtlenetwork.eu


Retrieving account balance using Node API:

You can get account balance in TN by using the Node API request.

Example of the request:

curl https://nodeIPaddres/addresses/balance/details/<account address>

Example of the response:

{
  "address": "3JMCn1EHq4WrsfUazezyYu23H1gHKvuffER",
  "regular": 6086358429,
  "generating": 5086358429,
  "available": 5086358429,
  "effective": 5086358429
}
