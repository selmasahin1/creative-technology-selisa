# Creative Technology Projekt von Lisa & Selma


## Projektidee
Das Projekt „Audio Responsive Partikel“ visualisiert Sound in Echtzeit innerhalb eines Igloos. Ziel ist es, akustische Signale – konkret Lautstärke und Frequenzen – in eine immersive, visuelle Erfahrung zu übersetzen.
Über ein Mikrofon wird Audio aufgenommen und in TouchDesigner analysiert. Die Lautstärke beeinflusst die Anzahl der Partikel, während verschiedene Frequenzbereiche die Farbe der Partikel steuern.

Durch die Ausgabe im Igloo, das aus mehreren Projektoren besteht, entsteht eine räumliche 360°-Visualisierung, bei der sich Sound nicht nur hören, sondern auch sehen und räumlich erleben lässt.

## Setup und Komponentenplan

Hardware:

MacBook Pro (TouchDesigner 2023.20480)
Microphone (USB 3.0)
Igloo mit 5 Projektoren

Software:

TouchDesigner


![Komponetenplan drawio](https://github.com/user-attachments/assets/30c13584-9108-4d27-b07b-8f92d0eb318c)


## Technische Umsetzung
### Audioeingang

Als Audioquelle dient ein externes USB-Mikrofon, das per USB 3.0 mit dem Computer verbunden ist.
In TouchDesigner wird das Mikrofon über einen Audio Device In CHOP ausgewählt. Wichtig ist, dass der richtige Audioeingang im Node manuell eingestellt wird.

### Lautstärkeanalyse

Die Lautstärke des Audiosignals wird mithilfe eines Analyze CHOPs ausgewertet.
Der Analyze CHOP berechnet einen Pegelwert (Amplitude), der anschliessend über einen Math CHOP skaliert wird, um für weitere Parameter nutzbar zu sein.

Dieser Wert steuert indirekt die Anzahl der Partikel im Particle GPU. Dafür wird ein Noise CHOP verwendet, dessen Seed-Wert mit der Lautstärke verbunden ist. Je lauter der Sound, desto stärker verändert sich der Seed, wodurch mehr Partikel entstehen und die Bewegung intensiver wird.

### Frequenzanalyse und Farbsteuerung

Für die Frequenzanalyse wird ein Audio Analysis CHOP eingesetzt.
Die relevanten Frequenzbereiche werden über einen Select CHOP ausgewählt und anschliessend mit einem Audio Band CHOP in drei Bereiche aufgeteilt:

Tiefe Frequenzen → Violett

Mittlere Frequenzen → Pink

Hohe Frequenzen → Rosa

Diese drei Werte werden auf die Farbparameter der Partikel gemappt, sodass sich die Farbe der Partikel dynamisch an den dominanten Frequenzbereich des Sounds anpasst.

### Ausgabe ins Igloo

Das finale Bild wird über einen Syphon/Spout Out TOP ausgegeben und auf einen separaten Laptop übertragen, der für das Igloo-Setup zuständig ist.
Das Igloo besteht aus fünf Projektoren, die gemeinsam eine 360°-Projektion darstellen.

Die notwendige Auflösung beträgt 8000 × 1000 Pixel, da diese exakt auf das Mapping des Igloos abgestimmt ist. Diese Auflösung muss in TouchDesigner sowie im Mapping-Setup korrekt eingestellt sein.

## Reproduzierbarkeit
Damit das Projekt reproduzierbar ist, werden folgende Schritte benötigt:

### Voraussetzungen

- TouchDesigner Version: 2023.20480

- Computer: Betriebssystem egal

- Mikrofon: Beliebiges Mikrofon (USB empfohlen)

- Ausgabesystem: Syphon/Spout-fähiger Rechner oder Igloo-System

### Schritt-für-Schritt-Anleitung

1. TouchDesigner installieren (Version 2023.20480).

2. Mikrofon mit dem Computer verbinden.

3. Projektdatei öffnen.

4. Im Audio Device In CHOP den korrekten Audioeingang auswählen.

5. Syphon/Spout aktivieren und sicherstellen, dass das Signal am Igloo-Rechner ankommt.

6. Lautstärke testen und gegebenenfalls die Math-CHOP-Werte anpassen.

Nach diesen Schritten reagiert das System in Echtzeit auf Audioinput.

## Reflexion
Die Zusammenarbeit im Zweierteam hat sehr gut funktioniert. Die Lernkurve war zu Beginn sehr steil, da wir beide am Anfang noch wenig Überblick über TouchDesigner hatten und uns teilweise verloren fühlten.

Nach etwa drei bis vier Arbeitssessions wurde das Verständnis deutlich besser, und wir konnten effizienter arbeiten sowie Aufgaben sinnvoll aufteilen. Besonders schwierig war die Trennung der Frequenzbereiche, da viele Tutorials auf ältere TouchDesigner-Versionen ausgelegt sind und sich Nodes oder Workflows verändert haben.

Wir haben verschiedene Tutorials ausprobiert, zusätzlich KI zur Unterstützung genutzt und schliesslich viel durch Ausprobieren und Experimentieren gelernt. Am Ende entstand eine funktionierende Mischung aus theoretischem Wissen und praktischer Erfahrung.

Das Endresultat hat uns sehr viel Spass gemacht, und wir haben uns stark darüber gefreut, dass das System zuverlässig funktioniert hat. Der gesamte Prozess war den Aufwand definitiv wert, da wir sehr viel dazulernen konnten.
Für zukünftige Projekte müssen wir nicht mehr bei null anfangen und können direkt mit dem Aufbau der Nodes beginnen. Zudem wissen wir jetzt, wie hilfreich gute Online-Tutorials sein können.

## Video
### Show-Reel
[Showreel](https://www.youtube.com/watch?v=45PMc1FJAyE)

### Erklärvideo
[Erklärvideo](https://www.youtube.com/watch?v=waS0NOouueM)
