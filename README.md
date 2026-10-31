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

Die Seite lädt keine Ressourcen von Drittanbietern und setzt keine Cookies. Die Bierliste („Was war das noch gleich“, Anker `#bierliste`) war in WordPress per Jetpack „Repeat Visitor“ erst ab dem dritten Besuch sichtbar. Das geht auf einer statischen Seite nicht serverseitig; sie ist deshalb seit 31.10.2026 immer sichtbar und wurde aus dem WordPress-Datenbankexport übernommen.

**Achtung:** Das Repository ist öffentlich. Alles, was in `index.html` steht, ist im Quelltext und in der Git-Historie für jeden lesbar – auch wenn es auf der Seite per CSS oder JavaScript versteckt wird.

## Lokal testen

```sh
python3 -m http.server 8000
# http://localhost:8000/
```

## Umstellung (erledigt am 31.10.2026)

1. **Pages aktiviert:** Settings → Pages → „Deploy from a branch“, `main` / `/ (root)`, Custom Domain `tschoch.de`.
2. **Domain verifiziert:** Profil-Settings → Pages → „Verified domains“, TXT-Eintrag `_github-pages-challenge-hui-161` (muss bleiben).
3. **DNS bei Cloudflare** (die DNS-Verwaltung bleibt dort, auch nach dem Registrarwechsel), alle Einträge „DNS only“:
   - `tschoch.de` A: 185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153
   - `tschoch.de` AAAA: 2606:50c0:8000::153, 2606:50c0:8001::153, 2606:50c0:8002::153, 2606:50c0:8003::153
   - `www` CNAME: `hui-161.github.io.`
4. **HTTPS:** Zertifikat ausgestellt, „Enforce HTTPS“ aktiv.
