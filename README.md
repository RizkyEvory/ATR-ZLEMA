# ⚡ ATR ZLEMA + EMA34 PRO

<div align="center">

![Version](https://img.shields.io/badge/version-2.0-gold?style=for-the-badge)
![Platform](https://img.shields.io/badge/platform-MetaTrader%205-blue?style=for-the-badge)
![Language](https://img.shields.io/badge/language-MQL5-orange?style=for-the-badge)
![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)
![Optimized](https://img.shields.io/badge/optimized%20for-XAUUSD-FFD700?style=for-the-badge)

**Indikator teknikal premium untuk MetaTrader 5 — menggabungkan ZLEMA (Zero-Lag EMA), ATR Trailing Stop, dan EMA34 Filter dalam satu paket visual yang powerful.**

*Developed by M4DI~UciH4 · [github.com/RizkyEvory](https://github.com/RizkyEvory)*

</div>

---

## 📋 Daftar Isi

- [Tentang Indikator](#-tentang-indikator)
- [Fitur Utama](#-fitur-utama)
- [Cara Instalasi](#-cara-instalasi)
- [Parameter Input](#-parameter-input)
- [EMA Confirmation Mode](#-ema-confirmation-mode)
- [Color Themes](#-color-themes)
- [Cara Membaca Sinyal](#-cara-membaca-sinyal)
- [Optimasi untuk XAUUSD](#-optimasi-untuk-xauusd)
- [Dashboard Info Panel](#-dashboard-info-panel)
- [Algoritma & Logika](#-algoritma--logika)
- [FAQ](#-faq)

---

## 🧠 Tentang Indikator

**ATR ZLEMA + EMA34 PRO v2.0** adalah indikator tren berbasis chart yang menggabungkan tiga komponen inti:

| Komponen | Fungsi |
|---|---|
| **ZLEMA** (Zero-Lag EMA) | EMA yang dimodifikasi untuk mengurangi lag, memberikan respons lebih cepat terhadap pergerakan harga |
| **ATR Trailing Stop** | Trailing stop dinamis berbasis volatilitas (ATR) yang mengikuti tren secara adaptif |
| **EMA34 Filter** | Filter konfirmasi tren sebagai layer validasi sinyal tambahan |

Indikator ini dirancang khusus untuk **XAUUSD (Gold)** namun dapat digunakan di instrumen lain dengan penyesuaian parameter.

---

## ✨ Fitur Utama

### 🎯 Core Features
- **ZLEMA Line** — Zero-Lag EMA dengan noise filter berbasis ATR, tampil berwarna sesuai arah tren
- **ATR Trailing Stop** — Stop adaptif yang ratchet naik (bullish) atau turun (bearish) secara otomatis
- **EMA34 Filter** — 3 mode konfirmasi berbeda untuk menyesuaikan sensitivitas sinyal
- **MTF (Multi-Timeframe) Filter** — Konfirmasi tren dari timeframe yang lebih tinggi

### 📊 Visual Features
- **Cloud Fill** — Area fill antara ZLEMA dan ATR Trail, berwarna sesuai tren
- **Bar Coloring** — Candle diwarnai otomatis mengikuti arah tren dengan transparansi yang bisa diatur
- **Signal Arrows** — Panah buy/sell muncul saat terjadi trend flip yang dikonfirmasi
- **Glow Effect** — Efek glow 3 layer pada sinyal untuk visibilitas lebih baik
- **6 Color Presets** + Custom — Pilih tema warna sesuai selera, termasuk tema Gold khusus XAUUSD

### 🖥️ Dashboard
- Info panel real-time berisi: status tren, nilai ZLEMA, ATR Trail, EMA, ATR
- Status filter EMA dan MTF (Long/Short)
- Waktu sinyal terakhir (Buy & Sell)
- Konfigurasi & versi indikator
- Desain premium dark-UI dengan gold accent

---

## 💾 Cara Instalasi

1. **Download** file `ATR_ZLEMA_EMA34_PRO.mq5`

2. **Buka** MetaEditor di MetaTrader 5:
   - Tekan `F4` pada MT5, atau
   - Klik **Tools → MetaQuotes Language Editor**

3. **Copy file** ke direktori indikator:
   ```
   [Data Folder MT5]\MQL5\Indicators\
   ```
   > Untuk menemukan Data Folder: di MT5, klik **File → Open Data Folder**

4. **Compile** script di MetaEditor:
   - Buka file `ATR_ZLEMA_EMA34_PRO.mq5`
   - Tekan `F7` untuk compile
   - Pastikan tidak ada error di tab "Errors"

5. **Pasang ke chart**:
   - Di MT5, buka tab **Navigator** (Ctrl+N)
   - Expand **Indicators → Custom**
   - Drag & drop `ATR_ZLEMA_EMA34_PRO` ke chart yang diinginkan

---

## ⚙️ Parameter Input

### ════ ATR ZLEMA Core ════

| Parameter | Default | Deskripsi |
|---|---|---|
| `Price Source` | Close | Harga yang digunakan sebagai input (Close/Open/High/Low/Median/Typical/Weighted) |
| `ZLEMA Length` | 14 | Periode ZLEMA. H1→14, M15→10, H4→20 |
| `ATR Length` | 14 | Periode ATR untuk kalkulasi band volatilitas |
| `ATR Multiplier` | 3.5 | Pengali ATR untuk lebar trailing stop. **XAUUSD: 2.5–4.0** |
| `Enable Noise Filter` | true | Aktifkan filter noise untuk mencegah whipsaw |
| `Noise Threshold` | 0.3 | Ambang batas noise dalam satuan ATR. **XAUUSD: 0.2–0.4** |

### ════ EMA34 Filter ════

| Parameter | Default | Deskripsi |
|---|---|---|
| `EMA Length` | 34 | Periode EMA (bisa diubah, default 34 karena cocok untuk XAUUSD) |
| `EMA Confirmation Mode` | Mode A | Lihat bagian [EMA Confirmation Mode](#-ema-confirmation-mode) |

### ════ MTF Confirmation ════

| Parameter | Default | Deskripsi |
|---|---|---|
| `Enable MTF Filter` | false | Aktifkan filter konfirmasi multi-timeframe |
| `MTF Timeframe` | H1 | Timeframe lebih tinggi untuk konfirmasi. Contoh: gunakan H4 saat trading di H1 |

### ════ Visuals — Rainbow ════

| Parameter | Default | Deskripsi |
|---|---|---|
| `Color Theme` | PRESET_GOLD | Tema warna (lihat bagian [Color Themes](#-color-themes)) |
| `Custom Bull Color` | Lime | Warna bullish untuk mode Custom |
| `Custom Bear Color` | Red | Warna bearish untuk mode Custom |
| `Cloud Fill Transparency` | 75 | Transparansi cloud fill (0 = solid, 100 = invisible) |
| `Bar Color Transparency` | 65 | Transparansi warna candle |
| `Enable Bar Coloring` | true | Warnai candle sesuai tren |
| `ZLEMA Line Width` | 2 | Ketebalan garis ZLEMA (1–5) |
| `Trail Line Width` | 3 | Ketebalan garis ATR Trail (1–5) |

### ════ Visuals — Signals ════

| Parameter | Default | Deskripsi |
|---|---|---|
| `Show Signal Arrows` | true | Tampilkan panah sinyal buy/sell |
| `Enable Glow Effect` | true | Aktifkan efek glow 3 layer pada sinyal |
| `Show EMA34 Line` | true | Tampilkan garis EMA34 di chart |
| `Show Cloud Fill` | true | Tampilkan cloud fill antara ZLEMA dan Trail |

### ════ Dashboard ════

| Parameter | Default | Deskripsi |
|---|---|---|
| `Show Dashboard` | true | Tampilkan info panel |
| `Position` | Upper Left | Sudut posisi dashboard |
| `X Offset` | 10 | Jarak horizontal dari sudut (pixels) |
| `Y Offset` | 25 | Jarak vertikal dari sudut (pixels) |
| `Font Size` | 9 | Ukuran font dashboard |

---

## 🎛️ EMA Confirmation Mode

Tiga mode ini mengontrol bagaimana EMA34 memvalidasi sinyal. Pilih sesuai gaya trading:

### Mode A — `Price vs EMA` *(Paling Responsif)*
```
Long OK  : Close > EMA34
Short OK : Close < EMA34
```
✅ Cocok untuk scalping dan intraday. Sinyal lebih banyak namun sedikit lebih berisiko noise.

### Mode B — `ZLEMA vs EMA` *(Momentum-Based)*
```
Long OK  : ZLEMA > EMA34
Short OK : ZLEMA < EMA34
```
✅ Keseimbangan antara responsif dan konfirmasi. Rekomendasi untuk kebanyakan setup.

### Mode C — `EMA Slope` *(Paling Smooth)*
```
Long OK  : EMA sedang naik (EMA[now] > EMA[prev])
Short OK : EMA sedang turun (EMA[now] < EMA[prev])
```
✅ Paling konservatif. Cocok untuk swing trading di H4/D1. Sinyal lebih sedikit namun lebih kuat.

---

## 🎨 Color Themes

| Preset | Bull Color | Bear Color | Rekomendasi |
|---|---|---|---|
| `PRESET_CLASSIC` | `#00FF00` (Green) | `#FF0000` (Red) | Chart gelap standar |
| `PRESET_AQUA` | `#00BFFF` (Deep Sky Blue) | `#FF8C00` (Dark Orange) | Dark theme modern |
| `PRESET_COSMIC` | `#49FFCE` (Mint) | `#9932CC` (Purple) | Aesthetic / streaming |
| `PRESET_EMBER` | `#FF6600` (Orange) | `#00CCCC` (Teal) | High contrast |
| `PRESET_NEON` | `#FFFF00` (Yellow) | `#FF00FF` (Magenta) | Neon / cyberpunk |
| `PRESET_GOLD` ⭐ | `#FFD700` (Gold) | `#E040FB` (Violet) | **XAUUSD Special** |
| `PRESET_CUSTOM` | *User defined* | *User defined* | Bebas pilih |

---

## 📖 Cara Membaca Sinyal

### Trend Status
| Kondisi | Artinya |
|---|---|
| ZLEMA & Trail berwarna **Bull** ↑ | Tren Bullish aktif |
| ZLEMA & Trail berwarna **Bear** ↓ | Tren Bearish aktif |
| Cloud di atas Trail | Momentum bullish |
| Cloud di bawah Trail | Momentum bearish |

### Signal Arrows
| Sinyal | Kondisi |
|---|---|
| **▲ BUY** | Tren flip dari Bear→Bull + EMA Filter OK + MTF Filter OK |
| **▼ SELL** | Tren flip dari Bull→Bear + EMA Filter OK + MTF Filter OK |

> **Penting:** Sinyal hanya muncul saat **ketiga kondisi** terpenuhi (ATR Trend Flip + EMA Filter + MTF Filter). Ini meminimalkan false signal.

### Entry Logic
```
BUY  : ATR Trail flip bullish + price/ZLEMA di atas EMA34 + [MTF bullish jika aktif]
SELL : ATR Trail flip bearish + price/ZLEMA di bawah EMA34 + [MTF bearish jika aktif]
```

---

## 🏅 Optimasi untuk XAUUSD

Berikut adalah parameter yang direkomendasikan untuk **XAUUSD**:

### H1 (Intraday)
```
ZLEMA Length  : 14
ATR Length    : 14
ATR Multiplier: 3.0 – 3.5
Noise Threshold: 0.3
EMA Length    : 34
EMA Mode      : Mode A atau B
MTF TF        : H4 (aktifkan)
Color Preset  : PRESET_GOLD
```

### M15 (Scalping)
```
ZLEMA Length  : 10
ATR Length    : 10
ATR Multiplier: 2.5 – 3.0
Noise Threshold: 0.2
EMA Length    : 34
EMA Mode      : Mode A
MTF TF        : H1 (aktifkan)
```

### H4 (Swing)
```
ZLEMA Length  : 20
ATR Length    : 14
ATR Multiplier: 3.5 – 4.0
Noise Threshold: 0.4
EMA Length    : 34
EMA Mode      : Mode B atau C
MTF TF        : D1 (aktifkan)
```

> **Tips XAUUSD:** Gold memiliki volatilitas tinggi (spike sering terjadi). Gunakan `ATR Multiplier` yang lebih besar (3.5+) dan `Noise Threshold` 0.3–0.4 untuk menghindari sinyal palsu akibat spike harga.

---

## 🖥️ Dashboard Info Panel

Dashboard real-time ditampilkan di sudut chart (posisi bisa diatur) dengan informasi berikut:

```
⚡ ATR ZLEMA + EMA34
PRO v2.0  •  M4DI~UciH4
github.com/RizkyEvory
─────────────────────────
📊 MARKET DATA
  Trend        ● BULLISH
  ZLEMA (14)   2345.67
  ATR Trail    2340.12
  EMA 34       2338.50
  ATR (14)     8.45
─────────────────────────
🎯 FILTERS
  EMA Mode     Price vs EMA
  Filter Status L: ✓ | S: ✗
  MTF (H4)     ENABLED
─────────────────────────
🔔 SIGNALS
  Active Signal  ● WAITING
  Last Buy       2024.01.15 10:00
  Last Sell      2024.01.14 16:30
─────────────────────────
ℹ️ INFO
  Symbol       XAUUSD
  Timeframe    H1
  ATR Mult     3.5x
  Noise Thr    0.3x
```

---

## 🔬 Algoritma & Logika

### 1. ZLEMA Calculation
```
lag      = (ZLEMA_Length - 1) / 2
alpha    = 2 / (ZLEMA_Length + 1)
zlema_src = price + (price - price[lag])   // Zero-lag adjustment
zlema    = EMA(zlema_src, alpha)           // Smooth with EMA
```

### 2. Noise Filter
```
IF ABS(zlema_raw - zlema_prev) > ATR * noise_threshold:
    zlema = zlema_raw   // Update allowed
ELSE:
    zlema = zlema_prev  // Hold previous (filter noise)
```
> Filter ini mencegah ZLEMA bergerak jika perubahan terlalu kecil (dianggap noise), kecuali sudah terlalu lama tidak update (> ZLEMA_Length bars).

### 3. ATR Trailing Stop (State Machine)
```
IF trend == BULL:
    IF price < trail:
        trend = BEAR
        trail = price + ATR * multiplier
    ELSE:
        trail = MAX(trail, price - ATR * multiplier)  // Ratchet up

IF trend == BEAR:
    IF price > trail:
        trend = BULL
        trail = price - ATR * multiplier
    ELSE:
        trail = MIN(trail, price + ATR * multiplier)  // Ratchet down
```

### 4. Signal Detection
```
BUY  = (trend flips BEAR→BULL) AND ema_long_ok AND htf_long_ok
SELL = (trend flips BULL→BEAR) AND ema_short_ok AND htf_short_ok
```

---

## ❓ FAQ

**Q: Apakah indikator ini repaint?**  
A: ATR Trailing Stop menggunakan state machine yang bersifat forward-calculated. Nilai bar yang sudah terkonfirmasi tidak berubah. Bar terakhir (realtime) bersifat dinamis sebagaimana lazimnya semua indikator trailing.

**Q: Bolehkah dipakai di pair selain XAUUSD?**  
A: Tentu. Sesuaikan `ATR Multiplier` dan `Noise Threshold` dengan karakteristik volatilitas pair tersebut. Untuk Forex major, coba ATR Mult 1.5–2.5 dan Noise Threshold 0.2–0.3.

**Q: Kenapa tidak ada sinyal meski tren sudah flip?**  
A: Sinyal memerlukan konfirmasi dari EMA Filter **dan** MTF Filter (jika diaktifkan). Cek status filter di Dashboard panel — pastikan kolom "L" atau "S" menunjukkan ✓.

**Q: MTF Filter tidak bekerja?**  
A: Pastikan MTF Timeframe yang dipilih **lebih tinggi** dari timeframe chart aktif. Contoh: jika di H1, gunakan MTF H4 atau D1.

**Q: Dashboard tidak muncul?**  
A: Pastikan parameter `Show Dashboard` = `true` dan tidak ada indikator lain yang menutupi area tersebut. Coba ubah `X Offset` dan `Y Offset`.

---

## 📁 File

```
ATR_ZLEMA_EMA34_PRO.mq5    ← Script utama indikator
README.md                   ← Dokumentasi ini
```

---

## 📜 Changelog

### v2.0 (Current)
- ✅ Tambah 6 Color Presets termasuk **PRESET_GOLD** khusus XAUUSD
- ✅ Premium Dashboard dengan dark UI dan gold accent
- ✅ Glow effect 3 layer pada sinyal
- ✅ Bar coloring dengan transparansi yang bisa diatur
- ✅ Cloud fill antara ZLEMA dan ATR Trail
- ✅ Noise filter yang disempurnakan
- ✅ MTF Confirmation filter
- ✅ 3 EMA Confirmation Mode

---

## 🤝 Kontribusi

Pull request, bug report, dan saran sangat disambut! 

1. Fork repo ini
2. Buat branch baru: `git checkout -b feature/nama-fitur`
3. Commit perubahan: `git commit -m 'Add: deskripsi fitur'`
4. Push: `git push origin feature/nama-fitur`
5. Buat Pull Request

---

## ⚠️ Disclaimer

> Indikator ini adalah alat bantu analisis teknikal. Tidak ada indikator yang memberikan sinyal 100% akurat. Selalu gunakan manajemen risiko yang baik. Penulis tidak bertanggung jawab atas kerugian trading yang terjadi.

---

<div align="center">

**Made with ❤️ by M4DI~UciH4**

[⭐ Star this repo](https://github.com/RizkyEvory) · [🐛 Report Bug](https://github.com/RizkyEvory/issues) · [💡 Request Feature](https://github.com/RizkyEvory/issues)

</div>
