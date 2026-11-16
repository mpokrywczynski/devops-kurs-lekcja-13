# Lekcja 13 – vhost portfolio.local (Nginx)

- `nginx/portfolio.local` – konfiguracja serwera (sites-available)
- `www/` – pliki strony (/var/www/portfolio.local)

## Wdrożenie
```bash
sudo cp nginx/portfolio.local /etc/nginx/sites-available/
sudo ln -s /etc/nginx/sites-available/portfolio.local /etc/nginx/sites-enabled/
sudo mkdir -p /var/www/portfolio.local
sudo cp -r www/. /var/www/portfolio.local/
head -c 3M /dev/urandom | sudo tee /var/www/portfolio.local/pobierz/duzy-plik.bin > /dev/null
sudo chown -R www-data:www-data /var/www/portfolio.local
sudo nginx -t && sudo systemctl reload nginx
```

## Sprawdzenie
```bash
curl -I -H "Host: portfolio.local" http://127.0.0.1/
curl -I -H "Host: portfolio.local" http://127.0.0.1/nie-ma-takiej
curl -I -H "Host: portfolio.local" http://127.0.0.1/test-500
curl -H "Host: portfolio.local" http://127.0.0.1/pobierz/
```
