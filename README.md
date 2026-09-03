# Barkod etiket oluşturucu

Ürün listesinden yazdırılabilir barkod etiketi hazırlar. Tek bir `index.html`
dosyası — kurulum, derleme, sunucu yok. Çift tıklayınca açılır.

**Canlı sürüm:** [hanzala.com.tr/araclar/barkod-etiket-olusturucu](https://hanzala.com.tr/araclar/barkod-etiket-olusturucu)

<br>

## Ne yapıyor

- **EAN-13 ve Code 128.** EAN-13'te 12 hane girerseniz kontrol hanesini kendi
  hesaplar; 13 hane girip yanlışsa uyarır, sessizce bozuk barkod basmaz.
- **A4 etiket tabakası** (70×37, 105×37, 52,5×29,7, 38×21, 105×74 mm) veya
  **termal etiket yazıcısı** için özel mm ölçüsü. Rulo modunda her etiket
  kendi sayfasına gider.
- **Adet sütunu** — aynı ürünün kaç etiketi basılacağını yazarsınız.
- **Eski fiyat sütunu** — üstü çizili eski fiyat ve indirim yüzdesi.
- Dört düzen, yazı ölçeği, kalın/eğik, ad ve fiyatı gizleme.

Veri hiçbir yere gitmiyor: girdiğiniz liste tarayıcıdan çıkmıyor, sunucu yok.

<br>

## Giriş biçimi

Her satıra bir ürün, sütunlar **sekme**, **noktalı virgül** veya **boru** ile:

```
Türk kahvesi	8690000000012	45	2
Çay	869000000002	20
İndirimli çay	8690000000012	20	1	35
```

`ad · barkod · fiyat · adet · eski fiyat` — adet boşsa 1 kabul edilir.

Satırda bu üç ayraçtan hiçbiri yoksa virgüle düşülür. Virgül bilerek son çare:
Türkçe fiyat `145,90` yazılıyor ve virgülü ayraç saymak fiyatı 145, adedi 90
yapıyordu — kullanıcı tek etiket isterken 90 etiket basılıyordu.

<br>

## Diller

Türkçe, İngilizce, Rusça, Almanca ve Arapça — sitedeki dillerin aynısı.
Ölçüler, örnek liste, tabaka adları ve uyarı metinleri de çevriliyor:
`52,5×29,7 mm` Rusçada `52,5×29,7 мм`, İngilizcede `52.5×29.7 mm` oluyor.

Arapça sağdan sola diziliyor. İki istisna var: ürün listesi kutusu soldan sağa
ve sola yaslı kalıyor (insanlar bu listeyi Excel'den yapıştırıyor, sütunlar
yapıştırıldığı sırada durmalı), etiket önizlemesi de öyle — o kutu baskı
çıktısı, sayfa yönünden etkilenmemeli.

Her dilin kendi adresi var: `index.html?dil=en`. Bağlantıyı paylaşınca aynı
dille açılıyor, `hreflang` etiketleri de bu adresleri gösteriyor. Dil seçilmezse
tarayıcının dili kullanılıyor, o da tanınmıyorsa Türkçe.

Örnek liste yalnızca siz henüz yazmadıysanız dile göre değişiyor — yazdığınız
liste dil değiştirince silinmiyor.

<br>

## Kullanım

`index.html` dosyasını indirip çift tıklayın. Barkod çizimi için
[JsBarcode](https://github.com/lindell/JsBarcode) CDN'den yükleniyor, o yüzden
ilk açılışta internet gerekiyor.

Kendi sitenize koymak isterseniz dosyayı olduğu gibi kopyalayın; başka bir
bağımlılığı yok.

<br>

## Sınama

`index.html?test=1` adresini açın. Kontrol hanesi hesabı, ayraç seçimi ve
barkod doğrulaması için sınamalar çalışır; ardından beş dilin çeviri
tablosunda anahtarların ve düzen adlarının tam olduğu kontrol edilir. Biri
kalırsa sekme başlığı `HATA:` olur.

<br>

## Lisans

MIT — [LICENSE](LICENSE). İstediğiniz gibi kullanın, değiştirin, satın.

Bu araç [hanzala.com.tr](https://hanzala.com.tr) için yazıldı. Orada
[başka ücretsiz araçlar](https://hanzala.com.tr/araclar) da var.
