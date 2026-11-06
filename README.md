# Stampport — web sitesi

[Stampport](https://github.com/nodabasi/stampport) mobil uygulamasının tanıtım ve destek
sitesi. Mağazaların istediği **destek**, **gizlilik politikası** ve **hesap silme**
bağlantıları buradan verilir. GitHub Pages ile yayında:
<https://nodabasi.github.io/stampport-app/>

Statik HTML ve tek bir CSS dosyası; derleme adımı, bağımlılık ve JavaScript yok.

## Sayfalar

Uygulama Türkçe ve İngilizce olduğu için site de iki dilli: Türkçe kökte, İngilizce `/en/`
altında. Her sayfa `hreflang` ile diğer dildeki karşılığını gösterir.

| Türkçe | İngilizce | Nerede kullanılır |
| --- | --- | --- |
| `/` | `/en/` | Mağaza listesindeki pazarlama adresi |
| `/destek/` | `/en/support/` | App Store Connect → Destek adresi |
| `/gizlilik/` | `/en/privacy/` | App Store Connect ve Play Console → Gizlilik politikası |
| `/hesap-silme/` | `/en/delete-account/` | Play Console → Hesap silme adresi |

**Bu dizinlerin adını değiştirme.** Mağazalara kaydedildikten sonra değişen yol canlı
bağlantıyı kırar.

## Yerelde bakmak

```bash
python3 -m http.server 8000
```

Bağlantılar göreli olduğu için site hangi alt dizinde olursa olsun çalışır.

## Güncellenmesi gerekenler

- **İletişim adresi:** `odabasi.developer@gmail.com` bütün sayfalarda geçiyor.
- **Yürürlük tarihi:** `gizlilik/` ve `en/privacy/` içindeki `.meta` satırı.
- **Mağaza bağlantıları:** iki ana sayfadaki HTML yorumunun yerine eklenecek.
- **Telif yılı:** alt bilgilerde.

## Site ile uygulama arasındaki bağ

Gizlilik ve hesap silme sayfaları uygulamanın bugünkü davranışını anlatır. Şunlar
değişirse sayfalar da güncellenmeli:

- buluta giden alanlar (`app/src/sync/records.ts`, `app/src/types`)
- kimin neyi görebildiği (`app/firestore.rules`)
- giriş yöntemleri (e-posta/şifre ve Google) ve hesap silmenin kapsamı (`app/src/store/useAuthStore.ts`)
- verinin tutulduğu bölge (Firestore `eur3`)
- reklam, analitik ya da hata takibi eklenirse "toplamadığımız bilgiler" bölümü
