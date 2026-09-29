# Swiss Relief STL Generator v7.0 – Grossrelief

Autor: **Reto Speerli**

Datenquelle: **swisstopo**

Verwendete Datensätze:
- swissALTI³D – hochauflösendes Geländemodell
- swissALTIRegio – 10-m-Geländemodell für grosse Massstäbe und Grenzgebiete
- swissBUILDINGS³D – optionale Gebäude bei geeignetem Massstab

## Zweck

v7 erzeugt grosse, zusammenhängende 3D-Druck-Reliefs und teilt sie automatisch in druckbettgerechte STL-Segmente. Die Segmente werden gemeinsam geplant und verwenden denselben Höhenbezug sowie identische Höhenwerte an gemeinsamen Kanten.

Beispiel: Ein Gesamtmodell von 1200 × 800 mm bei maximal 220 mm Druckfeld wird automatisch als 6 × 4 Segmente à 200 × 200 mm ausgegeben.

## Wichtige Eigenschaften

- Gesamtbreite frei einstellbar, Seitenverhältnis aus dem gewählten Kartenausschnitt
- Druckfeld standardmässig 220 mm, frei anpassbar
- gleichmässige Segmentierung ohne schmale Restkacheln
- automatische Mesh-Auflösung, Ziel etwa 0,35 mm im Druckmodell
- automatische Wahl der sinnvollsten Höhendaten:
  - bei grossen Modellen swissALTIRegio 10 m, wenn dies bereits feiner als das Zielmesh ist
  - sonst swissALTI³D 2 m bzw. 0,5 m
- gemeinsamer globaler Höhenbezug für alle Segmente
- gemeinsame Kanten werden explizit identisch gesetzt
- jedes STL-Segment ist ein geschlossener, separat druckbarer Körper mit Boden und Seitenwänden
- ZIP-Ausgabe mit allen STL-Dateien, README.txt und layout.csv
- ZIP wird streamend aufgebaut, damit nicht alle STL-Dateien gleichzeitig im Arbeitsspeicher liegen
- bestehende robuste Fallback-Logik für fehlende Höhendaten
- Gebäude bleiben optional und werden nur bei geeignetem Massstab freigeschaltet

## Segmentbezeichnung

`R01` ist die nördlichste/oberste Reihe, `C01` die westlichste/linke Spalte.

Beispiel:

```
R01_C01  R01_C02  R01_C03
R02_C01  R02_C02  R02_C03
```

## GitHub Pages

Alle Dateien ins Root-Verzeichnis eines neuen Repositorys kopieren und GitHub Pages für `main / root` aktivieren. Es ist kein Build-Schritt nötig.
