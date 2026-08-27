# Masa 2026

Tek kişilik jeopolitik simülasyon. 2026 dünyasından başlar, 177 ülkeden birini yönetirsin. Tek dosya, bağımlılık yok.

## Yayına alma

1. GitHub'da yeni bir repo aç (public olabilir, anahtar kodun içinde değil).
2. `index.html` dosyasını repo köküne yükle.
3. Settings → Pages → Source: `Deploy from a branch`, branch: `main`, klasör: `/ (root)`.
4. Bir iki dakika sonra `https://kullaniciadin.github.io/repoadi/` adresinde açılır.

## API anahtarı

Anahtarı **koda gömme**. Uygulama ilk açılışta kurulum ekranında anahtar istiyor ve yalnızca senin tarayıcının `localStorage` alanında tutuyor. Repo public olsa bile anahtar dışarı çıkmaz.

Anahtarı https://aistudio.google.com adresinden alabilirsin.

Model seçenekleri kurulum ekranında:

- **Hızlı** — `gemini-3.5-flash-lite`. Varsayılan. En düşük gecikme.
- **Dengeli** — `gemini-3.6-flash`. Daha iyi anlatım, biraz daha yavaş.
- Alttaki alana elle başka bir model adı da yazabilirsin.

Anahtar tarayıcıda tutulduğu için istek doğrudan tarayıcıdan Google'a gider. Bu kişisel kullanım için uygundur; uygulamayı başkalarına açacaksan anahtarı bir sunucu tarafına taşıman gerekir.

## Nasıl çalışıyor

Her turda oyunun durumu (tarih, kontrol edilen topraklar, dört stat, altı teknoloji hattı, kriz ısıları, ilişki tablosu, ekonomi göstergeleri, son gelişmeler) ve senin serbest metinle yazdığın hamle modele gidiyor. Model sonucu JSON olarak döndürüyor, uygulama da bunu duruma işleyip haritayı ve panelleri güncelliyor.

Çıktı `responseSchema` ile şemaya bağlandığı için biçim bozulmuyor. Cevap yine de uzunluk sınırına takılırsa, yarım kalan JSON son tamamlanmış alandan kesilip kurtarılıyor.

- **Bölge gündemi** — 13 açık kriz, her biri 0-100 ısı. Haritada konumlarına göre işaretli. Motor ısıları günceller, yeni kriz açar, çözülenleri kapatır.
- **Teknoloji** — yapay zekâ, yarı iletken, İHA, enerji, uzay, siber.
- **Diplomasi** — aktör bazlı -100/+100.
- **Dünya gündemi** — senin hamlenden bağımsız gelişmeler.

Oyun otomatik kaydediliyor, kurulum ekranından kaldığın yerden devam edebiliyorsun. Kayıtlar tarayıcıda durur; tarayıcı verilerini silersen kayıtlar da gider.

## Dünya tabanı

Başlangıç tablosu 27 Ağustos 2026 durumuna göre kuruldu: İran savaşı ve Hürmüz'ün kapalı olması, Ukrayna'da kilitli cephe, ABD-Çin çip ve nadir toprak kısıtlamaları, Mekke Ortak Savunma Anlaşması, Sudan, Sahel, Gazze, Kızıldeniz, Venezuela sonrası Karayipler. Sonrası simülasyon.

Tabanı güncellemek istersen `index.html` içindeki `BRIEF` metnini ve `CRISES` listesini düzenlemen yeterli.
