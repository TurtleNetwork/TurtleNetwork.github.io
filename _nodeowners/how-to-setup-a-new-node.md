---
layout: default
title: "How to setup a new node"
---
# How to setup a new TN full node

**Document Approvals**<br>
Document Owner: _@Black_Turtle on Telegram_ <br>
Document Creator/Editor: _@thenerd386 on Telegram_ <br>

**Table of Contents**

[1. Introduction](#introduction)

[2. Hosting](#hosting)

[3. Turtle Network Node Setup -- Step 1](#turtle-network-node-setup-step-1)

[4. Turtle Network Node Setup -- Step 2](#turtle-network-node-setup-step-2)

[5. Turtle Network Node Upgrade](#turtle-network-node-upgrade)

[6. Other Useful Information](#other-useful-information)

[7. Video tutorial](#video)

## Introduction

The following tutorial will show the full steps in setting-up a Linux Full Node on the Turtle Network.

**Note:** Knowledge about using SSH is required. All access to the VPS server is securely done via port 22 (SSH).

## Hosting

- A Virtual Private Server (VPS) server is required with the following minimum specifications:

  Details                                   | Minimum               | Recommended           |
  ----------------------------------------- | ----------------------| --------------------- |
  **Operating System:**                     | Ubuntu 16.04 or 18.04 | Ubuntu 20.04 or 22.04 |
  **Hosting type**                          | VPS                   | VPS                   |
  \- CPU                                    | 1 CPU vCores          | 2 CPU vCores (or more)|
  \- Memory                                 | 3 GB Memory           | 4 GB Memory (or more) |
  \- Storage                                | 50GB (SSD preferred)  | 100 GB (SSD preferred)|
  **Configuration:**                        | Static IP Required    | Static IP Required    |
  **Access:**                               | Root Access Required  | Root Access Required  |
  **TurtleNetwork (TN) required for a node**| 1,000 TN              | 1,000 TN              |

- Fully patch the Operating System (OS): Login as 'root' and execute the following commands:
    - `sudo apt update` \# Fetches the list of available updates
    - `sudo apt upgrade` \# Strictly upgrades the current packages
    - Reboot

- Create a local App user with sudo rights (more secure than using root):
    -   Issue the following command: `sudo adduser *username*` (replace \*username\* with the preferred username) and it will prompt to set a password.
    -   Add the new username into the sudo group with the following command:
        `sudo usermod -aG sudo *username*` (replace \*username\* with the chosen username).
    -   Log out as root.

- Add this new user to SSHD config 
    -   Open /etc/ssh/sshd_config in your editor
    -   Add this to the bottom of the file `AllowUsers *username*` (replace \*username\* with what you chose above)
    -   For extra security you can also change the line `PermitRootLogin yes` to `PermitRootLogin no` 
    -   Save the file and exit
    -   Type `sudo systemctl restart sshd` or `sudo service sshd restart`
    -   Now you can log in to the server with your new user 

## Turtle Network Node Setup -- Step 1

**Note:** All terminal sessions and commands from this step, will be done with the chosen 'username' from the 'Hosting section'.

1.   Install the JDK/JRE 11 (64-bit version) with the following commands:
```
sudo apt install openjdk-11-jre
sudo apt install openjdk-11-jdk
```
**Note:** Oracle JDK/JRE 11 with 64-bit version is required.

2.  Check the installation with the following command:
    -   `java -version`, the output should show information similar to what is shown below:

    > openjdk version "11.0.20" 2023-07-18
    > OpenJDK Runtime Environment (build 11.0.20+8-post-Ubuntu-1ubuntu122.04)
    > OpenJDK 64-Bit Server VM (build 11.0.20+8-post-Ubuntu-1ubuntu122.04, mixed mode, sharing)

**Note:** The version might differ.

## Turtle Network Node Setup -- Step 2

**Note:** All terminal sessions and commands from this step, will be done with the chosen 'username' from the 'Hosting section'.

**Github:**
<https://github.com/TurtleNetwork/TurtleNetwork/releases>

***Note: If you want to run a Testnet node make sure to download the files named with tn-testnet***

1.  Download the current .deb package (check the latest release in the above link): `wget https://github.com/TurtleNetwork/TurtleNetwork/releases/download/v1.3.16/tn_1.3.16_all.deb` (replace `/v1.3.16/` with the latest version, replace `tn_1.3.16_all.deb` with the latest .deb version).

2.  Install the downloaded .deb file: `dpkg -i tn_1.3.16_all.deb` (replace `tn_1.3.16_all.deb` with the latest .deb version).

3.  Create a wallet on the Turtle Network:

    -   <https://wallet.turtlenetwork.eu> then 'Sign in' or 'Get Started' and create a new account.
    -   **Important**: Save your SEED & password securely and never loose.
    -   Login to your wallet and record the following:
        -   Wallet Address
        -   Wallet Password
        -   In Wallet, navigate to the 'Backup' item in the top-right section, click, then record your 'ENCODED SEED' which will be used later.
        -   Log out of wallet

4.  Open <https://cluster.tnnode.turtlenetwork.eu> and access Swagger to do the following:
    -   Encrypt your API key, do the following:
        -   Click on 'Utils' then \"/utils/hash/secure\"
        -   Insert your own 'custom api key' in the 'Value' section then click 'Try it Out'  
        -   Record your 'custom api key' and the 'hash' value which was generated by the previous  command

5.  Edit the TN.conf file in /usr/share/tn/:
    -   `vi /usr/share/tn/conf/tn.conf` (or `nano /usr/share/tn/conf/tn.conf`)
    -   Change the following defaults:
        -   \# Network settings section:
            -   remove the '\#' then change: node-name = \"My MAINNET node\" \--\> change to your custom node name
            -   remove the '\#' then change: declared-address = \"1.2.3.4:6868\" \--\> change to 'yourstaticip:6860
            - if you experience issues connecting, you can specify know peers in this section \--\> known-peers = ["peer:port", "peer:port", "peer:port"]
        -   \# Wallet settings section:
            -   change: password = \"ridetheTN!\" to your wallet password set in section 4.
            -   remove the '\#' then change seed = \"\" to your ENCODED SEED noted in section 4.
        -   \# Node\'s REST API settings section:
            -   enable = no \--\> change to 'yes'
            -   bind-address = \"127.0.0.1\" \--\> change to 0.0.0.0
            -   port = 6859
            -   api-key-hash = \"H6nsiifwYKYEx6YzYD7woP1XCn72RVvx6tC1zjjLXqsu\" \--\> replace with your own hash key noted in previous section.
    
6.  Start the TN node: `sudo service tn start` or `sudo systemctl start tn`

7.  Watch the TN node log live (press ctrl+c to cancel): `sudo journalctl -u tn.service -f` & let it download the blockchain.

8.  Browse to <https://explorer.turtlenetwork.eu/peers> & confirm your node is listed.

9. Implement a Firewall using iptables (extra security):
    -   Insert the below data into an executable file called TN_firewall for ease-of-use, basic
        configuration below:
    -   Create file: `sudo touch TN_firewall`
    -   Execute using: `sudo ./TN_firewall`

```
#!/bin/sh
######################################
echo "*** Turtle Network Firewall ***"
######################################
#
###################
# Setting variables
###################
#
# Checking for iptables
#######################
IPTABLES=/sbin/iptables
#######################
#
echo "Checking for IPTABLES"

if ! [ -x $IPTABLES ] : then
        echo
        echo "ERROR IN CONFIGURATION: IPTABLES doesn't exist or isn't executable!"
        exit 1
fi
#
#####################
echo "FLUSHING RULES"
#####################
$IPTABLES -P INPUT ACCEPT
$IPTABLES -P FORWARD ACCEPT
$IPTABLES -P OUTPUT ACCEPT

#######################
echo "INPUT CHAIN... "
#######################
$IPTABLES -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
$IPTABLES -A INPUT -m state --state NEW -m tcp -p tcp --dport 53 -j ACCEPT
$IPTABLES -A INPUT -m state --state NEW -m udp -p udp --dport 53 -j ACCEPT
$IPTABLES -A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
$IPTABLES -A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
$IPTABLES -A INPUT -p tcp -m tcp --dport 443 -j ACCEPT
$IPTABLES -A INPUT -p tcp -m tcp --dport 6860 -j ACCEPT
$IPTABLES -A INPUT -i lo -j ACCEPT
$IPTABLES -A INPUT -j DROP

###############################################
echo "*** Turtle Network Firewall Complete ***"
###############################################
```


**Note:** Port 80 uses a proxy to forward to port 6859 (unless you have Apache already installed where then you will need to specify :6859 after the url / ip)

# Turtle Network Node Upgrade

**Note:** All terminal sessions and commands from this step, will be done with the chosen 'username' from the 'Hosting section'.

1. Backup your current tn.conf: `sudo cp /usr/share/tn/conf/tn.conf /usr/share/tn/conf/tn.conf.backup` 

2. Stop the TN node: `sudo service tn stop` or `sudo systemctl stop tn`

3. Get the updated files (Latest releases: <https://github.com/TurtleNetwork/TurtleNetwork/releases>)

    -   `wget https://github.com/TurtleNetwork/TurtleNetwork/releases/download/v1.3.16/tn_1.3.16_all.deb` (replace \*.deb with the latest .deb version)

4. Install the downloaded .deb file: `dpkg -i tn_1.3.16_all.deb` (replace \*.deb with the latest .deb version)

5. Start the TN node: `sudo service tn start` or `sudo systemctl start tn`

  <p>If you need to resync the entire blockchain: </p>

  - Remove TN data folder: `rm -rdf /var/lib/tn/data`

# Other Useful Information
- Review the node log: `sudo journalctl -u tn.service -f`
- Turtle Node Reporting: <http://statistics.turtlenetwork.eu/nodes>
- peers.dat is located at /var/lib/tn/peers.dat
- wallet.dat is located at /var/lib/tn/wallet/wallet.dat  

## Community

Get answers to your questions in the Turtle Network [group](https://t.me/turtlenetwork) in Telegram.

# Video
[Tutorial on node setup](https://www.youtube.com/watch?v=G8ICWvelEys&feature=youtu.be&a=)
