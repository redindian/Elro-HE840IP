# DISCLAIMER
This is a work in progress. Currently switches and dimmers are supported including settings percentages. The Elro HE840IP does not support getting status of devices. A future release will include saving dimmer settings and switch status to a file. These settings may not be correct if normal remotes are being used also.

# homebridge-home-easy
HomeEasy plugin for homebridge: https://github.com/nfarina/homebridge

This plugin communicates with the Elro HomeEasy Home automation gateway HE840IP:
http://www.elro.eu/en/products/cat/home-automation/home-easy-next/transmitters2/home-automation-gateway

Based on the LightwaveRF plugin for HomeBridge:
https://github.com/rooi/homebridge-home-easy

# Installation

1. Install homebridge using: npm install -g homebridge
2. Install this plugin using: npm install -g homebridge-home-easy
3. Update your configuration file. See the sample below.
4. Start homebridge

# Configuration

You can use the ip_address, username and password to configure the plugin automatically using:

 ```
"platforms": [
        {
          "platform": "HomeEasy",
          "name": "HomeEasy",
          "ip_address": "192.168.1.123",
          "username": "admin",
          "password": "111111"
        }   
    ]

```

If you want you can specify the devices yourself using the following syntax:

 ```
"platforms": [
        {
            "platform" : "HomeEasy",
            "name" : "HomeEasy",
            "ip_address": "192.168.1.123",
            "username": "admin",
            "password": "111111",
            "devices": [
                {
                    "roomid": 1,
                    "roomname": "LivingRoom",
                    "devid": 1,
                    "devname": "MyLight",
                    "devtype": "dimmer"
                },
                {
                    "roomid": 1,
                    "roomname": "LivingRoom",
                    "devid": 2,
                    "devname": "MyLight",
                    "devtype": "switch"
                }
            ]
        }
]
```

The following devices are supported:
- Dimmable Light: "devtype": "dimmer"
- Switch: "devtype": "switch"

# How to Determine Room Number:

Log in to HE840IP
View All Rooms
Select the room in question
Show Page Source
Search in Page Source for "All Off" -The Required value is in the data-room_number= attribute of that line

# How to Determine Device Number:

Log in to HE840IP
View All Rooms
Select the room in question
Device Number is usually the order in which the devices are listed, but this does not account for adding and removing devices. This may take some trial and error.
