# OSMI Mental Health in Tech Survey 2016 – Clusteranalyse

Begleitender Python-Code zur IU-Fallstudie im Modul **Unsupervised Learning und Feature Engineering**. Untersucht werden explorativ **wahrgenommene betriebliche Unterstützungsbedingungen für psychische Gesundheit**. Es werden weder medizinische Diagnosen noch individuelle Risikoprognosen erstellt.

## Projektinhalte

- Explorative Datenanalyse und Fehlwertprüfung der 63 ursprünglichen Fragebogenmerkmale
- Datenbereinigung und Feature Engineering, einschließlich Rollen-Multi-Hot-Encoding
- K-Means-Clustering auf sechs betrieblichen Merkmalen und alternative Fünf-Merkmals-Segmentierung
- Vergleich mit k-Modes (Huang-/Cao-Initialisierung), Sensitivitäts- und Teilstichprobenanalysen
- Visualisierung mit PCA, MCA und Cluster-Heatmaps sowie Prüfung externer Kontextvariablen

## Repository-Struktur

- `OSMI_Fallstudie_FINAL.ipynb` – ausführbarer Analysecode mit gespeicherten Ergebnisausgaben
- `requirements.txt` – Python-Abhängigkeiten; das Notebook verwendet `kmodes==0.12.2`
- `results/` – ausgewählte **aggregierte** Diagramme und Ergebnistabellen
- `results/README.md` – ergänzende Erläuterungen zu den exportierten Ergebnissen

### Ausgewählte Ergebnisdateien

Die folgenden aggregierten CSV-Dateien befinden sich im Verzeichnis results/ und ermöglichen die direkte Überprüfung zentraler Ergebnisse der Fallstudie:

| Datei | Inhalt |
| --- | --- |
| `clusterprofil_6_merkmale.csv` | Antwortanteile und Abweichungen für die Hauptsegmentierung |
| `clusteranteile_je_unternehmensgroesse.csv` | Clusteranteile **innerhalb** der Unternehmensgrößenklassen |
| `externe_tests.csv` | Chi-Quadrat-Kennzahlen, numerische p-Werte, korrigiertes Cramér's V und Prüfung erwarteter Zellhäufigkeiten |
| `arbeitsland_3_gruppen_prozent.csv` | Anteile der zusammengefassten Ländergruppen USA / UK / andere Länder je Cluster |

Die CSVs enthalten aggregierte Ergebnisse, **keine einzelnen Befragtenzeilen**.

## Datenquelle und Lizenz

- Originaldaten: **Open Sourcing Mental Illness (OSMI), Mental Health in Tech Survey 2016**
- Kaggle: https://www.kaggle.com/datasets/osmi/mental-health-in-tech-2016
- OSMI: https://www.osmihelp.org/research.html
- Lizenzhinweis zu den Originaldaten: **Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)**, siehe https://creativecommons.org/licenses/by-sa/4.0/

Die Originaldaten sind **nicht Bestandteil dieses Repositories**. Es werden keine IU-Aufgabenblätter oder individuellen Fragebogenantworten veröffentlicht. Die Lizenzangabe bezieht sich auf den Quelldatensatz und ist **keine automatische Freigabe des eigenen Codes**. Für diesen Code wird hier keine zusätzliche Lizenz erklärt.

## Ausführung in Google Colab

1. Die Original-ZIP des Datensatzes von Kaggle herunterladen. Sie enthält die Datei `mental-heath-in-tech-2016_20161114.csv` (Schreibweise wie in der Quelle).
2. `OSMI_Fallstudie_FINAL.ipynb` in Google Colab öffnen.
3. Über **Laufzeit → Alle ausführen** die Analyse starten. Das Notebook installiert bei Bedarf `kmodes==0.12.2` und fordert die ZIP-Datei zum Upload an, wenn sie nicht bereits verfügbar ist.
4. Nach Abschluss werden die Diagramme und aggregierten Ergebnistabellen im Verzeichnis /content/results/ gespeichert. Ausgewählte Ergebnisdateien sind zusätzlich im Repository unter results/ verfügbar.
5. Für die Reproduzierbarkeit nur aggregierte Ausgaben veröffentlichen; keine Rohdaten, Upload-Artefakte oder individuellen Beobachtungen in das Repository übernehmen.

Außerhalb von Colab können die Abhängigkeiten mit `python -m pip install -r requirements.txt` installiert werden. Die Eingabedaten sind dann entsprechend dem Notebook bereitzustellen; einzelne Colab-Uploadfunktionen setzen eine Colab-Laufzeit voraus.

**Hinweis zu `externe_tests.csv`:** Der CSV-Export im finalen Notebook erfolgt vor dem Hinzufügen der formatierten Anzeigespalte `p_formatiert`. Die Datei enthält die **numerischen** p-Werte (`p_Wert`); die formatierten Angaben erscheinen zusätzlich in der Notebook-Ausgabe. Die Länderauswertung wird wegen kleiner erwarteter Zellhäufigkeiten in den ursprünglichen Einzelkategorien separat für die Gruppen USA / UK / andere Länder geprüft.

## Zentrale Ergebnisse

- **1.146 abhängig Beschäftigte** aus ursprünglich 1.433 Befragungseinträgen
- K-Means mit sechs Merkmalen (`k=3`): Clustergrößen **308 / 340 / 498**, euklidische Silhouette **0,15485**
- Alternativmodell ohne Informationsfrage: Clustergrößen **357 / 487 / 302**, Silhouette **0,17688**; Übereinstimmung mit dem Hauptmodell **ARI 0,06799**
- Starker Zusammenhang zwischen Hauptcluster und Informationsfrage: korrigiertes Cramér's V **0,8967**, ARI **0,8185**
- k-Modes (Huang) erreicht unter der kategorialen Kostenfunktion **2.492**, die K-Means-Partition **2.606** Abweichungskosten
- Medianer Subsampling-ARI: K-Means ca. **0,989**, k-Modes (Huang) ca. **0,381**
- Stärkster untersuchter externer Zusammenhang: Unternehmensgröße mit korrigiertem Cramér's V ca. **0,241**

**Interpretation:** Die Cluster erfassen Antwortmuster und Unterstützungswahrnehmungen, keine stabilen psychologischen Mitarbeitendentypen. Die freiwillige Befragung ist nicht nachweislich repräsentativ. Die geringe Trennschärfe, die Dominanz einer Informationsfrage und mögliche gemeinsame Arbeitgeber schränken die Übertragbarkeit ein. Es dürfen keine individuellen Personalentscheidungen daraus abgeleitet werden.

## Versionierung und Nachvollziehbarkeit

Die technischen Analyseschritte, Modellalternativen und Sensitivitätsanalysen sind im Notebook dokumentiert. Die zusätzlich hochgeladenen aggregierten CSVs ermöglichen eine Prüfung ausgewählter Kennzahlen ohne erneuten Durchlauf des gesamten Notebooks.
