Der Vergleich: Wie ein Sicherheitsbeamter vor der Tür
Stellen Sie sich den Cloudflare-Worker wie einen Sicherheitsbeamten vor der Tür Ihres Streamings vor. Er lässt die Videodaten von Mega.nz zu Ihnen durch, verbirgt aber Ihre echte IP-Adresse.

Hier ist der Unterschied, wie die beiden Beamten arbeiten:

1. Die Standard-Variante (worker.js)
Das Verhalten: Dieser Beamte ist extrem stur und streng. Er lässt nur Daten durch, die haargenau von der Adresse .userstorage.mega.co.nz kommen. Wenn automatisierte Internet-Bots anklopfen, um den Worker auszuspionieren, wirft er sie aggressiv hinaus und schreibt einen lauten Fehlerbericht (HTTP 400 / 403 / 405).
Vorteil: Extrem minimalistisch.
Nachteile:
Volle Fehlerprotokolle: Ihr Cloudflare-Dashboard ist voll von roten Fehlermeldungen (ca. 77 % Fehlerrate) wegen des täglichen "Hintergrundrauschens" durch Internet-Bots.
Stream-Abbrüche: Wenn Mega.nz einen Server verwendet, der auf .mega.nz (ohne .co) oder auf g.api endet, blockiert der Worker diesen legitimen Stream. Ihr Video bricht ab.
2. Die erweiterte Variante (extended_domain_worker.js) — Empfohlen 🌟
Das Verhalten: Dieser Beamte ist genauso sicher, arbeitet aber wesentlich intelligenter und flexibler:
Die Bot-Täuschung (Sauberes Dashboard): Wenn Bots anklopfen und nach nicht existierenden Pfaden suchen, zeigt der Worker ihnen einfach die normale Statusseite (Status 200 OK), statt sie mit einer Fehlermeldung abzuweisen. Für Sie bedeutet das: Keine künstlichen 4xx-Fehlerraten mehr im Cloudflare-Dashboard – Ihre Statistik bleibt blitzsauber.
Erweiterter Durchlass (Keine Abbrüche): Er kennt alle Server-Varianten von Mega.nz (sowohl .co.nz als auch .nz für Speicher- und API-Server). Der Stream läuft unterbrechungsfrei durch.
Browser-freundlich (CORS): Er beantwortet Anfragen von Webbrowsern (CORS-Preflight), was die Nutzung zukunftssicher macht (z. B. wenn Sie MegaStreamer später in einer Plex-Webseite nutzen möchten).
Vorteil: Wesentlich stabilere Streams und saubere, aussagekräftige Cloudflare-Statistiken.
Zusammenfassung der Unterschiede für den Vergleich:
Eigenschaft	Standard (worker.js)	Erweitert (extended_domain_worker.js)
Zuverlässigkeit der Streams	⚠️ Mittel (Abbrüche bei bestimmten Mega-Servern)	Sehr hoch (erlaubt alle Mega-Server-Varianten)
Fehlerrate in Cloudflare	❌ Hoch (ca. 77 %, da Bots 400er-Fehler auslösen)	Gegen 0 % (Bots werden stumm gefiltert)
Browser-Kompatibilität	❌ Nein (blockiert Browser-Standardanfragen)	Ja (unterstützt CORS / Web-Clients wie Plex)
Sicherheit	Sicher	Genauso sicher (kein Missbrauch möglich)
