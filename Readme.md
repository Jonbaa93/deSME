# deSME - Dekarbonisieurng der Energieversorgung von KMU
Dieses Tool der Energiesystemmodellierung bietet die Möglichkeit, die Energieversorgung im Bereich Strom, Nieder- und Hochtemperaturwärme mit dem Fokus der Dekarbonisierung zu modellieren. Zur Identifizierung der kostengünstigsten Transformation der Energieversorgung für Unternehmen wird eine lineare Optimierung vorgenommen. Die Energiesystemmodellierung wird in dem Open Energy Modelling Framework (OEMOF) implementiert. Das Framework dient zur Modellierung, Darstellung und Analyse von Energiesystemen.

Eine Schematische Darstellung der Energieversorgung von KMU:
![alt text](https://github.com/Jonbaa93/deSME/blob/main/Schematische%20Darstellung.png?raw=True)

## Einrichten der Programmierumgebung
Hinweis: getestet unter Python 3.7.6

### Voraussetzungen
* Python-Installation (siehe https://www.python.org/downloads/)
* Git-Installation (siehe https://git-scm.com/downloads)
* Account bei Github (siehe https://github.com/)

### Erstellen einer virtuellen Programmierumgebung (Virtual environment)
Konsole öffnen (Windows: cmd-Fenster, Linux/macOS: Terminal) und mittels `cd`-Befehl in das gewünschte Verzeichnis navigieren, in dem die virtuelle Programmierumgebung erstellt werden soll.
Dann folgenden Befehl ausführen:
```
python3 -m venv deSME
```
Auf diese Weise wird eine neue virtuelle Programmierumgebung (Virtual environment) mit dem Namen **deSME** erzeugt.
Hinweis: Sollte der Befehl mit `python3` nicht funktionieren, alternativ `python` schreiben.

In der virtuellen Progammierumgebung werden nun im weiteren Verlauf alle Pakete installiert, welche für die Umsetzung der 100prosim Python-Applikation mit oemof-tabular und Django benötigt werden. Der Vorteil der Nutzung einer virtuellen Programmierumgebung besteht im Wesentlichen darin, dass durch die Installation der benötigten Python-Pakete das Betriebssystem und seine Komponenten nicht beeinflusst werden (z.B. Vermeidung von Versionskonflikten etc.)

#### Aktivieren der virtuellen Programmierumgebung (Virtual environment)
Mittels `cd`-Befehl in das Verzeichnis navigieren, in dem im vorherigen Schritt die virtuelle Programmierumgebung erstellt wurde. Anschließend den folgenden Befehl ausführen:

*Windows*
```
deSME\Scripts\activate.bat
```

*Linux*
```
source deSME/bin/activate
```

*macOS*
```
source deSME/bin/activate
```
Das die Aktivierung der virtuellen Programmierumgebung erfolgreich war, ist daran zu sehen, dass im cmd-Fenster bzw. im Terminal nun vor dem Dateipfad '(deSME)' steht.

#### Deaktivieren der virtuellen Programmierumgebung (Virtual environment)
Deaktivieren der virtuellen Programmierumgebung durch folgenden Befehl:
```
deactivate
```
Die Deaktivierung der virtuellen Programmierumgebung war erfolgreich, wenn im Terminal das `(deSME)` vor dem Dateipfad wieder verschwunden ist.

### Klonen der Git-Repository
Konsole öffnen (Windows: cmd-Fenster, Linux/macOS: Terminal) und mittels `cd`-Befehl in das gewünschte Verzeichnis navigieren, in dem die lokale Kopie der 100prosim Git-Repository abgelegt werden soll.
Dann folgenden Befehl ausführen:
```
git clone https://github.com/Jonbaa93/deSME
```
Auf der lokalen Festplatte wird nun im gewünschten Zeichnis ein neuer Ordner mit der Bezeichnung **deSME** erstellt.
Für nähere Informationen zur Verwendung von Git siehe: https://docs.github.com/en

### Installation benötigter Pakete
(Hinweis: Diese Schritte werden in der virtuellen Programmierumgebung (Virtual environment) ausgeführt. Diese muss also zunächst wie zuvor beschrieben aktiviert werden)

Für die Installation der benötigten Pakete mittels `cd`-Befehl in das Verzeichnis `/deSME/` navigieren. Hier nun den folgenden Befehl ausführen:
```
pip install -r requirements.txt
```
Die Installation der benötigten Pakete wird nun automatisch ausgeführt.

### Installation Solver
Damit das Paket oemof-solph für die Berechnung bzw. Optimierung verwendet werden kann, muss ein Solver installiert werden. Hier wird zunächst der Cbc-Solver verwendet. Für Informationen zur Installation siehe: https://github.com/coin-or/Cbc. Alternativ können andere Solver verwendet werden.

## Durchführung eines Dekarbonisierungs-Szenarios

Die Datei **deSME.ipynb** wird als Jupyter-Notebook ausgeführt. Diese enthält die Modellierung auf der Basis von oemof-solph nach dem Aufbau der **Schematischen Darstellung.png**. Die definierten Klassen innerhalb der Modellierung ist mit Bezügen zu Eingangsdaten und -Paramtern der Datei **data.xlsx** versehen. Die Daten können innerhalb der Datei verändert werden. Eine Verschiebung des Zellenaufbaus darf nicht durchgeführt werden. Alle Ein- und Ausgabedaten sind in kW bzw. kWh definiert. Eingelesene Lastgänge sowie die Energiesystemmodellierung werden in stündlicher Auflösung durchgeführt. Die Investitionskosten innerhalb des Modells werden annualisiert in €/kW bzw. €/kWh angegeben.

## Erläuterungen zu den Basisdaten

Das Modell berechnet im Basisszenario eine dekarbonisierte Energieversorgung für das Jahr 2030 auf Basis von Prognosedaten der Agora-Energiewende (https://www.agora-energiewende.de/veroeffentlichungen/klimaneutrales-deutschland-2045-datenanhang/). Die Berechnung findet für ein Jahr in stündlicher Auflösung statt. 

