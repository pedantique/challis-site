# Challis & Company website

One static page listing the company's apps, served by GitHub Pages from `main` at
<https://pedantique.github.io/challis-site/> (planned: <https://challis.com.au>).

- `index.html`: the page. One `<li>` card per app; copy one to add an app, and give it a
  `p-<name>` class with an `--accent` colour in `style.css` (light and dark).
- `style.css`: same palette and type as `pedantique/widen-site`; light and dark follow the system.
- `img/puzzlement.png`, `img/widen.png`: app icons, `sips -Z 240` from each app site's `img/icon.png`.
- `img/favicon.svg`, `img/apple-touch-icon.png`: the "C&" mark. Regenerate the PNG with
  `sed 's/ rx="40"//' img/favicon.svg | rsvg-convert -w 180 -h 180 -o img/apple-touch-icon.png`.

All links are relative, so the site works both at the github.io project path and on the domain.

When `widen.challis.com.au` is live, change the Widen card's `href` (and "Learn more" if wanted).

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
