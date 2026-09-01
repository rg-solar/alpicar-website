# Alpicar – Website

Statische Website für **Alpicar SRL** (Appiano sulla strada del vino / Eppan
an der Weinstraße, Südtirol). Deutsch und Italienisch, helles "Alpin"-Design.

## Struktur

```
alpicar-website/
├── index.html            Startseite (Deutsch)
├── impressum.html         Impressum (Deutsch)
├── it/
│   ├── index.html         Startseite (Italienisch)
│   └── impressum.html     Note legali (Italienisch)
├── assets/
│   ├── css/style.css      gesamtes Design (von DE & IT gemeinsam genutzt)
│   ├── js/main.js         Menü-Toggle, Jahr im Footer
│   └── img/                Logo, Favicons, Foto-Platzhalter
├── robots.txt
├── sitemap.xml             inkl. hreflang DE/IT
├── llms.txt                Zusammenfassung für KI-Systeme
└── README.md
```

Reines HTML/CSS/JS ohne Build-Schritt. DE und IT teilen sich `assets/` –
Design-Änderungen an `style.css` wirken automatisch auf beide Sprachen.

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

- Navigation klappt unter ca. 900px Breite zu einem Menü-Icon (☰) zusammen;
  der "Kontakt aufnehmen"-Button wird auf Mobilgeräten ausgeblendet, da der
  Kontakt-Link im aufklappbaren Menü enthalten ist.
- Alle Grid-Layouts (Hero, Leistungen, Über uns, Kontakt) wechseln unter
  900px auf eine Spalte.
- Zusätzliche Feinjustierung (Abstände, Schriftgrößen, Kartenränder) unter
  480px Breite für kleine Smartphones.

Zum Testen: Browserfenster schmaler ziehen oder die Entwicklertools-
Gerätesimulation verwenden.

## Inhalte / offene Punkte zum Prüfen

- Öffnungszeiten / Terminvergabe – aktuell nur „nach Vereinbarung" formuliert.
- Impressum: Handelsregister-/REA-Nummer und ggf. Datenschutzhinweise ergänzen
  (in beiden Sprachversionen).
- Echte Fotos fehlen noch (Platzhalter markiert mit "Foto folgt" /
  "Foto in arrivo") – Dateien in `assets/img/` ablegen und in beiden
  `index.html`-Dateien gegen den `.photo-placeholder`-Block austauschen.
- Marken-Logos sind aktuell **Text-Badges** für die Reifenmarken (Michelin,
  Pirelli, Vredestein), keine echten Logo-Dateien – dafür bräuchte es
  offizielle Logo-Freigaben/-Dateien der Marken. Fahrzeugmarken (Porsche,
  Ferrari usw.) werden bewusst **nirgends** namentlich genannt – Texte
  sprechen stattdessen generisch von "Luxusautos und großen Reifendimensionen".
- Referenzkunden (z. B. Golfclubs) wurden bewusst nicht namentlich genannt,
  da im Ordner keine Freigabe dafür vorlag – kann bei Bedarf ergänzt werden.
- Logo: aus `logo/LogoAlpicar verde.pdf` freigestellt (Vektor-Version, hohe
  Auflösung), helle Header-Variante + Favicon (Bergsilhouette).

## SEO &amp; KI-Optimierung

- Aussagekräftige `<title>`/`<meta description>` mit Ort + Leistungen, ohne Markennamen Dritter
- Open-Graph- &amp; Twitter-Card-Tags fürs Teilen in sozialen Medien
- `canonical`- und `hreflang`-Links (DE/IT), `meta robots`, `theme-color`
- Favicon (aus dem Logo abgeleitet, mehrere Größen + Apple-Touch-Icon)
- Strukturierte Daten (JSON-LD): `AutoRepair` (Name, Adresse, Telefon, E-Mail) + `FAQPage`, je Sprache
- FAQ-Sektion (natives `<details>`, kein JS nötig) – beantwortet typische Fragen, liefert zusätzlichen crawlbaren Text
- `robots.txt`, `sitemap.xml` (mit hreflang-Alternates)
- `llms.txt` – kurze, strukturierte Zusammenfassung für KI-Systeme (ChatGPT-Suche, Perplexity u. Ä.)

**Wichtig:** `canonical`/`og:url`/Sitemap gehen aktuell von `https://www.alpicar.bz/`
aus (aus der E-Mail-Adresse `info@alpicar.bz` abgeleitet). Bitte vor dem
Live-Schalten prüfen, ob das die tatsächliche künftige Domain ist – falls
nicht (z. B. bei GitHub-Pages-URL), müssen diese Stellen einmal angepasst werden.

## Auf GitHub veröffentlichen

Lokales Repo ist bereits initialisiert (siehe `git log`). Um es auf GitHub
als neues Repository **alpicar-website** zu veröffentlichen (im Ordner
`alpicar-website` ausführen):

```bash
gh repo create alpicar-website --public --source=. --remote=origin --push
```

Falls `gh` nicht installiert/eingeloggt ist, alternativ über die GitHub-Weboberfläche:

1. Auf github.com ein neues, leeres Repository `alpicar-website` anlegen (ohne README).
2. Dann lokal:
   ```bash
   git remote add origin https://github.com/<dein-account>/alpicar-website.git
   git branch -M main
   git push -u origin main
   ```

### Hosting via GitHub Pages

Nach dem Push: im Repo unter **Settings → Pages** als Quelle den Branch
`main` (Ordner `/root`) auswählen. Die Seite ist danach unter
`https://<dein-account>.github.io/alpicar-website/` erreichbar (Deutsch)
bzw. `.../it/` (Italienisch).
