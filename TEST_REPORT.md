# Side Quest – Test Report 1.0

## Automatisierte / technische Prüfungen

### JavaScript-Syntax
- kompletter Standalone-Spielcode mit `node --check` geprüft: **PASS**
- Service Worker mit `node --check` geprüft: **PASS**

### React/TypeScript-Source
- alle `.ts` / `.tsx`-Dateien über TypeScript `transpileModule` syntaktisch geprüft: **0 Syntaxfehler**
- vollständiger npm/Vite-Build in dieser Umgebung nicht möglich: `npm install` läuft aufgrund Registry-/Netzwerkzugriff ins Timeout

### PWA-Struktur
Geprüft:
- `index.html`: vorhanden
- `manifest.webmanifest`: gültiges JSON
- `sw.js`: syntaktisch gültig
- 192×192 Icon: vorhanden
- 512×512 Icon: vorhanden
- `display: standalone`
- `start_url: ./`
- alle im Precache referenzierten Assets vorhanden
- keine externen HTTP-/HTTPS-Laufzeitressourcen in `index.html`

Ergebnis: **PASS**

### HTTP-Asset-Test
Über lokalen statischen HTTP-Server geprüft:
- `/` → 200
- `/index.html` → 200
- `/manifest.webmanifest` → 200
- `/sw.js` → 200
- `/icons/icon-192.png` → 200
- `/icons/icon-512.png` → 200

Ergebnis: **PASS**

## Logic Smoke Test – echter Party-Build-Code

Der tatsächliche Inline-Spielcode des Party-Builds wurde in einer isolierten JavaScript-VM ausgeführt.

Geprüft:
1. frischer Produktionsbuild startet ohne Demo-Gäste
2. Standard-Preset = 90 aktive Missionen
3. 14 Missionen standardmäßig optional/deaktiviert
4. Mehrfachimport von 8 Gästen
5. Admin-PIN ändern
6. Pre-Party-Check erkennt individuelle PIN
7. Missionsziehen liefert maximal 3 Optionen
8. nur aktive Missionsvorlagen werden gezogen
9. Spieler kann nie sein eigenes Target sein
10. Mission kann übernommen werden
11. erfüllte Mission schreibt korrekte Punkte
12. erfüllte Mission wird `safe`
13. erfolgreicher Call zieht vollen Missionswert ab
14. Discard zieht 50 %, aufgerundet, ab
15. offene Mission am Spielende zieht 50 %, aufgerundet, ab
16. mehrfaches Spielende erzeugt keine doppelte Strafe
17. Settlement-Snapshot wird erzeugt
18. Snapshot bleibt gegen spätere Punkteänderungen stabil
19. Backup besitzt gültige Envelope-Daten
20. Backup setzt `lastBackupAt`

Testergebnis:

```json
{"pass":true,"activeMissions":90,"optionalMissions":14,"guests":8,"finalAnna":-8}
```

**Ergebnis: PASS**

## Browser-/Device-Test

Ein Chromium-Browser ist in der Arbeitsumgebung vorhanden, jedoch blockiert die Umgebung Navigation zu `localhost`, Container-IP und `file://` per Administrator-Policy (`ERR_BLOCKED_BY_ADMINISTRATOR`). Daher konnte kein glaubwürdiger vollständiger Browser-Service-Worker-Test auf einem echten virtuellen Origin durchgeführt werden.

Dies wird nicht als bestanden ausgegeben.

### Noch notwendig auf dem Zieltablet
- HTTPS-URL online öffnen
- PWA installieren
- Flugmodus aktivieren
- PWA erneut starten
- Tablet offline neu starten
- PWA erneut starten
- Datenpersistenz kontrollieren

Siehe `08_PARTY_RELEASE.md`.
