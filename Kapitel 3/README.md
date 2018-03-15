# Kapitel 3 - Software Setup

Im folgenden wollen wir die Grundfunktionen der Software einrichten. Auch das ist nicht kompliziert:

1. Sicherstellen, dass die Software-Liste des Raspberry Pi aktuell ist
```
sudo apt-get update
```

1. Installieren eines Development-Kits, das wir für GPIO benötigen
```
sudo apt-get install python-dev
```

1. Installieren der GPIO-Bibliothek
```
sudo apt-get install python-rpi.gpio
```