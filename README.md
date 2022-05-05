# deckFanControl
Bash script to control the Steam Deck Fan speed

## IMPORTANT 
**The script was developed for personal use, and is provided AS IS, I take no responsability on any problem on your hardware caused by the usage of the script.**

**Controll your deck temperatures and adjust the RPM to avoid overheating**

## Description

This script reads every 2 seconds the "edge" temp of the steam deck CPU and adjust the FAN RPM acording to the values on the speeds file

 On exit, the script will set the fan to auto again, if the exit is due to:
  
  A) Receiving a sigterm or sigint.
  
  B) A file named stop is created on the script folder

**If the script is killed or suffers an error, the fan speed will remain as the last speed set even after rebooting the SteamDeck, never set you lowest temp too high**

**If this happens, to activate the auto fan profile, relaunch and close properly the script, or launch as root the command:**

**echo 0 > /sys/class/hwmon/hwmon5/recalculate**



### Script configuration

The speeds file must be on the same directory as the script, the format is:
<Temp with 2 digits><Space><RPM>
  
  The fan curve can be changed modifying the values on the speeds file.
  
  The default values are lower than the stock steam deck fan speeds, so expect high temps if you stress the Deck with the script on
  
  |Temperature| RPM|
  ---|---|
|40 |2000|
|45 |3000|
|50 |3500|
|55 |4000|
|60 |4500|
|65 |5000|
|70 |6000|
  
If the speed is lower than the first Temp set on the speeds file, the fan will STOP
  
 ### Execution
  
  This script needs ROOT access. So you must set a root password.
  
  This script can be launched from steam, creating a shortcut.
  
  The shortcut must be for the Aplication Konsole, this will allow to launch the script and enter your root password on "console" mode
  In the shortcut properties, set the values as follows
  
  |Property |Value | 
  --- | --- | 
  |Target|Konsole|
  |Start In|"directory where you installed the script"|
  |launch options|--fullscreen -e sudo ./deckFanControl|
  
  To allow the script to run without a password, edit the sudoers file and add:
  
  deck ALL=(ALL:ALL) NOPASSWD:/home/deck/deckFanControl/deckFancontrol
  
  Adapting the path to your installation
  
  Once Lauched, set the controller schema to "Web browser" to be able to use the mouse and the keyboard.
  
  To exit gracefully using the Konsole shortcut, close the Konsole window (File->close Window)


