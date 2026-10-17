# Reel Moda – Yayına alma rehberi

## Klasörde neler var?
- `index.html` : Sitenin kendisi (dokunmanıza gerek yok)
- `data.json` : Ürünler, fiyatlar, kategoriler, kargo ayarı, Instagram/WhatsApp bilgisi. Sitede değiştirmek istediğiniz her şey burada.
- `img/` : Ürün fotoğrafları buraya yüklenir
- `sitemap.xml`, `robots.txt` : Google için

## 1) Alan adınızı yazın (tek seferlik)
`index.html`, `sitemap.xml` ve `robots.txt` dosyalarında `ALANADINIZ.com` yazan yerleri kendi alan adınızla değiştirin (örn. `reelmoda.com`). GitHub'da dosyayı açıp kalem simgesine basarak düzenleyebilirsiniz.

## 2) GitHub'a yükleme
1. github.com'da ücretsiz hesap açın, **New repository** ile `reelmoda` adında depo oluşturun.
2. **Add file → Upload files** ile bu klasörün içindekileri (index.html, data.json, sitemap.xml, robots.txt ve img klasörü) sürükleyip bırakın, **Commit changes**'a basın.
   (Zip dosyasını önce bilgisayarınızda açın, zip'in kendisini yüklemeyin.)

## 3) Yayınlama (önerilen: Cloudflare Pages veya Netlify)
GitHub Pages ticari/e-ticaret siteleri için uygun değildir, bu yüzden aşağıdakilerden birini kullanın.

**Cloudflare Pages:** Workers & Pages → Create → Pages → Connect to Git → `reelmoda` deposunu seçin. Build command boş, output directory boş (veya `/`) kalsın → Deploy.

**Netlify:** Add new site → Import from Git → deponuzu seçin. Build command ve publish directory boş kalsın → Deploy.

Site önce `...pages.dev` veya `...netlify.app` adresinde açılır. Önce orada her şeyin çalıştığını kontrol edin.

## 4) .com alan adı bağlama
1. Alan adını Natro, Turhost, GoDaddy, Namecheap vb. bir yerden satın alın.
2. Cloudflare/Netlify'da **Custom domains** bölümüne alan adınızı ekleyin.
3. Ekranda gösterilen DNS kayıtlarını (genellikle CNAME veya A kaydı) alan adı sağlayıcınızın DNS panelinde girin. Birkaç dakika ile birkaç saat arasında aktif olur, HTTPS otomatik gelir.

## 5) Google'a tanıtma
search.google.com/search-console → alan adınızı ekleyin → doğrulayın → **Sitemaps** bölümüne `sitemap.xml` yazıp gönderin. Google'da görünmesi günler veya haftalar sürebilir.

## data.json nasıl düzenlenir?
GitHub'da `data.json` dosyasını açıp kalem simgesine basın, değiştirin, **Commit changes**. Site birkaç dakikada güncellenir. Virgül, tırnak ve parantezlere dikkat edin; hata olursa site boş görünür. Emin değilseniz jsonlint.com'da kontrol edin.

- **Fiyat:** ürünün `"p"` değeri (sadece rakam, ör. `1490`)
- **Beden ve stok:** `"s": {"S": 5, "M": 3}` (listede olmayan beden satılmaz, `0` tükendi demektir)
- **Fotoğraf:** Fotoğrafı `img` klasörüne yükleyin, ürünün `"im"` satırına `["img/elbise-1.jpg", "img/elbise-2.jpg"]` yazın. İlk fotoğraf kapaktır. Fotoğraflar 1000 piksel genişliğinde ve 300 KB civarı olursa site hızlı açılır.
- **Yeni ürün:** Bir ürün bloğunu kopyalayıp yapıştırın, numarasını (`"9"` gibi) ve bilgilerini değiştirin. Kategori adı `site.cats` listesindekilerle aynı yazılmalı.
- **Ürün silme:** İlgili bloğu tamamen silin.
- **Kategori ekleme/yeniden adlandırma:** `site.cats` listesini değiştirin; ürünlerdeki `"c"` değerlerini de aynı yazın.
- **Ücretsiz kargo limiti ve kargo ücreti:** `site.free` ve `site.ship` (`free` 0 olursa tüm siparişlerde ücretsiz)
- **Instagram ve WhatsApp:** `store.ig` (kullanıcı adı), `store.wa` (905xxxxxxxxx biçiminde), `store.mail`

## Önemli notlar
- Sipariş akışı müşteriye WhatsApp/e-posta ile sipariş özeti gönderme biçiminde çalışır; stok kendiliğinden düşmez, `data.json` üzerinden sizin güncellemeniz gerekir.
- Kartla online ödeme için bir ödeme sağlayıcısı (iyzico, PayTR vb.) bağlamanız gerekir. Şu an sitede kart bilgisi alınmaz.
- Gerçek satışta mesafeli satış sözleşmesi, iade ve gizlilik (KVKK) metinleri gibi yasal sayfalar gerekebilir. Bunun için bir uzmana danışın.
