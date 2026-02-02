# 🚀 Deployment Guide - Losovanie.sk

Návod na nasadenie aplikácie na produkčný server.

## 📦 Súbory na Upload

Nahrajte všetky tieto súbory na váš web hosting:

```
index.html          - Hlavný súbor aplikácie
manifest.json       - PWA manifest
robots.txt          - SEO - pravidlá pre roboty
sitemap.xml         - SEO - mapa stránok
.htaccess           - Apache konfigurácia (ak používate Apache)
README.md           - Dokumentácia (voliteľné)
```

## 🌐 Doména: www.losovanie.sk

### DNS Nastavenia

1. **A Record**: Smerujte `losovanie.sk` na IP adresu vášho servera
2. **CNAME**: Nastavte `www` ako alias pre `losovanie.sk`
3. **SSL Certifikát**: Zabezpečte HTTPS (Let's Encrypt, Cloudflare, atď.)

### Príklad DNS záznamov:
```
Type    Name    Content             TTL
A       @       123.456.789.012     Auto
CNAME   www     losovanie.sk        Auto
```

## 🔧 Hosting Requirements

### Minimálne Požiadavky:
- **Webserver**: Apache 2.4+ alebo Nginx 1.18+
- **PHP**: NIE je potrebné (čisto HTML/CSS/JS)
- **Database**: NIE je potrebné
- **Storage**: ~100 KB
- **Bandwidth**: Minimálne

### Odporúčané:
- ✅ SSL Certifikát (HTTPS)
- ✅ Kompresné (gzip/brotli)
- ✅ CDN (Cloudflare, atď.)
- ✅ HTTP/2 alebo HTTP/3

## 📝 Kroky Nasadenia

### 1. Príprava Súborov

```bash
# Skontrolujte, že máte všetky súbory
ls -la
# index.html, manifest.json, robots.txt, sitemap.xml, .htaccess
```

### 2. Upload na Server

#### Option A: FTP/SFTP
```bash
# Použite FTP klienta (FileZilla, Cyberduck, atď.)
# Nahrajte všetky súbory do root adresára (public_html, www, atď.)
```

#### Option B: SSH/SCP
```bash
scp -r * user@losovanie.sk:/var/www/html/
```

#### Option C: Git
```bash
git clone https://github.com/your-repo/losovanie.git
cd losovanie
# Nahrajte súbory na server
```

### 3. Nastavte Práva

```bash
# SSH do servera
ssh user@losovanie.sk

# Nastavte správne práva
chmod 644 index.html
chmod 644 manifest.json
chmod 644 robots.txt
chmod 644 sitemap.xml
chmod 644 .htaccess
```

### 4. Test Funkcionality

Otvorte v prehliadači:
- ✅ https://www.losovanie.sk
- ✅ https://losovanie.sk (redirect na www)
- ✅ http://losovanie.sk (redirect na https)

### 5. SEO Setup

#### Google Search Console:
1. Pridajte web: https://search.google.com/search-console
2. Overte vlastníctvo
3. Odošlite sitemap: https://www.losovanie.sk/sitemap.xml

#### Google Analytics (voliteľné):
Pridajte tracking kód pred `</head>`:
```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

## 🔒 Bezpečnosť

### SSL Certifikát (Let's Encrypt):
```bash
# Na Ubuntu/Debian serveri
sudo apt install certbot python3-certbot-apache
sudo certbot --apache -d losovanie.sk -d www.losovanie.sk
```

### Firewall:
```bash
# Povoľte iba HTTP/HTTPS
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw enable
```

## ⚡ Performance Optimalizácia

### Apache (.htaccess už obsahuje):
- ✅ Gzip kompresiu
- ✅ Browser caching
- ✅ Security headers

### Nginx (alternatíva k .htaccess):
```nginx
server {
    listen 80;
    server_name www.losovanie.sk losovanie.sk;
    return 301 https://www.losovanie.sk$request_uri;
}

server {
    listen 443 ssl http2;
    server_name www.losovanie.sk;
    
    ssl_certificate /path/to/cert.pem;
    ssl_certificate_key /path/to/key.pem;
    
    root /var/www/html;
    index index.html;
    
    # Gzip compression
    gzip on;
    gzip_types text/html text/css application/javascript;
    
    # Browser caching
    location ~* \.(html)$ {
        expires 1h;
    }
    
    location / {
        try_files $uri $uri/ /index.html;
    }
}
```

## 📊 Monitoring

### Check List po nasadení:
- [ ] Stránka sa načíta na https://www.losovanie.sk
- [ ] HTTP -> HTTPS redirect funguje
- [ ] Losovanie funguje správne
- [ ] Responzívny dizajn na mobile
- [ ] robots.txt je dostupný
- [ ] sitemap.xml je dostupný
- [ ] manifest.json je dostupný
- [ ] SSL certifikát je platný
- [ ] Žiadne chyby v konzole

### Nástroje na testovanie:
- PageSpeed Insights: https://pagespeed.web.dev/
- SSL Test: https://www.ssllabs.com/ssltest/
- Mobile-Friendly Test: https://search.google.com/test/mobile-friendly
- Schema Markup: https://validator.schema.org/

## 🆘 Riešenie Problémov

### Stránka sa nenačíta:
```bash
# Skontrolujte logy
sudo tail -f /var/log/apache2/error.log
# alebo
sudo tail -f /var/log/nginx/error.log
```

### .htaccess nefunguje:
```bash
# Povoľte mod_rewrite v Apache
sudo a2enmod rewrite
sudo systemctl restart apache2
```

### SSL chyby:
```bash
# Obnovte certifikát
sudo certbot renew
```

## 📞 Podpora

Pre technickú podporu kontaktujte:
- Email: info@losovanie.sk
- Web: www.losovanie.sk

---

© 2026 Losovanie.sk | Marián Šaray
