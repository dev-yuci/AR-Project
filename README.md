<div align="center">

<img src="https://img.shields.io/badge/Unity-6-000000?style=for-the-badge&logo=unity&logoColor=white"/>
<img src="https://img.shields.io/badge/AR_Foundation-ARCore%20%7C%20ARKit-00B4D8?style=for-the-badge"/>
<img src="https://img.shields.io/badge/C%23-239120?style=for-the-badge&logo=c-sharp&logoColor=white"/>
<img src="https://img.shields.io/badge/Platform-Android%20%7C%20iOS-lightgrey?style=for-the-badge"/>
<img src="https://img.shields.io/badge/Status-Prototype-orange?style=for-the-badge"/>

<br/><br/>

# 🌊 OceanLens AR

### *Dijital Deniz Biyolojisi ve Ekosistem Eğitim Platformu*

> **"Görmediğini koruyamazsın."**

Telefonunu odasının zeminine tut — saniyeler içinde yanında bir **İmparator Melek Balığı** yüzmeye başlasın. OceanLens AR, kentsel yaşamın okyanustan kopardığı bireyleri teknolojiyle yeniden denizle buluşturan bir Artırılmış Gerçeklik eğitim platformudur.

<br/>

[![GitHub](https://img.shields.io/badge/github-dev--yuci%2FAR--Project-181717?style=flat-square&logo=github)](https://github.com/dev-yuci/AR-Project)
[![Trello](https://img.shields.io/badge/Trello-Project_Board-0052CC?style=flat-square&logo=trello)](https://trello.com/invite/b/69a924c87497473606005940/ATTIafaf1e7dd20c59c88bbc0d0108d54106225A40B7/project-management)

</div>

---

## 📖 İçindekiler

- [Proje Hakkında](#-proje-hakkında)
- [Özellikler](#-özellikler)
- [Teknik Mimari](#-teknik-mimari)
- [RAMS Analizi](#-rams-analizi)
- [Kurulum](#-kurulum)
- [Kullanım](#-kullanım)
- [Proje Yapısı](#-proje-yapısı)
- [Yol Haritası](#-yol-haritası)
- [Geliştirici](#-geliştirici)

---

## 🐠 Proje Hakkında

OceanLens AR, modern şehir hayatının betonlaşmış sınırları içinde yaşayan bireylerin okyanusla olan bağını yeniden kurmayı hedefleyen bir **EdTech (Eğitim Teknolojileri)** projesidir.

Uygulama, kullanıcının fiziksel çevresini anlık olarak **yaşayan bir dijital resife** dönüştürür. Gerçek ölçeklerde (`1:1`) render edilen deniz canlıları, kullanıcının kendi odasında yüzer; etrafında tur atılabilir, milimetrik mesafeye kadar yaklaşılabilir.

### Hedeflenen Sektörler
| Sektör | Kullanım Senaryosu |
|--------|-------------------|
| 🎓 **Eğitim (EdTech)** | Sınıf içi interaktif deniz biyolojisi dersleri |
| 🏛️ **Dijital Müzecilik** | Akvaryum ve bilim merkezleri için AR sergileri |
| 🌱 **Çevre Farkındalığı** | NGO kampanyaları, WWF gibi kuruluşlar için içerik |
| 🏥 **Rehabilitasyon** | Çocuk hastanelerinde terapötik kullanım |

---

## ✨ Özellikler

- 🐟 **Gerçek Ölçek (1:1)** — Deniz canlıları gerçek boyutlarıyla odanıza konuk olur
- 📍 **Kararlı AR Sabitleme** — Anchor sistemi ile sanal nesneler fiziksel dünyaya kilitlenir; titreme/kayma yaşanmaz
- 📶 **Offline-First** — İnternet bağlantısı gerektirmez; okul ve uzak ortamlarda tam performans
- 🔒 **Gizlilik Önce** — Kamera verisi hiçbir sunucuya gönderilmez; tamamen cihaz üzerinde işlenir (On-Device Processing)
- 📱 **Çapraz Platform** — Android (ARCore) ve iOS (ARKit) desteği
- ♾️ **Genişletilebilir İçerik** — Prefab tabanlı mimari; yeni türler merkezi kodu bozmadan eklenir

---

## 🏗️ Teknik Mimari

```
OceanLens AR
├── Motor          → Unity 6
├── AR Framework   → AR Foundation (ARCore / ARKit)
├── Dil            → C# (SOLID prensipleri, modüler yapı)
├── Render         → OpenGL ES3, Low-Poly + Özel Shader
├── Takip          → SLAM (6DoF) + Raycast Manager
├── Sensörler      → Kamera, İvmeölçer, Jiroskop
└── Sürüm Kontrol  → GitHub
```

### Çalışma Akışı

```
Kamera Akışı
     │
     ▼
SLAM (Eşzamanlı Konumlandırma & Haritalama)
     │
     ▼
Zemin Algılama (Plane Detection)
     │
     ▼
Anchor Oluşturma  ──►  Sanal Nesne Spawn
     │
     ▼
Raycast Manager (Kullanıcı Etkileşimi)
     │
     ▼
Animasyon Döngüsü + FPS Stabilizasyonu (≥30 FPS)
```

---

## 🔬 RAMS Analizi

| Boyut | Uygulanan Yöntem | Durum |
|-------|-----------------|-------|
| **Reliability** (Güvenilirlik) | C# Exception Handling, Anchor stabilizasyonu, asenkron veri işleme | ✅ |
| **Availability** (Kullanılabilirlik) | Asynchronous Loading, Offline-First mimari, çapraz platform destek | ✅ |
| **Maintainability** (Bakım) | SOLID prensipleri, Prefab tabanlı yönetim, GitHub sürüm kontrolü | ✅ |
| **Safety** (Güvenlik) | Fiziksel sınır uyarıları, On-Device Processing, kısıtlı izin erişimi | ✅ |

---

## 🚀 Kurulum

### Gereksinimler

- Unity **6.x** veya üzeri
- AR Foundation paketi (`com.unity.xr.arfoundation`)
- **Android:** ARCore destekli cihaz (Android 7.0+), ARCore XR Plugin
- **iOS:** ARKit destekli cihaz (iOS 11+, A9 çip+), ARKit XR Plugin

### Adımlar

```bash
# 1. Repoyu klonla
git clone https://github.com/dev-yuci/AR-Project.git

# 2. Unity Hub ile aç
# File > Open Project > klonladığın klasörü seç

# 3. Bağımlılıkları yükle
# Window > Package Manager > AR Foundation + ilgili platform plugin

# 4. Build ayarları
# File > Build Settings > Android veya iOS seç > Switch Platform
```

### APK Build (Android)

```
File > Build Settings > Android
Player Settings:
  - Minimum API Level: Android 7.0 (API 24)
  - Graphics API: OpenGL ES3
  - ARCore: Required
Build > APK dosyasını cihaza yükle
```

---

## 📱 Kullanım

1. Uygulamayı başlat
2. **Güvenlik uyarısını** oku ve etrafında yeterli alan olduğundan emin ol
3. Telefonu **zemine doğru tut** — sistem yüzeyi tarar (birkaç saniye)
4. Yeşil ışık belirince **ekrana dokun** — balık spawn olur
5. Yavaşça hareket ederek balığın etrafında **tur at**, yaklaş, incele 🐠

---

## 📁 Proje Yapısı

```
AR-Project/
├── Assets/
│   ├── Models/          # Low-poly deniz canlısı modelleri
│   ├── Shaders/         # Özel su ve balık shader'ları
│   ├── Prefabs/         # Spawn edilebilir varlıklar
│   ├── Scripts/
│   │   ├── ARManager.cs        # AR oturumu yönetimi
│   │   ├── PlaneDetector.cs    # Zemin algılama
│   │   ├── SpawnController.cs  # Nesne spawn sistemi
│   │   └── AnimationLoop.cs    # Yüzme animasyonları
│   └── Scenes/
│       └── MainScene.unity
├── Packages/
│   └── manifest.json
└── ProjectSettings/
```

---

## 🗺️ Yol Haritası

- [x] Unity 6 + AR Foundation altyapısı
- [x] SLAM tabanlı zemin algılama
- [x] İmparator Melek Balığı modeli + animasyon
- [x] APK prototip çıktısı
- [ ] 🔊 Sesli rehber (türe özel anlatım)
- [ ] 📋 İnteraktif bilgi panelleri (dokunarak aç)
- [ ] 🌐 Shared AR — birden fazla kullanıcı aynı balığı görür
- [ ] 🐙 Yeni tür paketi (ahtapot, köpek balığı, denizanası...)
- [ ] 💡 Gerçek dünya ışığına uyumlu dinamik aydınlatma
- [ ] 🎨 UI/UX revizyonu

---

## 👨‍💻 Geliştirici

**Yusuf Aytaş**
`220542015` — Yazılım Mühendisliği Güncel Konular

[![GitHub](https://img.shields.io/badge/GitHub-dev--yuci-181717?style=flat-square&logo=github)](https://github.com/dev-yuci)

---

<div align="center">

*"Teknoloji, doğayla yeniden bağ kurmamızı sağlayan bir farkındalık penceresidir."*

**🌊 OceanLens AR — Okyanusu Odanıza Taşıyın**

</div>
