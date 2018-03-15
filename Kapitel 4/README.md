# Kapitel 4 - CODE

1. Lege einen neuen Ordner an: `mkdir dooralarm && cd dooralarm`
1. Öffne einen Texteditor auf der Kommandozeile (z.B. `vim` oder `nano`) und füge das folgende Script ein:

```python
#!/usr/bin/env python

import time # sodass wir "sleep" zum warten benutzen können
import RPi.GPIO as io # importieren die GPIO library die wir installiert haben, aber nenne sie "io"

## setze GPIO mode auf BCM
## der Befehl nimmt GPIO number anstatt pin number
io.setmode(io.BCM)
 
## wir haben GPIO 23 genommen. Falls du einen anderen pin genommen hast, entsprechend anpassen.
door_pin = 23
 
## nutze den eingebauten pull-up resistor
io.setup(door_pin, io.IN, pull_up_down=io.PUD_UP)  # aktiviere input mit PullUp
 
## initialisiere die door-Variable
door=0
 
## dieser loop führt das if-Statement aus
while True:
    ## if switch is open
    if io.input(door_pin):
        door=0 # set door auf initial value
        # do something
        print("Door open")
        time.sleep(1) # wait 1 second vor der nächsten Aktion
    ## if switch is closed und door does not equal 1
    if (io.input(door_pin)==False and door!=1):
        # do something
        print("Door closed")
        door=1 # set door so that this loop won't act again until the switch has been opened
```

1. mache zum Abschluss das Script direkt ausführbar:
```
chmod +x gpio_script.py
```