# Data Pakan Anjing & Kucing — Web Tracker

Aplikasi web sederhana (1 file HTML, tanpa server/database) untuk memantau stok &
masa kadaluarsa pakan anjing/kucing per cabang toko, lengkap dengan login,
warna status otomatis, dan export ke Excel/CSV.

## Cara online-kan lewat GitHub Pages (gratis)

1. **Buat repository baru** di GitHub (Public), misalnya bernama `data-pakan`.
2. **Upload file `index.html`** dari folder ini ke repository tersebut.
   - Lewat browser: buka repo → tombol **Add file → Upload files** → pilih `index.html` → **Commit changes**.
   - Atau lewat terminal:
     ```bash
     git clone https://github.com/USERNAME/data-pakan.git
     cd data-pakan
     cp /path/ke/index.html .
     git add index.html
     git commit -m "Tambah aplikasi data pakan"
     git push
     ```
3. **Aktifkan GitHub Pages**:
   - Buka repo → **Settings → Pages**.
   - Pada **Source**, pilih branch `main` dan folder `/ (root)`.
   - Klik **Save**.
4. Tunggu 1–2 menit, lalu situs akan aktif di:
   ```
   https://USERNAME.github.io/data-pakan/
   ```
   Bagikan link ini ke tiap cabang untuk login dengan akun masing-masing.

## Mengganti akun/password cabang

Buka `index.html`, cari bagian `const ACCOUNTS = [ ... ]` di bagian `<script>`,
lalu ubah `username`, `password`, atau `label` sesuai kebutuhan. Setelah
disimpan, `git add`, `git commit`, `git push` lagi — GitHub Pages otomatis
memperbarui situsnya dalam 1–2 menit.

## Penting soal penyimpanan data

Situs ini **statis** (tanpa server/database asli). Data yang diinput disimpan
di `localStorage` **browser/perangkat itu sendiri**, per akun cabang. Artinya:

- Kalau cabang Jakarta selalu input dari laptop toko yang sama, datanya akan
  tetap ada tiap kali dibuka kembali di laptop itu.
- Data **tidak otomatis tersinkron** ke perangkat lain atau ke pusat/admin.
  Jadi kalau admin membuka situs dari komputer berbeda, dropdown pilihan
  cabang tidak akan menampilkan data yang diinput cabang dari perangkat lain.
- Membersihkan cache/riwayat browser, mode Incognito, atau ganti browser akan
  menghilangkan data yang tersimpan.

Ini wajar untuk situs statis GitHub Pages — tidak ada biaya server, tapi juga
tidak ada database pusat. Kalau ke depannya butuh data yang benar-benar
tersinkron antar cabang & bisa diakses admin dari mana saja secara real-time,
itu perlu backend + database sungguhan (misalnya Google Sheets sebagai
database sederhana, atau Firebase/Supabase). Ini bisa dibuatkan terpisah bila
diperlukan.

## Keamanan

Username & password tersimpan sebagai teks biasa di dalam kode `index.html`,
sehingga siapa pun yang membuka "View Page Source" bisa melihatnya. Cocok
untuk penggunaan internal yang sederhana, bukan untuk data yang sangat
sensitif atau publik.
