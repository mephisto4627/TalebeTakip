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

`_sablon.html` ortak şablondur; sınıf dosyaları bundan üretilir (fark: `<title>` ve
`window.SINIF_KODU` satırı). Şablonda değişiklik yapılırsa 6 klasöre yeniden üretilir.

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
