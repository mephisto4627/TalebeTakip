# Talebe Takip — Sınıf Siteleri

Kur'an kursu öğrenci takip sistemi. Her klasör bir sınıfın sitesidir; hepsi aynı merkezi
Google Apps Script'e bağlanır ve her sınıf kendi Google E-Tablosuna yazar.

| Klasör | Sınıf |
|---|---|
| `bagdat/` | Bağdat |
| `endulus/` | Endülüs |
| `gazze/` | Gazze |
| `kudus/` | Kudüs |
| `medine/` | Medine |
| `mekke/` | Mekke |
| `nurdag/` | Nurdağ (bağımsız — bkz. aşağı) |

`_sablon.html` ortak şablondur; sınıf dosyaları bundan üretilir (fark: `<title>` ve
`window.SINIF_KODU` satırı). Şablonda değişiklik yapılırsa 6 klasöre yeniden üretilir.

**`nurdag/` istisnadır:** başka bir Google hesabında, kendi Apps Script'ine ve kendi
E-Tablosuna bağlanır (merkezi script'i kullanmaz). `_sablon.html`'den türetildi ama
`scriptUrl` kendine ait. Şablon güncellenirse `nurdag/index.html`'e elle taşınmalı
(otomatik yeniden üretime dahil değil). Kendi `Code.gs`'i `nurdag/Code.gs`'te saklanır —
gerçek script bu dosyanın bir kopyasıdır, Apps Script editöründen elle güncellenir.

## Vercel kurulumu (her sınıf için bir kez)

1. vercel.com → **Add New… → Project** → bu repoyu içe aktar.
2. **Root Directory** alanına sınıf klasörünü yaz (örn. `bagdat`).
3. Framework: **Other**, build ayarı gerekmez (statik).
4. Deploy → proje ayarlarından **Domains** ile sınıfın alan adını bağla.
5. Diğer 5 sınıf için tekrarla (aynı repo, farklı Root Directory).

## Arka plan

Merkezi Apps Script `kurs2-talebe-takip` reposundaki `apps-script/Code.gs` dosyasından
yönetilir. Yeni sınıf eklemek: E-Tablo ID'sini `SINIFLAR` haritasına ekle, yeni sürüm
deploy et, editörden `tetikleyicileriKur()` fonksiyonunu bir kez çalıştır.

## Nurdağ kurulumu (bağımsız hesap)

1. Nurdağ E-Tablosunu aç → `Uzantılar > Apps Script`.
2. `nurdag/Code.gs` içeriğinin tamamını yapıştır.
3. `Deploy > New deployment > Web app`: Execute as `Me`, Access `Anyone with the link`.
4. Editörden `tetikleyicileriKur()` fonksiyonunu bir kez çalıştır (elle Excel düzenlemesi anında yansısın).
5. Verilen `/exec` adresini `nurdag/index.html` içindeki `scriptUrl` alanına yapıştır.
6. Vercel: **Add New… → Project** → bu repo → Root Directory `nurdag` → deploy.
