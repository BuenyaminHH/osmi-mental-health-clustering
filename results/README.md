# OSMI Mental Health in Tech Survey 2016 – Clusteranalyse

Begleitender Python-Code zur IU-Fallstudie im Modul **Unsupervised Learning und Feature Engineering**. Ziel ist die explorative Untersuchung **wahrgenommener betrieblicher Unterstützungsbedingungen für psychische Gesundheit**. Es werden keine medizinischen Diagnosen oder individuellen Risikoprognosen erstellt.

## Projektinhalte

- Exploration und Fehlwertanalyse der 63 ursprünglichen Fragebogenmerkmale
- Datenbereinigung und Feature Engineering, darunter Rollen-Multi-Hot-Encoding
- K-Means-Clustering auf sechs betrieblichen Merkmalen und alternative Segmentierung ohne die Informationsfrage
- Vergleich mit k-Modes (Huang/Cao), Clusterzahlwahl, Sensitivitäts- und Stabilitätsanalysen
- Dimensionsreduktion mit PCA und MCA, Cluster-Heatmaps und externe Kontextvergleiche

**Dateien:** `OSMI_Fallstudie_FINAL.ipynb` enthält den Code mit den in Colab gespeicherten Ausgaben. `results/` enthält ausgewählte, aus **genau diesem Notebook** exportierte aggregierte Abbildungen. `requirements.txt` dokumentiert die Python-Abhängigkeiten. Zusätzliche aggregierte CSV-Tabellen werden beim Ausführen im Ordner `results/` erzeugt.

## Datenquelle und Lizenz

- Originaldaten: **Open Sourcing Mental Health (OSMI), Mental Health in Tech Survey 2016**.
- Kaggle: https://www.kaggle.com/datasets/osmi/mental-health-in-tech-2016
- Primärquelle: https://www.osmihelp.org/research.html
- Lizenz der **2016er Daten** laut OSMI: **Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)**; siehe https://creativecommons.org/licenses/by-sa/4.0/ . Diese Lizenzangabe bezieht sich auf die Datenquelle und ist **keine automatische Lizenzfreigabe des eigenen Codes**.

Die Originaldaten sind nicht Bestandteil dieses Repositories. Es werden keine IU-Aufgabenblätter oder individuellen Fragebogenantworten veröffentlicht.

## Notebook in Google Colab ausführen

1. Die Original-ZIP über Kaggle herunterladen. Sie enthält `mental-heath-in-tech-2016_20161114.csv` (Schreibweise wie in der Quelle).
2. `OSMI_Fallstudie_FINAL.ipynb` in [Google Colab](https://colab.research.google.com/) öffnen.
3. **Laufzeit → Alle ausführen** wählen. Die erste Codezelle installiert `kmodes==0.12.2`. Das Notebook lädt die ZIP-Datei auf Nachfrage hoch, sofern diese noch nicht im Colab-Dateisystem liegt. Den Namen `archive (1).zip` trägt das ursprüngliche Arbeitsarchiv; die Upload-Funktion akzeptiert auch andere ZIP-Dateinamen, solange genau die erwartete CSV darin liegt.
4. Die Zellen bis einschließlich Abschnitt 8 ausführen und die gespeicherten Ergebnisdiagramme sowie die in `/content/results/` neu erzeugten CSV-Dateien prüfen.
5. Für einen neuen öffentlichen Stand das ausgeführte Notebook erneut als `.ipynb` herunterladen; dabei sicherstellen, dass keine individuellen Datensätze oder vertraulichen Uploadinformationen in den Ausgaben stehen.

Außerhalb von Colab können die Abhängigkeiten mit `python -m pip install -r requirements.txt` installiert werden; die ZIP ist dann in das Arbeitsverzeichnis neben das Notebook zu legen. Die Colab-Uploadfunktion benötigt die Colab-Laufzeit.

## Zentrale Ergebnisse der ausgeführten Analyse

- **1.146 abhängig Beschäftigte** aus 1.433 Fragebogeneinträgen.
- K-Means (sechs Merkmale, `k = 3`): Clustergrößen **308 / 340 / 498**; euklidische Silhouette **0,15485**.
- Ohne die Informationsfrage: Clustergrößen **357 / 487 / 302**, Silhouette **0,17688**; ARI zwischen den Lösungen **0,06799**.
- Clusterzuordnung und Informationsfrage: korrigiertes Cramér's V **0,8967**, ARI **0,8185**. Die Informationsfrage prägt die Hauptlösung stark.
- k-Modes (Huang) erreicht kategoriale Abweichungskosten **2.492**; die K-Means-Partition erreicht unter **derselben k-Modes-Kostenfunktion** **2.606**. Die Verfahren sind nicht anhand einer einzelnen Kennzahl insgesamt zu bewerten.
- Medianer Subsampling-ARI: K-Means etwa **0,989**, k-Modes (Huang) etwa **0,381**.
- Stärkster untersuchter externer Zusammenhang: Unternehmensgröße mit der Clusterzuordnung (korrigiertes Cramér's V etwa **0,241**). Die zusammengefassten Ländergruppen wurden bei einer minimalen erwarteten Zellzahl von **35,75** getestet.

Die Ergebnisse beschreiben Antwortmuster und betriebliche Wahrnehmungen, **keine stabilen psychologischen Mitarbeitendentypen**. Die Stichprobe ist nicht nachweislich repräsentativ für alle Technologieunternehmen. Mögliche gemeinsame Arbeitgeber, die dominierende Informationsfrage und die geringe Trennschärfe begrenzen die Generalisierbarkeit. Die Cluster dürfen nicht zur individuellen Personalbewertung verwendet werden.

## Datenschutz und Reproduzierbarkeit

Der Ordner `results/` enthält **nur aggregierte Abbildungen**, keine Rohdatensätze, keine Zeilen aus dem ursprünglichen Survey und keine identifizierenden Angaben. Tabellen und Abbildungen werden beim Ausführen des Notebooks reproduzierbar in `results/` gespeichert. Die im Notebook enthaltenen Ausgaben wurden auf gespeicherte Fehlermeldungen und offensichtliche Geheimnisse geprüft; sie ersetzen keine unabhängige Bewertung der Eignung der Quelle für öffentliche Weitergabe.
