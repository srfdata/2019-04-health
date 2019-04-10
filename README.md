# 2019-04-health

## Vorbemerkungen
Dieses Dokument beschreibt die Vorprozessierung und explorative Analyse des Datensatzes, der Grundlage des auf srf.ch veröffentlichten Artikels [Wie gesund ist die Schweiz](http://www.srf.ch/data) ist.

SRF Data legt Wert darauf, dass die Datenvorprozessierung und -Analyse nachvollzogen und überprüft werden kann. SRF Data glaubt an das Prinzip offener Daten, aber auch offener und nachvollziehbarer Methoden. Zum anderen soll es Dritten ermöglicht werden, auf dieser Vorarbeit aufzubauen und damit weitere Auswertungen oder Applikationen zu generieren.

Die Endprodukte des vorliegenden Scripts, neben der explorativen Analyse, sind (Datenbeschreibung siehe unten):

* `health_survey_2017.csv`: Datensatz Gesundheitsbefragung reduziert auf 17 Kategorien als CSV
* `health_survey_2017.json`: Datensatz Gesundheitsbefragung reduziert auf 11 Kategorien als JSON
### R-Script & Daten

Die Vorprozessierung und Analyse wurde im Statistikprogramm R vorgenommen. Das zugrunde liegende Script sowie die prozessierten Daten können unter [diesem Link](https://srfdata.github.io/2019-04-health/rscript.zip) heruntergeladen werden. Durch Ausführen von `main.Rmd` kann der hier beschriebene Prozess nachvollzogen und der für den Artikel verwendete Datensatz generiert werden. Dabei werden Daten aus dem Ordner `input` eingelesen und Ergebnisse in den Ordner `output` geschrieben. 

SRF Data verwendet das [rddj-template](https://github.com/grssnbchr/rddj-template) von Timo Grossenbacher als Grundlage für seine R-Scripts. Entstehen bei der Ausführung dieses Scripts Probleme, kann es helfen, die Anleitung von [rddj-template](https://github.com/grssnbchr/rddj-template) zu studieren.

### GitHub

Der Code für die vorliegende Datenprozessierung ist auf [https://github.com/srfdata/2019-04-health](https://github.com/srfdata/2019-04-health) zur freien Verwendung verfügbar. 

### Lizenz

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons Lizenzvertrag" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" href="http://purl.org/dc/dcmitype/Dataset" property="dct:title" rel="dct:type">2019-04-health</span> von <a xmlns:cc="http://creativecommons.org/ns#" href="https://github.com/srfdata/2019-04-health" property="cc:attributionName" rel="cc:attributionURL">SRF Data</a> ist lizenziert unter einer <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Namensnennung - Weitergabe unter gleichen Bedingungen 4.0 International Lizenz</a>.

### Weitere Projekte

Code & Daten von [SRF Data](http://srf.ch/data) sind unter [http://srfdata.github.io](http://srfdata.github.io) verfügbar.

### Haftungsausschluss

Die veröffentlichten Informationen sind sorgfältig zusammengestellt, erheben aber keinen Anspruch auf Aktualität, Vollständigkeit oder Richtigkeit. Es wird keine Haftung übernommen für Schäden, die  durch die Verwendung dieses Scripts oder der daraus gezogenen Informationen entstehen. Dies gilt ebenfalls für Inhalte Dritter, die über dieses Angebot zugänglich sind.

### Datenbeschreibung 

#### `health_survey_2017.json`, `health_survey_2017.csv`

| Attribut | Typ | Beschreibung |
|-------|------|-----------------------------------------------------------------------------|
| group | String | Einteilung nach Geschlecht: Männer, Frauen |
| subgroup | String  | Einteilung nach Altersgruppe |
| category | String | Kategoriebezeichnung in Englisch des ausgewählten Gesundheitsthemas |
| year  | String | Erhebungsjahr der Gesundheitsbefragung |
| key  | String | Antwortmöglichkeit, unterschiedlich je nach Thema |
| value  | Numeric | Entsprechender Wert für key |

### Originalquelle

#### Standardtabellen Gesundheitsbefragung 2017

&rarr; `input/tabellen_2017`

Die Daten stammen aus der [Schweizerischen Gesundheitsbefragung](https://www.bfs.admin.ch/bfs/de/home/statistiken/gesundheit/erhebungen/sgb.html), die alle fünf Jahre seit 1992 durchgeführt wird. Die sechste Erhebung fand im Jahr 2017 statt und wurde Ende Februar 2019 publiziert. Für das vorliegende Projekt wurden die Standardtabellen 2017 verwendet. Insgesamt hat das BfS 86 Tabellen veröffentlicht. Es handelt sich dabei um Excel-Dateien, die auf den jeweiligen Sheets die Daten der vergangenen Erhebungen enthalten. Die Tabellen können beim [Bundesamt für Statistik (BfS)](https://www.bfs.admin.ch/bfs/de/home/statistiken/kataloge-datenbanken/tabellen.html?dyn_prodima=900210) heruntergeladen werden können.

Jede Tabelle enthält die Daten für ein Gesundheitsthema (zum Beispiel: Wie häufig trinken Sie normalerweise alkoholische Getränke?). Die Antwortmöglichkeiten (key) unterscheiden sich je nach Thema. In den Tabellen sind die Daten nach Sprachregion, Bildungshintergrund, Geschlecht und Alter unterschieden.

#### Glossar 2017

&rarr; `input/gesundheitsbefragung_glossar_2017.csv`

Mit Hilfe des Glossar werden die Tabellen ausgewählt, die in diesem Skript analysiert wurden. Im Glossar sind der Dateiname der Tabelle, die englische Kategoriebezeichnung und die unterschiedlichen Antwortmöglichkeiten enthalten.