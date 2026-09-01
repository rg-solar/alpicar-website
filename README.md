# Alpicar – Website

Statische Website für **Alpicar SRL** (Appiano sulla strada del vino / Eppan
an der Weinstraße, Südtirol). Deutsch und Italienisch, helles "Alpin"-Design.

**Live-Repo:** https://github.com/rg-solar/alpicar-website
**Vorschau (GitHub Pages):** https://rg-solar.github.io/alpicar-website/
**Zieldomain (bestätigt):** `https://www.alpicar.bz/`

## Struktur

```
alpicar-website/
├── index.html              Startseite (Deutsch)
├── impressum.html          Impressum (Deutsch)
├── datenschutz.html        Datenschutzerklärung (Deutsch)
├── it/
│   ├── index.html          Startseite (Italienisch)
│   ├── impressum.html      Note legali (Italienisch)
│   └── privacy.html        Informativa privacy (Italienisch)
├── assets/
│   ├── css/style.css       gesamtes Design (von DE & IT gemeinsam genutzt)
│   ├── js/main.js          Menü-Toggle, Jahr im Footer
│   ├── fonts/              Inter (self-hosted, statt Google Fonts CDN)
│   └── img/                Logo, Favicons, Foto-Platzhalter
├── robots.txt
├── sitemap.xml              inkl. hreflang DE/IT, auch für die Datenschutz-Seiten
├── llms.txt                 Zusammenfassung für KI-Systeme
└── README.md
```

Reines HTML/CSS/JS ohne Build-Schritt. DE und IT teilen sich `assets/` –
Design-Änderungen an `style.css` wirken automatisch auf beide Sprachen.

## Seitenaufbau (Startseite)

Hero (mit klarer Sofort-Aussage direkt unter dem Slogan + „Jetzt anrufen“) →
Trust-Zeile → Reifenmarken → Leistungen (3 Karten: Reifenservice,
Kfz-Werkstatt, Fahrzeugvermittlung) → **Präzisionsschliff für Golfplätze**
(eigener Spezialbereich für SBR900, nicht mehr nur eine Karte unter
„Leistungen“) → FAQ → Über uns → Jobs → Kontakt (mit Anrufen/WhatsApp/
Route-Buttons). Zusätzlich eine mobile Sticky-Kontaktleiste
(Anrufen | WhatsApp | Route), die auf Bildschirmen unter 900px immer am
unteren Rand sichtbar bleibt.

## Sprachen

Oben rechts in der Navigation wechselt ein DE/IT-Umschalter zwischen den
Versionen. Beide Seiten sind inhaltlich identisch, mit `hreflang`-Angaben
im `<head>` und in der `sitemap.xml` verknüpft (wichtig für Google, damit
nicht eine Sprachversion als "Duplicate Content" der anderen gewertet wird).

Um Inhalte zu ändern, künftig **beide** Sprachversionen pflegen:
`index.html` (Deutsch) und `it/index.html` (Italienisch) enthalten denselben
Aufbau, nur den Text jeweils in der passenden Sprache.

## Mobile

Die Seite ist responsiv (ein CSS, keine separate mobile Seite):

- Navigation klappt unter ca. 900px Breite zu einem Menü-Icon (☰) zusammen.
- Eine fixe Sticky-Leiste (Anrufen / WhatsApp / Route) ist unter 900px immer
  am unteren Bildschirmrand sichtbar (`assets/css/style.css`,
  `.mobile-stickybar`).
- Alle Grid-Layouts (Hero, Leistungen, SBR900-Bereich, Über uns, Kontakt)
  wechseln unter 900px auf eine Spalte.
- Getestet mit Playwright (Chromium) in Desktop- und Mobile-Ansicht, inkl.
  echtem Klick-Test des Menü-Buttons – nicht nur Screenshot-Vergleich.
- **Bekannter Stolperstein, bereits gelöst:** `backdrop-filter` auf einem
  Vorfahren-Element erzeugt in Chromium einen neuen Containing Block für
  `position:fixed`-Nachfahren. Deshalb liegt der Blur-Effekt im Header auf
  einem `::before`-Pseudoelement statt direkt auf `<header>`, und die mobile
  Sticky-Leiste liegt bewusst außerhalb von `<header>` als direktes Kind von
  `<body>`.

## Inhalte / offene Punkte

**1. Echte Fotos – höchste Priorität.** Alle `.photo-placeholder`-Blöcke
("Foto folgt" / "Foto in arrivo") warten auf echtes Bildmaterial. Eine
automatische Suche im E-Mail-Archiv wurde versucht, aber verworfen: die dort
gefundenen Bilder waren fast ausschließlich sensible Kundendokumente
(Personalausweise, Führerscheine, Rechnungen) oder Fotos aus einem anderen
Geschäftsbereich (Stapler-Handel) – nichts davon wurde verwendet oder
gespeichert. Empfohlene Foto-Liste (mit dem Kunden abgestimmt):
Werkstatt außen/innen, Reifenservice an einem hochwertigen Fahrzeug,
Rad/Reifen-Detail, SBR900 beim Schleifen (idealerweise Vorher/Nachher),
Fahrzeugübergabe, Porträt Gunnar Giuliani/Team. Sobald Fotos vorliegen,
einfach in `assets/img/` ablegen und die jeweiligen `.photo-placeholder`-
Blöcke in `index.html` / `it/index.html` ersetzen.

**2. Reifenmarken-Logos.** Aktuell weiterhin Text-Badges (mit kleinem
Reifen-Icon). Ein Versuch, offizielle Vektor-Logos von Michelin, Pirelli und
Vredestein automatisch zu laden, ist an den Netzwerk-Einschränkungen dieser
Arbeitsumgebung gescheitert (Wikimedia/Markenseiten waren nicht erreichbar).
Am schnellsten geht es, wenn Gunnar die drei offiziellen Logo-Dateien (SVG
oder PNG mit transparentem Hintergrund, z. B. aus dem Presse-/Händlerbereich
der Marken-Websites) schickt – die werden dann direkt eingesetzt.

**3. Über uns – noch offen.** Wartet auf ein paar Stichworte von Gunnar
(warum gegründet, wie lange schon, was ihm wichtig ist), um den Abschnitt
persönlicher zu machen.

**4. Impressum.** Handelsregister-/REA-Nummer und eine rechtssichere
DSGVO-Angabe nach Art. 13 sollten von Alpicar (ggf. mit Steuerberater/
Rechtsberatung) vor dem Live-Schalten noch bestätigt werden. Der sichtbare
Platzhalter-Hinweis wurde entfernt, damit die Seite fertig wirkt – die
Prüfung selbst steht aber noch aus.

**5. Öffnungszeiten / Terminvergabe** – aktuell nur „nach Vereinbarung"
formuliert.

**6. Referenzkunden** (z. B. Golfclubs) wurden bewusst nicht namentlich
genannt, da keine Freigabe dafür vorlag – kann bei Bedarf ergänzt werden.

**7. SEO-Ausbau (später):** eigene Unterseiten für z. B. „Reifenservice
Eppan", „Kfz-Werkstatt Eppan", „Fahrzeugvermittlung Südtirol" und
„Schleifservice Golfplatz-Mähwerke" – die technische Grundlage (Struktur,
sitemap.xml, hreflang) ist bereits vorbereitet.

Logo: aus `logo/LogoAlpicar verde.pdf` freigestellt (Vektor-Version, hohe
Auflösung), helle Header-Variante + Favicon (Bergsilhouette).

## SEO &amp; KI-Optimierung

- Aussagekräftige `<title>`/`<meta description>` mit Ort + Leistungen, ohne Markennamen Dritter
- Open-Graph- &amp; Twitter-Card-Tags fürs Teilen in sozialen Medien, `og:image` als absolute URL
- `canonical`- und `hreflang`-Links (DE/IT), `meta robots`, `theme-color`
- Favicon (aus dem Logo abgeleitet, mehrere Größen + Apple-Touch-Icon)
- Strukturierte Daten (JSON-LD): `AutoRepair` (Name, Adresse, Telefon, E-Mail) + `FAQPage`, je Sprache
- FAQ-Sektion (natives `<details>`, kein JS nötig) – beantwortet typische Fragen, liefert zusätzlichen crawlbaren Text
- `robots.txt`, `sitemap.xml` (mit hreflang-Alternates, inkl. Datenschutz-Seiten)
- `llms.txt` – kurze, strukturierte Zusammenfassung für KI-Systeme (ChatGPT-Suche, Perplexity u. Ä.)
- Google Fonts selbst gehostet (`assets/fonts/`) – kein externer Request an fonts.googleapis.com mehr,
  schneller und ohne Drittanbieter-Datenübertragung

## Auf GitHub veröffentlichen

Bereits erledigt – das Repo ist live unter
https://github.com/rg-solar/alpicar-website (Branch `master`). Für künftige
Änderungen genügt in diesem Ordner:

```bash
git add -A
git commit -m "Beschreibung der Änderung"
git push
```

### Hosting via GitHub Pages

GitHub Pages ist bereits aktiviert (Branch `master`, Ordner `/root`). Die
Vorschau ist erreichbar unter https://rg-solar.github.io/alpicar-website/
(Deutsch) bzw. `.../it/` (Italienisch). Sobald die eigene Domain
`alpicar.bz` per DNS auf GitHub Pages zeigt, kann sie in
**Settings → Pages → Custom domain** hinterlegt werden.
