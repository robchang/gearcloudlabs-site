# Deploy — gearcloudlabs.com

Static site. No build step. No paid platform required.

## Deploy

1. Copy **all files** in this directory to your web root (e.g. `/var/www/gearcloudlabs.com/`).
2. Point DNS A/AAAA (or CNAME) for `gearcloudlabs.com` and `www` at your host.
3. Enable HTTPS (Let's Encrypt / certbot, or your host's free TLS).

### nginx (sketch)

```nginx
server {
  listen 443 ssl http2;
  server_name gearcloudlabs.com www.gearcloudlabs.com;
  root /var/www/gearcloudlabs.com;
  index index.html;
  error_page 404 /404.html;
  location / { try_files $uri $uri/ $uri.html /404.html; }
  # ssl_certificate …;
}
```

### Apache (sketch)

```apache
DocumentRoot /var/www/gearcloudlabs.com
ErrorDocument 404 /404.html
# Prefer DirectoryIndex index.html
```

## Edit content daily

- **Insight post:** copy `templates/insight.html` (or `.md` for drafting) → `insights/your-slug.html`. Add a `<li>` on `insights/index.html`. Add URL to `sitemap.xml`.
- **Case study:** copy `templates/case-study.html` → `work/your-slug.html`. Link from `work/index.html` + sitemap.
- **Segment/demo page:** duplicate `media/index.html` or `smb/index.html` as a starting point.

## Fill TODOs before calling it done

- Booking link (Cal.com etc.) on home + contact
- Form endpoint (Formspree etc.) or keep mailto
- Proof / testimonials / logos (permissioned only)
- Optional Plausible/GoatCounter snippet in `<head>`
- Replace `hello@gearcloudlabs.com` if you use a different inbox
