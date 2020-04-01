---
layout: default
title: "TNTippingBot"
---
## TNTippingBot

**Description**: TNTippingBot tipping service for the Turtle Network Platform, on Telegram.

**Summary**: @TNTippingBot on the Telegram mobile/web application.

**Data Sheet**: @TNTippingBot Data Sheet.

**Credits**: *@Hawky & @Black_Turtle in Telegram.*

### Standard Functions

* Tip a user with any Turtle Network asset within a Telegram group.
* Telegram username required (create in Telegram Settings section)
* Turtle Network wallet and address automatically created

### Operational Security (OpSEC)

* ***Telegram app***: ‘Who can See my Phone number’ setting **change to ‘Nobody’** in ‘Settings, ‘Privacy & Security’ then ‘Phone Number’.
* ***Changing Telegram username***: A tip wallet is linked to a Telegram username, so be aware if username is changed, you could loose access to your tip wallet, so move funds to a new wallet prior and/or import an empty key. ***Also note*** that someone else could potentially ‘grab’ the old username and have access to the original wallet, so move funds to a new wallet prior & don’t import the same private key into multiple Telegram usernames.
* ***Note***: *Be Safe, it’s a tipping wallet, backup private keys, don’t store large amount of funds, keep private key, phone number & username safe.*

### Setup

* Telegram group admin inserts @TNTippingBot into the group
* Telegram group admin gives the bot admin rights to delete messages only, then the bot will clean messages posted

### Available Commands

* /tntip – tip user <*user*> <*amount*> <*token*>
* /tntrade – buy or sell <*amount*> <*token*>
* /tntiptop – tip top10 <*amount/user*> <*token*>
* /tntips – show help
* /tnaddress – view address
* /tnbal – view current balance
* /tnwithdraw – withdraw <*address*> <*amount*> <*token*>
* /tntop – view top10 tippers
* /tnprivatekey – request private key
* /tnimportprivatekey – import private key <*private key*>

[@TNTippingBot](https://t.me/TNTippingBot) Type the ‘/tntips‘ to show the below commands;
* /tntip@TNTippingBot – tipping a user in the format <*user*> <*amount*> <*token*>
* /tntrade@TNTippingBot – trade at market prices in the format <*buy or sell*> <*amount*> <*token*>
* /tntiptop@TNTippingBot – tipping the top 10 in the format <*amount/user*> <*token*>
* /tntips@TNTippingBot – showing this help message
* /tnaddress@TNTippingBot – showing the address for the user who requests it
* /tnbal@TNTippingBot – showing the current balance of the requesting user
* /tnwithdraw@TNTippingBot – withdraw funds in the format <*address*> <*amount*> <*token*>
* /tntop@TNTippingBot – shows most tipping person on Telegram
* /tnprivatekey@TNTippingBot – request the private key to your tipping wallet in a private chat
* /tnimportprivatekey@TNTippingBot – import a private key for your tipping wallet in the format <*private key*> PLEASE SAVE YOUR FORMER PRIVATE KEY IN ORDER FOR BEING ABLE TO RESTORE IT
**Note**: Please have in mind to not store large amounts of funds due to potential security flaws!
**Note**: Keys are stored somewhere. Remember this is only for tipping! This is not a full wallet.

### Fees
Total: 0.05TN p/tip
* fees to TN 0.01TN
* fees to network to process the fee payment: 0.02TN
* fees to network to process tip: 0.02TN

### New Functions
Nov 2018: ‘tntrade’ command added for instant market trades.<br>
Jan 2020: Bot moved to new infrastructure and Push Messages created for ‘Tip Tuesday’

### Hidden functions
Nov 2018: /tntiptop50@TNTippingBot – tipping the top 50 in the format <*amount/user*> <*token*>
