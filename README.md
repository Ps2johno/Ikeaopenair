.__ __                        .__        
|__|  | __ ____ _____  _____  |__|______ 
|  |  |/ // __ \\__  \ \__  \ |  \_  __ \
|  |    <\  ___/ / __ \_/ __ \|  ||  | \/
|__|__|_ \\___  >____  (____  /__||__|   
        \/    \/     \/     \/           v1 
Guide how to connect it to tasmota


THINGS YOU NEED 
soldering iron - a basic soldering iron 
good solder and flux
wires
ESP board or module
! Important! 
Make sure to flash Tasmota to the module before soldering 


SOLDERING
Unplug the two connectors from the PCB and remove from the enclosure so its easier to solder
The PCB has all the pads labelled. You will use the top row, ones labelled: 5V, GND and REST
Some tips for easier soldering: Pre-tin the pads and wires before soldering. Use plenty of flux, don't be stingy with it. Avoid overheating by not leaving the soldering iron on the pads for too long.
To solder the three wires, ensure the soldering iron is set to 350°C. Briefly touch the iron to the pad and wire until the solder melts. Be sure the wires are long enough to reach the ESP module and are securely attached with no shorts.
Connect the wires as follows:

REST to any safe free pin, I used GPIO5 aka D1. This is the pin used to receive data from the air quality sensor.
5V to the Vin of the voltage regulator or 5V pin on the D1 mini
GND to GND
I made a hole on the other side to seamlessly fit the new wires and make installation easy.
Tasmota Configuration
To have support for Vindriktning’s sensor you need at least Tasmota version 9.5.0.7. Since it is not included in standard builds, you need to enable the sensor by adding it to user_config_override.h: #define USE_VINDRIKTNING    // Add support for IKEA VINDRIKTNING particle concentration sensor (+1k code)¸

Or, download an unofficial build tasmota-allsensors which supports almost all sensors, Vindriktning included.
Once the firmware is installed on the ESP module go to Configuration - Configure Module and set the pin you connected the REST wire to as VINDRIKTNING. In my case it was GPIO5.

After a reset, if everything went according to plan you will see the values in the webUI
