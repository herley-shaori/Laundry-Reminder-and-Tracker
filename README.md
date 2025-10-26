# Laundry Reminder & Tracker

Aplikasi web sederhana untuk mengingatkan dan melacak jadwal laundry Anda. Ketika Anda menaruh laundry, aplikasi akan otomatis membuat reminder untuk mengambilnya 24 jam kemudian dan menyinkronkannya dengan Google Calendar.

## Fitur

- ✅ Tombol "Taruh Laundry" untuk mencatat laundry baru
- ⏰ Countdown timer 24 jam untuk setiap laundry
- 📊 Dashboard statistik laundry aktif dan selesai
- 📅 Integrasi dengan Google Calendar
- 💾 Penyimpanan lokal menggunakan localStorage
- 📱 Responsive design dengan template Mazer

## Cara Menggunakan

### 1. Setup Google Calendar API

Untuk mengaktifkan sinkronisasi dengan Google Calendar:

1. Buka [Google Cloud Console](https://console.cloud.google.com/)
2. Buat project baru atau pilih project yang sudah ada
3. Aktifkan **Google Calendar API**:
   - Di sidebar, klik "APIs & Services" > "Library"
   - Cari "Google Calendar API"
   - Klik "Enable"

4. Buat kredensial:
   - Klik "APIs & Services" > "Credentials"
   - Klik "Create Credentials" > "API Key"
   - Salin API Key yang dihasilkan

5. Buat OAuth 2.0 Client ID:
   - Klik "Create Credentials" > "OAuth client ID"
   - Pilih "Web application"
   - Tambahkan Authorized JavaScript origins:
     - `http://localhost:5173` (untuk development)
     - `http://localhost:3000`
     - URL production Anda
   - Salin Client ID yang dihasilkan

6. Edit file `index.html` dan ganti:
   ```javascript
   const CLIENT_ID = 'YOUR_CLIENT_ID.apps.googleusercontent.com';
   const API_KEY = 'YOUR_API_KEY';
   ```
   Dengan Client ID dan API Key Anda.

### 2. Menjalankan Aplikasi

#### Opsi 1: Menggunakan NPM (Development)

```bash
# Install dependencies
npm install

# Jalankan development server
npm run dev
```

Aplikasi akan berjalan di `http://localhost:5173`

#### Opsi 2: Menggunakan Live Server

Buka file `index.html` menggunakan Live Server extension di VS Code atau web server lainnya.

#### Opsi 3: Langsung di Browser

Anda bisa langsung membuka `index.html` di browser, tapi fitur Google Calendar mungkin tidak berfungsi karena CORS policy.

### 3. Menggunakan Aplikasi

1. **Taruh Laundry**: Klik tombol besar "Taruh Laundry" di dashboard
2. **Pantau Countdown**: Lihat countdown timer untuk setiap laundry aktif
3. **Sync dengan Google Calendar**: Klik tombol Google merah di pojok kanan bawah untuk sinkronisasi
4. **Tandai Selesai**: Klik tombol "Selesai" ketika sudah mengambil laundry
5. **Lihat Riwayat**: Scroll ke bawah untuk melihat riwayat laundry yang sudah selesai

## Struktur Proyek

```
Laundry-Reminder-and-Tracker/
├── index.html              # File utama aplikasi
├── assets/                 # Assets dari template Mazer
│   ├── compiled/          # CSS dan JS yang sudah dikompilasi
│   ├── extensions/        # Extension libraries
│   └── static/            # Static assets
├── layouts/               # Layout template
├── partials/              # Partial components
├── package.json           # NPM dependencies
└── README.md             # Dokumentasi ini
```

## Teknologi

- **UI Template**: [Mazer](https://github.com/zuramai/mazer) by zuramai
- **Google Calendar API**: Untuk sinkronisasi kalender
- **localStorage**: Untuk penyimpanan data lokal
- **Vanilla JavaScript**: Tanpa framework, murni JavaScript

## Troubleshooting

### Google Calendar tidak tersinkronisasi

- Pastikan Anda sudah setup Client ID dan API Key dengan benar
- Pastikan Authorized JavaScript origins sudah ditambahkan di Google Cloud Console
- Pastikan aplikasi dijalankan melalui web server (bukan langsung buka file HTML)
- Cek console browser untuk error messages

### Data hilang setelah refresh

- Data disimpan di localStorage browser
- Jangan clear cache/cookies browser
- Data akan hilang jika dibuka di browser yang berbeda

## Lisensi

Menggunakan template [Mazer](https://github.com/zuramai/mazer) yang merupakan open source.

## Credits

- Template UI: [Mazer](https://github.com/zuramai/mazer) by [@zuramai](https://github.com/zuramai)
- Icons: Bootstrap Icons
- Google Calendar API

## Kontribusi

Silakan buat pull request atau issue jika ada bug atau saran improvement!

---

Dibuat dengan ❤️ untuk memudahkan tracking laundry
