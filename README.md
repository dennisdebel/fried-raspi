# Raspberry Pi Frying
code for live cooking/frying a raspberry pi board

## Hard+software
raspi a+ + latest rasbian + pixel startup script (pi:pi)

## How to
make your startup script in bash:

`$ nano myscript.sh`

insert:

```#!/bin/sh

sleep 25 # insert a few seconds pause to make sure pi has booted and doesnt kill the audio while doing so on its last cpu cycles ;)
aplay -c 2 -f S16_LE -r 44100 /dev/urandom & # play noise from cpu/random
while :; do /opt/vc/bin/vcgencmd measure_temp; sleep 1; done # display current cpu temp on loop
```

make executable:

`$ chmod +x myscript.sh`

then add it to your startup config, open/create:

`$ nano /home/pi/.config/lxsession/LXDE-pi/autostart`


(if that doesnt work, us the one below)

`$ sudo nano /etc/xdg/lxsession/LXDE-pi/autostart`


when wanting it to open in a new terminal window add above '@screensaver':

`@lxterminal -e "/home/pi/myscript.sh"`
