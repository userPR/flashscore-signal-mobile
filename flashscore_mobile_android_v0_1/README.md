# Flashscore Canlı Sinyal Takipçisi — Android v0.1

Bu proje masaüstündeki V3.10.11 Chrome uzantısının ilk Android portudur.

## Bu sürümde olanlar

- Uygulamanın kendi mobil Canlı Sinyaller ekranı
- Foreground service ile canlı monitor
- Telefon bildirimi
- Takipli takım modu
- Tüm Maçlar Modu
- Tüm Maçlar Modu: 15–30 dakika 0-0 ve 60–82 dakika 0-0
- Normal mod: 15–30 beraberlik / takipli takım geride
- Normal mod: 60–82 beraberlik / takipli takım geride
- 15 / 20 / 25 / 30 checkpoint kontrolü
- Kural 2: 18–30, 0-0, ilgili lig, ev sahibi >=2 isabetli şut
- Son 5 dakikada toplam +4 isabetli şut sinyali
- İsabetli şut + Big chances taraması
- Bir detay sayfası 25 saniyede sonuç vermezse sıradaki maça geçme
- Bildirim kartında güncel dakika, skor, isabetli şut ve Big chances

## Mimari

Uygulama iki WebView kullanır:

1. `monitorWebView`: Flashscore futbol canlı listesini izler ve canlı maç snapshotlarını çıkarır.
2. `workerWebView`: Maçları sırayla STATS sayfasında açar, Show more varsa tıklar ve istatistikleri okur.

Kural motoru ve telefon bildirimleri native Java servisinde çalışır. UI, local HTML/CSS/JS WebView ekranıdır.

## Android Studio ile APK oluşturma

1. Android Studio'da bu klasörü `Open` ile açın.
2. İstenirse Android SDK Platform 35'i kurmasına izin verin.
3. Gradle senkronizasyonunun bitmesini bekleyin.
4. `Build > Build App Bundles or APKs > Build APKs` seçin.
5. Debug APK genelde `app/build/outputs/apk/debug/app-debug.apk` altında oluşur.

Telefon Android 13+ ise ilk açılışta bildirim izni ister.

## Mobilde stabil çalışma için

Bu sürüm foreground service kullanır ve sürekli bildirim alanında `Flashscore Canlı Sinyaller` servisini gösterir. Telefonun üreticiye özel pil optimizasyonu servisi durdurursa uygulamayı pil ayarlarında kısıtlanmamış / unrestricted çalışmaya almak gerekebilir.

## Önemli teknik not

Mobil sürüm ilk porttur. Flashscore HTML/DOM yapısını değiştirdiğinde masaüstündeki parser gibi mobil parser da güncelleme isteyebilir. Özellikle cihaz arka plandayken WebView davranışı gerçek telefonda test edilmelidir.
