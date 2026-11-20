# Ergebnisgrafiken der OSMI-Clusteranalyse

Dieser Ordner enthält die aggregierten Visualisierungen der explorativen Analyse des Datensatzes *OSMI Mental Health in Tech Survey 2016*.

Die Abbildungen wurden mit dem Notebook `OSMI_Fallstudie_FINAL.ipynb` erstellt und dokumentieren die Datenaufbereitung, Clusterbildung, Methodenvergleiche und ergänzenden Auswertungen.

## Übersicht der Abbildungen

| Datei | Inhalt |
|---|---|
| `01_fehlwerte.png` | Untersuchung der fehlenden Angaben |
| `02_eda_verteilungen.png` | Explorative Verteilungen ausgewählter Merkmale |
| `03_cramers_v.png` | Zusammenhänge zwischen kategorialen Merkmalen |
| `04a_heatmap_basis.png` | Clusterprofile des Sechs-Merkmals-Modells |
| `04b_heatmap_ohne_informationen.png` | Clusterprofile des alternativen Fünf-Merkmals-Modells |
| `05_methodenvergleich.png` | Vergleich der Clustering-Verfahren |
| `06a_pca.png` | Zweidimensionale PCA-Darstellung |
| `06b_mca_personen.png` | MCA-Projektion der Befragten |
| `06c_mca_kategorien.png` | MCA-Projektion der Antwortkategorien |
| `06d_mca_inertie.png` | Inertieverteilung der MCA-Dimensionen |
| `08_unternehmensgroesse_cluster.png` | Clusterverteilung nach Unternehmensgröße |
| `09_externe_hr_alle_kategorien.png` | Antwortverteilungen der externen HR-Merkmale |

## Hinweise zur Interpretation

Die Visualisierungen dienen der explorativen Beschreibung wahrgenommener betrieblicher Unterstützungsbedingungen. Die Cluster sind keine medizinischen Diagnosen oder individuellen Risikokategorien.

Die Abbildungen zeigen aggregierte Ergebnisse. Die zugrunde liegenden individuellen Fragebogenantworten werden in diesem Repository nicht veröffentlicht.

Für den vollständigen Analyseablauf, die methodischen Einschränkungen und die Reproduktion wird auf das Notebook und die README im Hauptverzeichnis verwiesen.
