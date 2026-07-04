<div align="center">

# 🎭 OverLayna

### 📖 Penerjemah Real-Time untuk Komik & Manga

[![Android](https://img.shields.io/badge/Platform-Android-3DDC84?style=for-the-badge&logo=android)](https://developer.android.com)
[![Kotlin](https://img.shields.io/badge/Language-Kotlin-7F52FF?style=for-the-badge&logo=kotlin)](https://kotlinlang.org)
[![Jetpack Compose](https://img.shields.io/badge/UI-Jetpack%20Compose-4285F4?style=for-the-badge)](https://developer.android.com/jetpack/compose)

<img alt="OverLayna Banner" src="https://raw.githubusercontent.com/frostyxsec/OverLayna/refs/heads/main/OverLayna.png" />

</div>

---

## 📱 Tentang OverLayna

**OverLayna** adalah aplikasi Android yang menerjemahkan teks pada komik, manga, atau buku komik secara **real-time** menggunakan fitur screenshot/overlay layar. Teks terjemahan ditampilkan langsung di atas bubble dialog asli dengan tampilan yang rapi dan presisi.

### ✨ Fitur Utama

| Fitur | Deskripsi |
|---|---|
| 🖼️ **Screenshot & Terjemah** | Tangkap layar dan langsung terjemahkan semua teks |
| 🔄 **Overlay Real-Time** | Terjemahan muncul di atas bubble dialog asli |
| 🧠 **AI OCR Correction** | AI mengoreksi error OCR sambil menerjemahkan |
| 🌍 **Multi-Bahasa** | Mendukung Jepang, Korea, Cina, dan lainnya |
| 🎯 **Multi-Provider AI** | Pilih Gemini, OpenCode Zen, atau DeepL |
| 💾 **Riwayat** | Simpan dan lihat terjemahan sebelumnya |

---

## 🤖 Provider AI

OverLayna mendukung **3 provider AI** untuk terjemahan:

### 🟢 Google Gemini

| Model | Kecepatan | Kualitas |
|---|---|---|
| `gemini-2.5-flash` | ⚡⚡⚡ | ⭐⭐⭐ |
| `gemini-2.5-pro` | ⚡⚡ | ⭐⭐⭐⭐ |
| `gemini-3.5-flash` | ⚡⚡⚡ | ⭐⭐⭐ |
| `gemini-2.5-flash-lite` | ⚡⚡⚡⚡ | ⭐⭐ |
| `gemini-3.1-flash-lite` | ⚡⚡⚡⚡ | ⭐⭐ |

- ✅ OCR + Terjemahan
- ✅ Koreksi error otomatis
- 🔑 Dapatkan API key di [Google AI Studio](https://aistudio.google.com/app/apikey)

### 🔵 OpenCode Zen

| Model | Deskripsi |
|---|---|
| `mimo-v2.5-free` | Model default, gratis |

- ✅ OCR + Terjemahan
- ✅ Koreksi error otomatis
- 📝 Model bisa diisi manual (provider sering update)
- 🔑 Dapatkan API key di [OpenCode](https://opencode.ai)

### 🟣 DeepL

| Jenis | URL |
|---|---|
| Free | `api-free.deepl.com` |
| Pro | `api.deepl.com` |

- ⚠️ **Terjemahan saja** (tanpa OCR correction)
- 🔑 Dapatkan API key di [DeepL](https://www.deepl.com/pro-api)
- 💡 API key berakhiran `:fx` = Free, selain itu = Pro

---

## 🛠️ Teknologi

| Komponen | Teknologi |
|---|---|
| 🖥️ UI Framework | Jetpack Compose + Material 3 |
| 🧩 Architecture | MVVM + ViewModel |
| 🗄️ Database | Room (riwayat terjemahan) |
| 🔌 Networking | OkHttp + Moshi (JSON) |
| 🔍 OCR | Google ML Kit Text Recognition |
| 🎯 Koordinat | Google Vision normalized (0-1000) |

---

## ⚙️ Cara Pakai

### 1️⃣ Aktifkan Overlay

Setelah membuka aplikasi, tap tombol **"Aktifkan Overlay"** untuk memulai layanan screenshot.

### 2️⃣ Pilih Provider

Buka menu **⚙️ Pengaturan** dan pilih provider AI:

- **Google Gemini** → Masukkan API key, pilih model
- **OpenCode Zen** → Masukkan API key, ketik model (default: `mimo-v2.5-free`)
- **DeepL** → Masukkan API key (auto-detect Free/Pro)

### 3️⃣ Validasi API Key

Tap tombol **"Validasi"** untuk memastikan API key berfungsi.

### 4️⃣ Terjemahkan!

Buka komik favorit, screenshot layar, dan OverLayna akan menampilkan terjemahan secara otomatis! 🎉

---

## 🏗️ Build dari Source

### Prasyarat

## 🔐 Keamanan API Key

- 🔑 API key disimpan secara lokal di perangkat (SharedPreferences)
- ❌ Tidak ada data yang dikirim ke server pihak ketiga
- 🚫 API key tidak dibagikan atau di-cache
- 🗑️ Fitur **"Hapus Semua"** untuk menghapus semua data pengaturan

---

## 🐛 Known Issues & Troubleshooting

| Masalah | Solusi |
|---|---|
| 🔴 API key tidak valid | Pastikan API key benar dan aktif |
| 🟡 Bubble tidak muncul | Coba screenshot ulang, pastikan bubble terlihat jelas |
| 🟡 Teks bergeser | Pastikan resolusi layar stabil |
| 🔵 Overlay tidak muncul | Berikan izin overlay di pengaturan sistem |
| ⚫ APK terlalu besar | Build release dengan R8 minification |

---

## 📝 Catatan Teknis

### 📐 Sistem Koordinat

OverLayna menggunakan **koordinat normalized (0-1000)** sesuai format Google Vision:

```
X = (x / lebarLayar) × 1000
Y = (y / tinggiLayar) × 1000
```

### 🔍 Clustering Teks

Teks yang berdekatan dikelompokkan menjadi satu bubble:

- **maxXGap**: 200px (jarak horizontal maksimal)
- **maxYGap**: 150px (jarak vertikal maksimal)

### 🔄 Pipeline Terjemahan

```
Screenshot → ML Kit OCR → AI Provider → Koordinat Normalisasi → Overlay
     ↓              ↓              ↓
   Bitmap      Teks mentah    Teks terkoreksi + diterjemahkan
```

---

## 📄 Lisensi

MIT License - Silakan gunakan dan modifikasi sesuai kebutuhan.

---

<div align="center">

### 🎉 Dibuat dengan ❤️ untuk komunitas pembaca komik

**OverLayna** — *Membaca komik dalam bahasa apapun* 🌏

</div>
