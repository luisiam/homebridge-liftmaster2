# homebridge-liftmaster2
LiftMaster Plugin for [HomeBridge](https://github.com/nfarina/homebridge) (API 2.0)

Older version that uses API 1.0: [homebridge-liftmaster](https://github.com/nfarina/homebridge-liftmaster)

# Installation
1. Install homebridge using `npm install -g homebridge`.
2. Install this plugin using `npm install -g git+https://github.com/luisiam/homebridge-liftmaster2.git`.
3. Update your configuration file. See configuration sample below.

# Configuration
Each HomeBridge installation has only one `config.json` and it is used to configure both the HomeBridge and all the plugins.  Edit your homebridge's `config.json` accordingly. 

The section of json that needs to be added to `config.json` to configure the 'homebridge-liftmaster2' follows:
 ```
"platforms": [{
    "platform": "LiftMaster2",
    "username": "email@email.com",
    "password": "password"
}]
```

The following sample HomeBridge 'config.json' file, is for a setup that includes only the `homebridge-liftmaster2` plugin.  (If your setup only needs the `homebridge-liftmaster2` plugin, you can use this example as is.  Remember to change the username and password lines to match your https://www.myliftmaster.com/ MyQ login credentials!)

```
{
    "bridge": {
        "name": "Homebridge",
        "username": "CC:22:3D:E3:CE:30",
        "port": 51826,
        "pin": "031-45-154"
    },
    
    "description": "My config file description (put anything you would like in here!)", 

    "platforms": [{
         "platform": "LiftMaster2",
         "username": "email@email.com",
         "password": "password"
    }]
}
```

### Advanced Configuration (Optional)
This step is not required. HomeBridge with API 2.0 can handle configurations in the HomeKit app.
```
"platforms": [{
    "platform": "LiftMaster2",
    "username": "email@email.com",
    "password": "password",
    "longPoll": 300,
    "shortPoll": 5,
    "shortPollDuration": 120
}]
```

| Fields            | Description                                                   | Required |
|-------------------|---------------------------------------------------------------|----------|
| platform          | Must always be `LiftMaster2`.                                 | Yes      |
| username          | Your MyQ account email.                                       | Yes      |
| password          | Your MyQ account password.                                    | Yes      |
| longPoll          | Normal polling interval in `s` (Default 300s).                | No       |
| shortPoll         | Polling interval in `s` when door state changes (Default 5s). | No       |
| shortPollDuration | Duration in `s` to use `shortPoll` (Default 120s).            | No       |


###The default location of the HomeBridge config.json file

The HomeBridge 'config.json' is located by default in a .homebridge directory off of the user's home directory.  The following shows the default location of the file, for the default user, on a Raspberry Pi:
```
pi@raspberrypi:~/.homebridge $ cd ~/.homebridge
pi@raspberrypi:~/.homebridge $ pwd
/home/pi/.homebridge
pi@raspberrypi:~/.homebridge $ ls /home/pi/.homebridge/config.json
/home/pi/.homebridge/config.json
pi@raspberrypi:~/.homebridge $ 
```
