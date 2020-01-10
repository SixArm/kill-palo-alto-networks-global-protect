# Launch script for the Palo Alto GlobalProtect macOS VPN client

The GlobalProtect VPN client from Palo Alto runs continually in the background. This can cause problems for some users because it keeps trying to connect, popping up dialog boxes, with no way to quit.

   * The UI does not have any kind of "Quit" button or menu item.

   * The macOS Activity Monitor can use "Quit" or "Force Quit", and the command line process tools can use `kill` or `pkill`, but the software restarts when it's loaded into launchctl.

   * The software is able to run simultaneously on multiple user accounts on the same Mac; this is an atypical setup for a solo user, but a typical setup for our teammates, who may have a user account for normal work, and a separate user account for demos.

The kill function uses `launchctl` to unload the code, then kills all processes named GlobalProtect and PanGPS.
 
The start function uses `launchctl` to reload all GlobalProtect with all its dependencies.

## Installing

Simply download the raw file and save it to a convenient location
on your hard drive.

## Launching the Script

Simply execute `gplaunch` from the command line with the appropriate parameters.

```
Usage: gplaunch [-k] [-s]

    -k|--kill           unloads and kills all related GlobalProtect processes
    -s|--start          loads all dependent processes for GlobalProtect connections
```

## Authors

* **Joel Parker Henderson** - *Initial work* - [SixArm software] (https://github.com/SixArm)
* **Danny Aponte** - *Contributor* - [Intelligent Product Solutions] (https://github.com/ips-yes)
