# Ауыл Такси 🚕
Cloudflare Workers + D1 + PWA негізіндегі бастапқы MVP.

## Файлдар
- `public/index.html` — мобильді интерфейс
- `public/manifest.webmanifest`, `public/sw.js` — PWA
- `worker/index.js` — API
- `worker/migrations/0001_initial.sql` — D1 схемасы
- `wrangler.toml` — Cloudflare конфигурациясы

## Орнату
1. Cloudflare Dashboard → Workers & Pages → D1 → `auyl-taxi-db` атты дерекқор жасаңыз.
2. D1 Console-да `worker/migrations/0001_initial.sql` файлын орындаңыз.
3. `wrangler.toml` ішіндегі `database_id` орнына өз D1 ID-ін жазыңыз.
4. Компьютерде Wrangler орнатып, `wrangler login`, `wrangler secret put SESSION_SECRET`, `wrangler deploy` орындаңыз.
5. Бағыттар мен тарифтерді D1-ге енгізіңіз, мысалы:
```sql
INSERT INTO routes(from_name,to_name,price) VALUES ('Торғай ауылы','Аудан орталығы',2500),('Аудан орталығы','Қала',5000);
```
Бағалар — тек мысал, өз тарифіңізбен ауыстырыңыз.

## Ескерту
Бұл әзірлеу нұсқасы. SMS растауы және Kaspi API төлемі қосылмаған; Kaspi тек төлем тәсілі ретінде белгіленеді. Жүргізушілер әкімші мақұлдағанша тапсырыс қабылдай алмайды. Әкімші аккаунтын қауіпсіз seed тәсілімен бөлек орнату керек. Жария іске қоспас бұрын қауіпсіздік аудиті, rate limit, privacy policy және толық тестілеу қажет.
