# Masterarbeit Vorherhersage von Abflüssen ausgewählter Pegel in Baden-Württemberg
### Überblick
In diesem Repository befinden sich 16 Jupyter Notebooks zur Datenvorbereitung, Datenauswahl, Modellierung und Evaluation zur Vorhersage von Abflüssen ausgewählter Pegel in Baden-Württemberg mithilfe von Methoden des maschinellen Lernens (XGBoost, Random Forest).

Die jeweiligen Skripte bauen aufeinander auf und folgen dabei der Methodik, die in der Arbeit beschrieben wurde.

### Ordnerstruktur
Da die Skripte in Jupyter Notebooks vorzufinden sind, sind die verwendeten Dateien nicht in diesem Repository enthalten. Der Übersichtlichkeit wegen soll die grobe Ordnerstruktur dennoch kurz erklärt werden:
```text
Masterarbeit/
|
|--.ipynb_checkpoints/
|-- Datensätze/
|    |--DWD/
|    |   |--Baden-Württemberg-Messnetze und Parameternetze-stündlich/
|    |   |--Enhanced-Baden-Württemberg-Messnetze und Parameternetze-stündlich/
|    |   |--Filtered-Enhanced-Ba-Wü-Messnetze und Parameternetze-stündlich/
|    |   |__Messnetze und Parametermessnetze-stündlich/
|    |   
|    |
|    |--UDO-LUBW/
|        |--Auswahl Landespegel Hydrologie/
|        |--Endgültige Auswahl Landespegel Hydrologie/
|        |__Landespegel Hydrologie/
|
|--Evaluation/
|--Plot/
|   |--Evaluation/
|   |__Forecasts/
|
|--Koordinaten der Gewässerstationen.csv
|--Koordinaten der Niederschlagsstationen.csv
|--Matched coordinates.csv
|--Stammdaten_Endgültige_Auswahl_der_Gewässerstationen.csv
|__...
```
### Beschreibung der Jupyter Notebooks

#### Datenaufbereitung und Datenauswahl
1. **Waters.ipynb**:
In diesem Notebook werden die Abflusszeitreihen für die spätere Vorhersage aufbereitet und vorbereitet sowie nach Kriterien wie maximale zusammenhängende Lücken aussortiert und nach gleichmäßiger räumlicher Verteilung ausgewählt.
2. **Waters Interpolation.ipynb**:
Hier werden die fehlenden Werte der ausgewählten Abflusszeitreihen interpoliert. 
3. **DWD_precipitation.ipynb**:
In diesem Skript werden die Niederschlagsstationen für die spätere verwendung aufbereitet und vorbereitet.
4. **DWD_gap_handling.ipynb**:
In diesem Skript werden verschiedene Verfahren zum Umgang mit fehlenden Daten in den Niederschlagszeitreihen angewandt.
5. **matching_coordinates.ipynb**: Hier werden den jeweiligen Abflussstationen die Niederschlagsstationen zugeordnet, die maximal 20 km von den Abflussstationen entfernt sind. Die zugeordneten Niederschlagszeitreihen dienen schließlich als exogene Variablen für die spätere Vorhersage.
#### Explorative Datenanalyse
6. **explorative data analysis.ipynb**: In diesem Skript werden die Abflusszeitreihen analysiert und die Korrelation zwischen den Abflusszeitreihen und den zugeordeten Niederschlagszeitreihen berechnet.

#### Anwendung der Methoden
##### XGBoost
- Die folgenden Skripte führen jeweils nahezu das gleiche durch: Hier werden die Hyperparameter-Optimierungen sowie die finalen Vorhersagen mit jeweils einer Lead Time von einer, sechs, 24 und 72 Stunden durchgeführt (horizon wird in diesem Code als Synonym für Lead Time verwendet).
7. **XGBoost_modelling_single_horizon_1h.ipynb**
8. **XGBoost_modelling_single_horizon_6h.ipynb**
9. **XGBoost_modelling_single_horizon_24h.ipynb**
10. **XGBoost_modelling_single_horizon_72h.ipynb**

##### Random Forest
- Analog zum Unterkapitel XGBoost wird in den folgenden Dateien ebenfalls nahezu das gleiche durchgeführt: Hyperparameter-Optimierung und finale Vorhersagen mit jeweils einer Lead Time von einer, sechs, 24 und 72 Stunden.
11. **RandomForest_modelling_single_horizon_1h.ipynb**
12. **RandomForest_modelling_single_horizon_6h.ipynb**
13. **RandomForest_modelling_single_horizon_24h.ipynb**
14. **RandomForest_modelling_single_horizon_72h.ipynb**

#### Evaluation
- Die folgenden Skripte evaluieren die finalen Vorhersagen der jeweiligen Verfahren (XGBoost, Random Forest) über alle gewählten Lead Times hinweg.
15. **XGBoost_Evaluation_Forecast.ipynb**
16. **RandomForest_Evaluation_Forecast.ipynb**
