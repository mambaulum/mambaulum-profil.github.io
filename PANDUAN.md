# Panduan memasang profil madrasah

Isi folder: `index.html` (halaman publik), `admin.html` (halaman edit), `config.js`, `defaults.js`, folder `img/`, `rules-profil.json`.

## 1. Siapkan Firebase
1. Buka Firebase Console, pilih proyek (boleh proyek yang sama dengan SI MAMBA).
2. Authentication > Sign-in method > aktifkan **Email/Password**.
3. Authentication > Users > **Add user**: buat akun admin (email dan kata sandi). Salin **User UID**-nya.

## 2. Aturan database
1. Realtime Database > **Rules**.
2. Tambahkan dua blok dari `rules-profil.json` (`profil` dan `profil_admin`) ke dalam `"rules": { ... }` yang sudah ada. Jangan menimpa aturan lama.
3. Publish.

## 3. Daftarkan admin
Realtime Database > Data > tambahkan node `profil_admin` dengan anak bernama UID admin tadi dan nilai `true`.
Untuk admin tambahan: buat user di Authentication, lalu tambahkan UID-nya di sini.

## 4. Isi config.js
Project settings > Your apps > tambah Web app. Salin `apiKey` ke `config.js`. Isi `databaseURL` dengan alamat Realtime Database (contoh `https://nama-proyek-default-rtdb.firebaseio.com`).

## 5. Hosting
- Firebase Hosting: `firebase init hosting` (public directory: folder ini), lalu `firebase deploy`.
- Atau tarik folder ini ke Netlify / Cloudflare Pages, atau unggah ke `public_html` hosting biasa.

## 6. Mengedit
Buka `alamat-situs/admin.html`, masuk, ubah isi atau foto, klik Simpan dan terbitkan. Halaman utama langsung memakai isi baru.

Catatan: foto disimpan di database (otomatis diperkecil). Sebaiknya jangan lebih dari sekitar 20 foto.
