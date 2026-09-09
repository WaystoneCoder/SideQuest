# Side Quest – Party Release 1.0

**Status:** Release Candidate für den realen Einsatz auf einem gemeinsamen Tablet  
**Arbeitstitel:** SIDE QUEST  
**Subtitle:** „Geheime Missionen. Bloß nicht auffliegen.“

## 1. Enthaltene Release-Varianten

### A. Empfohlener Event-Build: dependency-freie PWA
Ordner: `side-quest-party-build-1.0/`

Dieser Build ist für die konkrete Feier gedacht:
- eine einzige `index.html` mit kompletter Spiellogik,
- Web-App-Manifest,
- Service Worker,
- lokale Icons,
- keine externe API,
- keine externen Fonts,
- keine JavaScript-CDNs,
- kein Backend.

Der Spielstand wird lokal im Browser/PWA gespeichert und kann jederzeit als JSON-Backup exportiert werden.

### B. React/TypeScript/Dexie-Source
Ordner: `party-missions/`

Dies bleibt die strukturierte Referenzimplementierung für spätere Weiterentwicklung. Der Paketdownload konnte in der aktuellen Arbeitsumgebung wegen Registry-/Netzwerk-Timeouts nicht vollständig ausgeführt werden. Daher ist für die Feier der eigenständige PWA-Build die verifizierte Auslieferungsvariante.

---

## 2. Content Freeze 1.0

Die Bibliothek enthält weiterhin **104 Missionsvorlagen**.

Für den Party-Preset sind **90 Missionen standardmäßig aktiv**. 14 besonders situationsabhängige oder vergleichsweise konstruierte Missionen bleiben in der Bibliothek, sind aber standardmäßig deaktiviert und können im Adminbereich wieder eingeschaltet werden.

Standardmäßig optional/deaktiviert:

- `INT004` – Sitzplatz anbieten / Platz machen
- `INT013` – Ort auf der Feier zeigen oder erklären
- `INT014` – freiwilliges Kompliment auslösen
- `MAN015` – zweimal dasselbe Wort benutzen
- `MAN017` – Erinnerung an frühere Feier erzählen
- `GRP002` – Dreierdiskussion über Reiseziel
- `GRP003` – Gruppenkonsens zum Lieblingssnack
- `GRP007` – vier Personen auf dasselbe Thema lenken
- `RSK002` – „typisch für dich“ auslösen
- `RSK004` – Verhalten einer dritten Person erklären lassen
- `RSK006` – Meinung zu anderer Aktivität auslösen
- `LNG002` – dreimal dieselbe Snackempfehlung
- `LNG005` – drei Personen mit gleichem Urlaubsort
- `LNG008` – zweimal unabhängig dasselbe Spiel vorgeschlagen bekommen

Die Missionen werden nicht gelöscht. Sie können unter **Admin → Missionen verwalten** jederzeit aktiviert werden.

---

## 3. Vorbereitung auf dem Tablet

### Einmaliger Setup-Ablauf

1. Party-Build auf einen **HTTPS-fähigen statischen Host** hochladen.
2. URL auf dem Zieltablet online öffnen.
3. Die Seite einmal vollständig laden.
4. Als PWA / „Zum Home-Bildschirm“ installieren.
5. App vom Home-Bildschirm öffnen.
6. Adminbereich öffnen. Initiale PIN für einen frischen Build: `2468`.
7. Unter **Einstellungen / PIN** eine eigene PIN setzen.
8. Unter **Gästeliste** alle Gäste einfügen – idealerweise per Mehrfachimport.
9. Unter **Missionen verwalten** den 90er-Preset prüfen und bei Wunsch Missionen an-/abschalten.
10. Unter **Backup / Restore** ein erstes Backup exportieren.
11. **Pre-Party-Check** öffnen und Warnungen prüfen.

### Pflicht-Abnahmetest am echten Tablet

Nach dem Online-Setup:

1. App schließen.
2. Flugmodus einschalten bzw. WLAN/Mobilfunk deaktivieren.
3. App vom Home-Bildschirm neu öffnen.
4. Prüfen, ob Startscreen und Adminbereich funktionieren.
5. Testgast anlegen und kurz spielen.
6. Tablet vollständig neu starten.
7. Weiterhin offline bleiben.
8. App erneut öffnen.
9. Prüfen, ob der lokale Spielstand erhalten ist.
10. Danach Testspiel über Admin zurücksetzen und ein finales Backup der vorbereiteten Null-Session exportieren.

**Erst wenn diese zehn Punkte auf dem realen Zieltablet funktionieren, gilt 1.0 als für die Feier abgenommen.**

---

## 4. Empfohlene Geräteeinstellungen für die Feier

- Tablet dauerhaft oder möglichst lange am Ladegerät.
- „Nicht stören“ aktivieren.
- unnötige Benachrichtigungen deaktivieren.
- automatische Displaysperre großzügig einstellen.
- keine Browser-/Website-Daten während des Spiels löschen.
- keine Systemupdates während der Feier starten.
- PWA über das Home-Screen-Icon öffnen, nicht über zufällige Browser-Tabs.
- Hochformat als bevorzugte Ausrichtung verwenden.

---

## 5. Operativer Ablauf am Abend

### Start
- App öffnen.
- Startscreen bleibt neutral.
- Gäste wählen jeweils ihren Namen.
- Erstspieler sehen das Intro einmalig.
- Niemand muss sofort Missionen ziehen.

### Während des Spiels
- maximal drei aktive Missionen,
- Einlösen, Call und Discard erfolgen am zentralen Tablet,
- nach persönlicher Nutzung immer **Fertig**,
- Auto-Logout schützt offen gelassene Missionen,
- falsche Calls laufen über **Falscher Call?** am Startscreen.

### Sicherheitsbackup
Empfehlung:
- ein Backup vor dem offiziellen Spielstart,
- optional ein Backup während des Abends,
- auf jeden Fall ein Backup unmittelbar vor der Endabrechnung.

### Finale
- Admin → 30-Minuten-Finale starten,
- Countdown läuft persistent,
- Missionen dürfen weiterhin gezogen werden.

### Spielende
- Admin → Spiel beenden,
- offene Missionen werden automatisch mit 50 % Minus, aufgerundet, verarbeitet,
- Operation ist idempotent.

### Endabrechnung
- Endabrechnung starten,
- Snapshot wird eingefroren,
- Spieler einzeln abrechnen,
- Missions-Recaps aufdecken,
- Ranking erst zum Schluss revealen.

---

## 6. Recovery

### App wurde geschlossen
Einfach vom Home-Bildschirm erneut öffnen. Der lokale Spielstand bleibt bestehen.

### Tablet wurde gesperrt oder neu gestartet
App erneut öffnen. Der lokale Zustand soll bestehen bleiben; dies ist Teil des Pflicht-Abnahmetests.

### Falscher Klick / falsche Punkte
Admin → Ereignishistorie / Undo.

### Lokaler Spielstand beschädigt oder gelöscht
Admin → Backup / Restore → letztes JSON-Backup importieren.

### Update der App-Dateien
Spieldaten und statische App-Dateien sind getrennt. Trotzdem vor einem Update immer ein Backup exportieren.

---

## 7. Was bewusst nicht Teil von 1.0 ist

- mehrere gleichzeitig synchronisierte Geräte,
- Smartphones der Gäste,
- Cloud-Backend,
- Accounts,
- Push-Nachrichten,
- automatische Antwortprüfung,
- Foto-Uploads,
- Live-KI,
- App-Store-Veröffentlichung.

---

## 8. Release Gate

**Softwareseitig erfüllt:**
- Kernloop vollständig,
- Adminvorbereitung vollständig,
- Backup/Restore vorhanden,
- PWA-Dateien vorhanden,
- Offline-Cache strukturell validiert,
- keine externen Laufzeitressourcen,
- Logic-Smoke-Test bestanden,
- 90er Content-Preset gesetzt.

**Noch vom Nutzer auf dem Zielgerät zu erfüllen:**
- PWA installieren,
- Flugmodus-Start testen,
- vollständigen Tablet-Neustart offline testen,
- finalen Gästepool einspielen,
- finale PIN setzen,
- finales Null-Session-Backup exportieren.

**Ende – Party Release 1.0**
