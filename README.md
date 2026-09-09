# Side Quest – Party Build 1.1

Hotfix + Timer-Update.

## Behoben
- Antwortfelder bei Informations-/Long-Term-Missionen lassen sich nun auf Touch-Geräten normal beschreiben.
- Ursache war ein globaler Aktivitätslistener, der bei jedem Tastendruck/Touch den Screen neu gerendert hat.
- Eingabeaktivität setzt den Auto-Logout weiterhin zurück, ohne die UI neu aufzubauen.

## Neu: persönliche Missionstimer
Für zeitkritische Missionen erscheint im Missionsdetail ein eigener Timer.
Aktuell aktiviert für:
- `man018`: 5 Minuten
- `grp001`: 5 Minuten
- `grp007`: 10 Minuten

Ablauf:
1. Spieler öffnet die Mission.
2. `Timer starten` drücken, wenn der Versuch beginnt.
3. Countdown läuft nur für dieses Assignment und bleibt nach `Fertig`/Logout persistent.
4. Wird innerhalb der Zeit `Mission einlösen` gedrückt, geht es direkt weiter.
5. Bei späterer Einlösung fragt die App, ob die Mission innerhalb der vorgegebenen Zeit geschafft wurde.
6. Bei `Nein` bleibt die Mission aktiv und der Timer kann für einen neuen Versuch erneut gestartet werden.

## Upload
Für GitHub Pages den **Inhalt dieses Ordners** hochladen, sodass `index.html`, `sw.js` und `manifest.webmanifest` direkt im Repository-Root liegen.
