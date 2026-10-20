# Challis & Company website

One static page listing the company's apps, served by GitHub Pages from `main` at <https://challis.com.au> (HTTPS enforced).

- `index.html`: the page. One `<li>` card per app; copy one to add an app, and give it a
  `p-<name>` class with an `--accent` colour in `style.css` (light and dark).
- `style.css`: same layout and greys as `pedantique/widen-site`; light and dark follow the system.
- `img/puzzlement.png`, `img/widen.png`: app icons, `sips -Z 240` from each app site's `img/icon.png`.
- Brand: brand blue `#191970` (midnight blue) and Raleway (Google Fonts), from the company artwork in OneDrive
  `C&Co/Admin/Artwork 2.0/`.
- `img/wordmark.svg`: `SVG/Logo/Footer_logo.svg` with `fill="currentColor"`, inlined in the
  `<h1>` of `index.html` so it turns light in dark mode. Re-inline it if the logo changes.
- `img/favicon.png` (64), `img/logo-mark.png` (256), `img/apple-touch-icon.png` (180, on navy):
  the round C-and-target mark, cropped from `Artwork 2.0/Favicon.png` and recoloured
  from the artwork's `#2a286b` to brand blue.

All links are relative, so the site works both at the github.io project path and on the domain.

<!--
Custom domain: challis.com.au (DNS at GoDaddy)

1. GoDaddy → challis.com.au → DNS. Remove the parked/forwarding records for @ and www
   (any A record for @ pointing at GoDaddy, and turn off Domain Forwarding if it is on).
   Leave every MX record (Google Workspace) and any TXT/SPF/DKIM/DMARC records alone.
   Add:
       A      @    185.199.108.153
       A      @    185.199.109.153
       A      @    185.199.110.153
       A      @    185.199.111.153
       CNAME  www  pedantique.github.io
   Optional IPv6:
       AAAA   @    2606:50c0:8000::153   (and 8001, 8002, 8003)
2. Recommended: verify challis.com.au for Pages (github.com/settings/pages → Add a domain),
   which gives one TXT record _github-pages-challenge-pedantique to add. This also covers
   widen.challis.com.au.
3. Once `dig +short challis.com.au` shows only the 185.199.x.153 addresses:
       echo challis.com.au > CNAME && git add CNAME && git commit -m "Custom domain" && git push
   then, once the certificate is issued:
       gh api -X PUT repos/pedantique/challis-site/pages -F https_enforced=true
-->
