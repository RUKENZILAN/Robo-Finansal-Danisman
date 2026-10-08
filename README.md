# Robo-Finansal-Danışman
# Robo Advisor / Robo Danışman

Page: https://robo-finansal-danisman.vercel.app/

[English](#english) · [Türkçe](#türkçe)

---

## English

Robo Danışman  is a single-page robo advisor for Turkish savers. It asks six questions, assigns a risk profile, and suggests how to split money across term deposits, a money market fund, a debt instruments fund, an equity fund, gold, silver and foreign currency. It then projects three return scenarios over your investment horizon.


### Features

- Risk questionnaire with six questions (age, horizon, reaction to a 20% loss, goal, emergency fund, experience).
- Five profiles: very cautious, cautious, balanced, growth-oriented, aggressive.
- Allocation donut chart and a per-asset table with amounts in TRY.
- Bad, expected and good scenario chart for 1, 3, 5 or 10 years, with monthly contributions and an inflation-adjusted value.
- Turkish / English switch, four accent colors (teal, indigo, rose, graphite) and a light / dark switch. The choices are remembered in the browser.
- Works on phone and desktop. No backend, no account, no data leaves the page.

### How it works

1. Each answer scores 1 to 4. The six scores are added (range 6 to 24).
2. The total picks a profile: up to 9 very cautious, 10–13 cautious, 14–17 balanced, 18–21 growth-oriented, 22 or more aggressive.
3. Each profile has a fixed allocation (see `PROFILES` in the script).
4. Two safety rules adjust it:
   - A 1-year horizon moves all equity and silver to the money market fund.
   - No emergency fund moves up to 10 points of equity and silver to the money market fund.
5. The expected return is the weighted average of each asset's annual return. The bad and good scenarios subtract or add each asset's volatility, assuming every asset moves the same way at the same time. Real assets do not, so the real range is narrower.

### Default assumptions (examples, not forecasts)

| Asset | Return %/yr | Volatility % |
|---|---|---|
| Term deposit | 38 | 1 |
| Money market fund | 40 | 1 |
| Debt instruments fund | 42 | 6 |
| Equity fund | 55 | 30 |
| Gold | 45 | 18 |
| Silver | 50 | 30 |
| Foreign currency | 25 | 12 |
| Inflation | 30 | n/a |

These numbers were chosen by the author and are not taken from current market data. Edit them in the page under "Edit return assumptions", or change `ASSETS` in the script, and use your current deposit rate and fund returns.

### Customizing

Everything is in one file, `robo-danisman.html`.

- **Name:** change the `<title>`, the `kicker` strings in both languages, and the `oranla-*` storage keys.
- **Profiles and allocations:** edit `PROFILES` (each row of weights must add up to 100 and follow the order of `ASSETS`).
- **Assets and default returns:** edit `ASSETS`.
- **Texts:** edit the `T` object, which holds the Turkish (`tr`) and English (`en`) copy.
- **Colors:** edit the `:root` tokens and the `data-palette` rules at the top of the file.

Fonts (Bricolage Grotesque, IBM Plex Sans, IBM Plex Mono) load from Google Fonts, with system fallbacks.

### Disclaimer

This tool is for general information and education and is not investment advice. Personalized advice is provided by licensed institutions. Scenarios carry no return guarantee, and past performance does not indicate future results. Read fund prospectuses and product terms before deciding.

---

## Türkçe

Robo Danışman, Türkiye'deki tasarruf sahipleri için hazırlanmış tek sayfalık bir robo danışmandır. Altı soru sorar, bir risk profili belirler ve parayı vadeli mevduat, para piyasası fonu, borçlanma araçları fonu, hisse senedi fonu, altın, gümüş ve döviz arasında nasıl paylaştırabileceğinizi önerir. Ardından yatırım sürenize göre üç getiri senaryosu gösterir.


### Özellikler

- Altı soruluk risk anketi (yaş, süre, %20 değer kaybına tepki, hedef, acil durum birikimi, deneyim).
- Beş profil: çok temkinli, temkinli, dengeli, büyüme odaklı, atak.
- Dağılım halka grafiği ve varlık bazında TL tutarları gösteren liste.
- 1, 3, 5 veya 10 yıl için kötü, beklenen ve iyi senaryo grafiği. Aylık ek yatırım ve enflasyona göre bugünkü alım gücü de hesaplanır.
- Türkçe / English seçimi, dört vurgu rengi (turkuaz, indigo, gül, grafit) ve açık / koyu tema. Seçimleriniz tarayıcıda hatırlanır.
- Telefonda ve masaüstünde çalışır. Sunucu yok, hesap yok, veri sayfadan dışarı çıkmaz.

### Nasıl çalışır

1. Her cevap 1 ile 4 arasında puan alır. Altı puan toplanır (aralık 6–24).
2. Toplam profili belirler: 9'a kadar çok temkinli, 10–13 temkinli, 14–17 dengeli, 18–21 büyüme odaklı, 22 ve üzeri atak.
3. Her profilin sabit bir dağılımı vardır (betikteki `PROFILES`).
4. İki güvenlik kuralı dağılımı değiştirir:
   - Vade 1 yıl ise hisse ve gümüşün tamamı para piyasası fonuna aktarılır.
   - Acil durum birikimi yoksa hisse ve gümüşten en fazla 10 puan para piyasası fonuna aktarılır.
5. Beklenen getiri, her varlığın yıllık getirisinin ağırlıklı ortalamasıdır. Kötü ve iyi senaryo, her varlığın oynaklığını çıkarır veya ekler ve tüm varlıkların aynı anda aynı yönde gittiğini varsayar. Gerçekte öyle olmaz, bu yüzden gerçek aralık daha dardır.

### Varsayılan varsayımlar (örnektir, tahmin değildir)

| Varlık | Getiri %/yıl | Oynaklık % |
|---|---|---|
| Vadeli mevduat | 38 | 1 |
| Para piyasası fonu | 40 | 1 |
| Borçlanma araçları fonu | 42 | 6 |
| Hisse senedi fonu | 55 | 30 |
| Altın | 45 | 18 |
| Gümüş | 50 | 30 |
| Döviz | 25 | 12 |
| Enflasyon | 30 | yok |

Bu rakamları yazar seçmiştir, güncel piyasa verisinden alınmamıştır. Sayfadaki "Getiri varsayımlarını düzenle" bölümünden ya da betikteki `ASSETS` içinden değiştirin ve güncel mevduat faizinizi, fon getirilerinizi kullanın.

### Özelleştirme

Her şey tek dosyadadır: `robo-danisman.html`.

- **İsim:** `<title>`, iki dildeki `kicker` metinleri ve `oranla-*` saklama anahtarlarını değiştirin.
- **Profiller ve dağılımlar:** `PROFILES` içini düzenleyin (her ağırlık satırı 100 etmeli ve `ASSETS` sırasını izlemelidir).
- **Varlıklar ve varsayılan getiriler:** `ASSETS` içini düzenleyin.
- **Metinler:** Türkçe (`tr`) ve İngilizce (`en`) metinleri tutan `T` nesnesini düzenleyin.
- **Renkler:** Dosyanın başındaki `:root` tokenlarını ve `data-palette` kurallarını düzenleyin.

Yazı tipleri (Bricolage Grotesque, IBM Plex Sans, IBM Plex Mono) Google Fonts'tan yüklenir, sistem yazı tipleri yedek olarak tanımlıdır.

### Yasal uyarı

Bu araç genel bilgilendirme ve eğitim amaçlıdır, yatırım danışmanlığı değildir. Kişiye özel danışmanlık yetkili kuruluşlarca verilir. Senaryolar getiri garantisi taşımaz, geçmiş performans gelecekteki sonuçların göstergesi değildir. Karar vermeden önce fon izahnamelerini ve ürün koşullarını inceleyin.

