# Clone Onboxin — Project Context

## Tujuan

Onboxin adalah workstation operasional untuk proses retur gudang e-commerce: scan paket, rekam unboxing, validasi SKU/jumlah/kondisi, simpan bukti, buat laporan, dan tindak lanjuti dispute/RMA.

## Struktur aplikasi

- `src/`: frontend React, komponen operasional, konteks akun/bahasa, service sinkronisasi, dan utilitas laporan.
- `server.ts`: backend Express dan endpoint sinkronisasi/persistensi.
- `src/db/`: koneksi database, schema Drizzle, dan akses data warehouse.
- `drizzle/`: migration SQL dan snapshot schema PostgreSQL.
- `public/`: logo dan banner Onboxin.
- `tests/`: unit test dan integration test backend/frontend.
- `docs/`: panduan local trial dan operasional.

## Alur bisnis utama

Paket retur tiba → operator scan resi/Order ID → video unboxing → pemeriksaan SKU, jumlah, dan kondisi → hasil disimpan → laporan dibuat → kasus bermasalah diteruskan ke CS/RMA/manager.

## Modul utama

Dashboard, Unboxing Station, Result Viewer, Reports, Dispute Claims, RMA Claims, Claim History, Master Database, Finance, Store Management, Account Management, Backup Settings, dan Rules Docs.

## Database

Pengembangan lokal menggunakan PGlite. Production dapat menggunakan PostgreSQL managed seperti Supabase dengan konfigurasi driver PostgreSQL dan environment variables. Migration dan schema tersedia di `drizzle/` serta `src/db/`.

## Konfigurasi production

Gunakan `.env.example` sebagai template. Jangan commit `.env` asli, password database, API key, token Firebase/Google Drive, video retur, atau data pelanggan. Untuk deployment production, siapkan `NODE_ENV`, `PORT`, koneksi PostgreSQL, `SQL_SSL`, dan kredensial integrasi yang diperlukan.

## Menjalankan clone

1. Install dependency dengan `npm install`.
2. Salin `.env.example` menjadi `.env` dan isi nilai lokal.
3. Jalankan `npm run dev` untuk development.
4. Jalankan `npm run build` untuk build frontend.
5. Jalankan `npm test` untuk pengujian.

## Catatan deployment

Repository ini berisi source dan konteks aplikasi. Deployment ke VPS/Render membutuhkan environment variables production, database PostgreSQL, domain/HTTPS, dan kredensial layanan eksternal yang dikelola di secret manager/platform—bukan di GitHub.

