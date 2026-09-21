# MyMall feed

MyMall uygulamasının **kampanya/etkinlik beslemesi**. Bu depodaki dosyalar elle
düzenlenmez: MyMall deposundaki `feed` iş akışı her gün AVM'lerin kendi
etkinlik/kampanya sayfalarını gezer ve sonucu buraya yazar.

## campaigns.json

```jsonc
{
  "generatedAt": "2026-09-21T12:09:50+00:00",   // üretim zamanı (UTC)
  "campaigns": [
    {
      "id": "kitap-festivali",                   // AVM içinde tekil slug
      "mallId": "kozzy",                         // MyMall AVM kimliği
      "title": "Kitap Festivali",
      "kind": "event",                           // event | discount
      "isPaid": false,
      "image": "https://.../event/....webp",     // AVM sitesindeki görsel
      "description": "…",
      "url": "https://.../tr/etkinlikler-kampanyalar/kitap-festivali",
      "startsAt": "2026-09-12"                   // biliniyorsa
    }
  ]
}
```

Uygulama bu dosyayı `CampaignRepository` ile okur: **uzak JSON → Hive cache →
uygulamayla gelen asset**. Yani ağ yoksa son çekilen veri, hiç çekilmediyse
sürümle gelen yedek kullanılır.

Kullanılan adres:

```
https://raw.githubusercontent.com/<kullanici>/mymall-feed/main/campaigns.json
```

## İçerik

Veriler AVM'lerin herkese açık web sayfalarından derlenir; görseller indirilmez,
kaynak adresleriyle gösterilir. Kapsam şu an Rönesans Gayrimenkul portföyündeki
AVM'lerdir (Maltepe Piazza, Maltepe Park, Kozzy, Hilltown, İstanbul Optimum).
