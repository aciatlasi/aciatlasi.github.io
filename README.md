# Ortopedik Açı Atlası

**Canlı site:** https://aciatlasi.github.io/

Grafi üzerinde 31 ortopedik açının doğru ölçüm tekniğini adım adım gösteren, sürüklenebilir noktalı interaktif rehber.

Statik bir sitedir: derleme adımı, sunucu kodu veya veritabanı yoktur. Klasördeki dosyalar olduğu gibi herhangi bir statik barındırma servisine yüklenebilir.

## Dosyalar

| Dosya | Görevi |
|---|---|
| `index.html` | Uygulamanın tamamı (HTML, CSS, JS tek dosyada) |
| `favicon.svg` | Tarayıcı sekmesi simgesi |
| `icon-512.png` | Telefona "Ana ekrana ekle" simgesi |
| `manifest.webmanifest` | Uygulama gibi yüklenebilmesi için (PWA) |
| `sw.js` | Çevrimdışı çalışma: bir kez açıldıktan sonra internetsiz de açılır |

## Yayınlama seçenekleri

### 1. Netlify Drop (en kolay, hesap gerektirmeden ~1 dakika)
1. https://app.netlify.com/drop adresini açın.
2. `ortopedi-aci-atlasi` klasörünü sayfaya sürükleyip bırakın.
3. Size `https://xxxx.netlify.app` gibi bir adres verilir. Kalıcı olması için ücretsiz hesap açıp siteyi "claim" edin; ayarlardan adı değiştirebilirsiniz (ör. `ortopedi-aci-atlasi.netlify.app`).

### 2. GitHub Pages (ücretsiz, sürüm takibi ile)
1. GitHub'da yeni bir depo oluşturun (ör. `ortopedi-aci-atlasi`).
2. Bu klasördeki dosyaları depoya yükleyin ("Add file → Upload files").
3. Settings → Pages → Branch: `main`, klasör: `/ (root)` → Save.
4. Birkaç dakika içinde `https://<kullanıcı-adınız>.github.io/ortopedi-aci-atlasi/` adresinde yayında olur.

### 3. Cloudflare Pages / Vercel
Her ikisi de "statik site" olarak bu klasörü doğrudan kabul eder; build komutu boş, çıktı klasörü `/` bırakılır.

### Kendi alan adınız (ör. aciatlasi.com)
Alan adını bir kayıt firmasından aldıktan sonra, yukarıdaki servislerin "Custom domain" ayarından ekleyip DNS kayıtlarını onların gösterdiği şekilde girmeniz yeterli. HTTPS otomatik gelir.

## Yerelde açmak
`index.html`'e çift tıklamak yeterlidir. Çevrimdışı önbellek (service worker) yalnızca bir web sunucusu üzerinden açıldığında devreye girer:

```bash
python3 -m http.server 8000
```
ardından http://localhost:8000

## Güncelleme
`index.html`'de değişiklik yaptıktan sonra `sw.js` içindeki `CACHE='oaa-v2'` değerini bir artırın (`oaa-v3`), böylece kullanıcıların önbelleği yenilenir. Sonra dosyaları aynı servise tekrar yükleyin.

## Not
Bu uygulama eğitim amaçlıdır; çizimler şematiktir. Klinik karar için standart kaynaklar ve gerçek görüntüler esas alınmalıdır.
