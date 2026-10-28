# tschoch.de

Statische Kopie von tschoch.de für GitHub Pages (Quelle: Branch `main`, Ordner `/`).

## Herkunft

- Gespiegelt am 28.10.2026 aus der WordPress-Installation bei Ionos (WordPress 6.9.1, Theme Astra 4.11.13).
- Es gibt kein CMS mehr. Inhalte werden direkt in `index.html` geändert.
- Die Git-Historie zeigt jeden Migrationsschritt einzeln: Import, Links, Bereinigung, Fonts, Pages-Dateien.

## Aufbau

| Pfad | Inhalt |
|---|---|
| `index.html` | Startseite (Onepager mit Ankern) |
| `404.html` | Fehlerseite im Stil der Seite, mit rootrelativen Pfaden |
| `wp-content/`, `wp-includes/` | Theme-CSS/JS und Bilder in der alten WordPress-Pfadstruktur, damit alte Bild-URLs gültig bleiben |
| `fonts/` | Karma und Sono (SIL OFL 1.1), lokal statt über Google Fonts |
| `CNAME`, `.nojekyll`, `robots.txt`, `sitemap.xml` | Einstellungen für GitHub Pages und Suchmaschinen |

Die Seite lädt keine Ressourcen von Drittanbietern. Der Jetpack-Block „Repeat Visitor“ setzt im Browser ein Zähl-Cookie (`jp-visit-counter`); dabei werden keine Daten übertragen.

## Lokal testen

```sh
python3 -m http.server 8000
# http://localhost:8000/
```

## Umstellung (offen)

1. **Pages aktivieren:** Settings → Pages → „Deploy from a branch“, `main` / `/ (root)`.
   - Bei einem privaten Repo ist dafür GitHub Pro oder höher nötig.
2. **Domain verifizieren:** Profil-Settings → Pages → „Add a domain“, dann den angezeigten TXT-Eintrag `_github-pages-challenge-…` beim DNS-Anbieter setzen.
3. **DNS beim neuen Anbieter einrichten:**
   - `tschoch.de` A: 185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153
   - `tschoch.de` AAAA: 2606:50c0:8000::153, 2606:50c0:8001::153, 2606:50c0:8002::153, 2606:50c0:8003::153
   - `www` CNAME: `hui-161.github.io.`
4. Ist das Zertifikat ausgestellt, unter Settings → Pages „Enforce HTTPS“ aktivieren.
