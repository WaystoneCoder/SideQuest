# Changelog

## 1.1
- Fix: Antwortfelder wurden durch den Auto-Logout-Aktivitätslistener bei Touch/Tastatur-Eingaben neu gerendert.
- Fix: virtuelle Tastatureingaben zählen nun als Aktivität, ohne den Screen zu ersetzen.
- Feature: persistente persönliche Countdown-Timer für zeitkritische Missionen.
- Feature: nach abgelaufenem/nicht gestartetem Timer wird beim Einlösen nachgefragt, ob die Mission innerhalb des Zeitfensters geschafft wurde.
- Feature: bei `Nein` kann ein neuer Versuch mit neuem Timer gestartet werden.
- Packaging: Manifest, Service Worker und lokale App-Icons im Party-Build enthalten.
