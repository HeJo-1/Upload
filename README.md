# Upload Tool

Bu araç, belirli web sitelerindeki dosya yükleme (upload) formlarını otomatik olarak kullanarak HTML dosyalarını yüklemenizi ve sonuç URL'lerini toplamanızı sağlar. İki farklı modda çalışır: ön tanımlı siteler (`-sd`) ve istediğiniz site (`-ws`).

---

## Özellikler

- Firefox tarayıcısı üzerinden Selenium ile otomatik dosya yükleme
- Tek seferde birden fazla dosya yükleme desteği
- Yüklenen dosyaların URL'lerini otomatik alma
- URL'leri `urls.txt` dosyasına kaydetme seçeneği
- Renkli ve kullanıcı dostu terminal arayüzü
- Tkinter ile dosya seçici (file dialog)

---

## Gereksinimler

- **Python 3.x**
- **Firefox Tarayıcısı** (kurulu olmalı)
- **Geckodriver** (Firefox için Selenium sürücüsü — PATH'e eklenmiş olmalı)

### Python Kütüphaneleri

```bash
pip install selenium
pip install pyarmor
```

> `tkinter` genellikle Python ile birlikte gelir. Eğer eksikse sisteminize göre kurmanız gerekebilir.

---

## Kurulum

1.
```bash
git clone https://github.com/HeJo-1/Upload
cd Upload
```
2. Gerekli kütüphaneleri yükleyin:

```bash
pip install selenium
```

3. Firefox ve Geckodriver'ın kurulu olduğundan emin olun.
4. Terminalde script'i çalıştırın.
   ```bash
   python main.py
   ```

---

## Kullanım

### 1. Yardım Menüsünü Görmek

```bash
python main.py --help
```

---

### 2. Kayıtlı Siteler ile Upload (`-sd` modu)

Bu modda iki hazır test sitesi kullanılır:

- **Site 1:** `http://www.lsh-hotel.com/kindeditor/examples/uploadbutton.html`
- **Site 2:** `http://47.92.155.250/html/js/kindeditor/examples/uploadbutton.html`

```bash
python main.py -sd
```

**Adımlar:**

1. Site seçin `[1/2]`
2. Kaç tane dosya yükleneceğini girin
3. Onaylamak için Enter'a basın
4. Açılan pencereden yüklemek istediğiniz `.html` dosyasını seçin
5. İşlem otomatik olarak tekrarlanır
6. İsterseniz linkler `urls.txt` dosyasına kaydedilir

---

### 3. Kendi Sitenizi Belirterek Upload (`-ws` modu)

Herhangi bir site için özelleştirilmiş upload yapmak isterseniz:

```bash
python main.py -ws
```

**Girmeniz Gereken Bilgiler:**

| Alan | Açıklama | Örnek |
|------|----------|-------|
| Site linki | Yükleme sayfasının URL'si | `https://ornek.com/upload` |
| Dosya input XPath | File input elementinin XPath'i | `//input[@type='file']` |
| Sonuç URL XPath | Yükleme sonrası çıkan linkin XPath'i | `//*[@id="url"]` |
| Dosya sayısı | Kaç dosya yükleneceği | `10` |

---

## Örnek Kullanım Akışı

1. Terminali açın
2. `python main.py -sd` yazın
3. Site numarasını seçin (`1` veya `2`)
4. Tekrar sayısını girin (örn: `10`)
5. Enter'a basın
6. HTML dosyanızı seçin
7. İşlemin bitmesini bekleyin
8. Linkleri kaydetmek isteyip istemediğinizi belirtin

---

## Notlar ve Uyarılar

> ⚠️ **Yasal Uyarı:** Bu araç yalnızca **yetkiniz olan sitelerde** veya **test amaçlı** olarak kullanılmalıdır. Başkalarına ait sistemlere izinsiz yükleme yapmak **yasa dışıdır**.

- Script her döngüde yeni bir sayfa açar ve yükleme işlemini gerçekleştirir.
- Bazı sitelerde Cloudflare, CAPTCHA veya güvenlik önlemleri nedeniyle çalışmayabilir.
- XPath'ler site yapısına göre değişebilir. Tarayıcınızın geliştirici araçlarını (`F12`) kullanarak doğru XPath'i bulabilirsiniz.
- `urls.txt` dosyası mevcutsa linkler eklenir (append modu).

---

## Lisans

Bu araç **eğitim ve test amaçlı** geliştirilmiştir. Sorumluluk kullanıcıya aittir.
