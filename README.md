# Funded.

Landingpage für einen unabhängigen Service, der zeigt, wer eine Weiterbildung oder ein Studium in der Schweiz mitbezahlt (Bund, Kanton, Branchenfonds, Arbeitgeber, Steuern). Eine HTML-Datei, kein Build nötig.

Lokal starten:

```bash
python3 -m http.server 4323
```

Dann <http://localhost:4323> öffnen.

## Identity «Alpine Dawn»
- Fjord `#0F2B33`, Seeglas `#8CC4BD`, Aprikose `#F0A073`, Papier `#F5F2EC`
- Schrift: Instrument Sans (überall, ein Schnitt-Set)
- Logo: Variante C (Symbol aus drei Formen), Rohdateien aller drei Entwürfe in `brand/`

## Aufbau
Hero mit Alpen-Schichten und Plan-Vorschau → Scroll-Story (Globus zoomt in die Schweiz, die Quellen fliessen zu «Du») → 6 Schmerzpunkte → Zahlen mit Quellen → interaktiver Check → Zeitleiste «Wann kommt was?» → Preise → Klare Grenzen → FAQ → Warteliste.

## Performance
- Eine einzige `requestAnimationFrame`-Schleife, Schreibzugriffe nur als `transform`/`opacity`
- Jede Berg-Schicht ist eine eigene Compositor-Ebene, Parallax mit Glättung
- Globus: eigene Orthografie-Projektion für die Landmassen (ca. 0,3 ms statt ca. 6 ms mit d3), Pill-Sprites gecacht, kein `shadowBlur` pro Frame
- Canvas-Auflösung passt sich der echten Frame-Zeit an (starke Geräte behalten die volle Schärfe)
- `will-change` nur kurz vor und während einer Animation, danach wieder freigegeben
- Orb-Animation pausiert beim Scrollen und ausserhalb des Bildschirms

## Offen vor dem Schalten von Ads
- Name «Funded» ist nicht auf Marken geprüft (Swissreg, Klassen 9, 36, 41, 42)
- Warteliste speichert nur lokal im Browser (`TODO` im Skript)
- Impressum, Datenschutz, Bedingungen sind Platzhalter
- Zahlen im Abschnitt «Warum das lohnt» stammen aus SBFI, BASS 2025 und temptraining 2024, vor Veröffentlichung nochmals gegen die Quellen prüfen
- Beispielrechnungen sind fiktiv und als solche beschriftet
- Preise sind Testannahmen
- Keine Kundenstimmen eingebaut, weil es noch keine echten gibt
- Die Schweizer Umrisse sind von Hand gesetzt und stilisiert, nicht amtlich genau
