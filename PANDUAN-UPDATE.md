# Panduan update NovaPS (waktu sewa per unit, edit identitas, warna durasi)

Zip ini hanya berisi file yang BERUBAH (24 file, tidak ada file baru). Susunan
foldernya sama dengan proyek Anda, jadi cukup **salin isi folder
`novaps-update/` ke folder proyek** (yang berisi `index.html`) dan pilih
**Replace / Timpa** jika ditanya. Jangan memindahkan folder `novaps-update`
itu sendiri ke dalam proyek.

## File yang DIPERBARUI (timpa yang lama)

| File | Perubahan |
|---|---|
| `js/shared/orders.js` | Setiap unit punya waktu sewa, perpanjangan, dan pengembalian sendiri |
| `js/shared/rental-alerts.js` | Peringatan 4 jam, 1 jam, dan overdue per unit |
| `js/shared/admin-ui.js` | Pop-up admin: hitung mundur per unit dan tombol Mark returned per unit |
| `js/time-remaining.js` | Satu kartu per unit |
| `js/extend.js` | Perpanjangan per unit (`?order=...&unit=...`) |
| `js/order-detail.js`, `pages/order-detail.html` | Struk menampilkan hitung mundur dan tombol Extend per unit |
| `js/admin-time-remaining.js` | Satu baris per unit |
| `js/admin-dashboard.js` | Denda per unit masuk ke penghasilan |
| `js/order-form.js`, `pages/order-form.html` | Tombol Edit untuk mengubah identitas, warna berbeda saat mengedit |
| `src/partials/forms.css` | Pilihan durasi tidak lagi terlihat abu-abu seperti nonaktif |
| `css/*.css` yang tercantum | Hasil build (halaman yang memakai komponen input) |
| `README.md` | Catatan terbaru |

## Setelah menyalin
1. `npm run build` (opsional, folder `css/` di zip sudah ter-build).
2. Coba cepat:
   - Order 2 unit (3 hari dan 2 hari), bayar, lalu di admin: Accept dan
     Confirm delivered. Time Remaining customer dan admin menampilkan dua
     hitung mundur terpisah. Di Look Detail admin, tekan Mark returned pada
     satu unit saja. Stok unit itu langsung bertambah 1.
   - Form order: tekan Edit pada Customer Information, ubah nama atau alamat,
     tekan Done, lalu Checkout. Perubahan tersimpan ke My Profile.
3. Untuk GitHub dan Vercel: `git add .`, lalu `git commit -m "Per-unit rental time"`, lalu `git push`.

## Catatan
- Tidak ada file lama yang perlu dihapus.
- Order lama yang sudah berstatus Complete tetap aman. Waktunya dihitung ulang
  dari tanggal pengantaran dan durasi tiap unitnya.
- Perpanjangan sekarang per unit. Order dua unit diperpanjang satu per satu.
