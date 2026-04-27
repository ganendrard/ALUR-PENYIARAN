# Peningkatan Fitur Alur Siaran Nusantara TV

Rencana ini merinci langkah-langkah untuk meningkatkan fungsionalitas dan tampilan `index.html` sesuai dengan saran sebelumnya.

## User Review Required

- **Gambar Ilustrasi**: Apakah Anda ingin saya men-generate gambar ilustrasi menggunakan AI (untuk MCR, Transmisi, Pemancar), atau menyediakan ruang penampung gambar (*image placeholder*) agar Anda dapat memasukkan foto asli alat-alat tersebut nantinya? (Untuk saat ini, saya akan men-generate ilustrasi AI yang rapi agar web langsung terlihat bagus).

## Proposed Changes

### `index.html`

#### 1. Implementasi Dark Mode
- Mengubah warna statis di CSS menjadi CSS Variables (`:root` untuk mode terang, dan `[data-theme="dark"]` untuk mode gelap).
- Menambahkan tombol *toggle* (sakelar) Light/Dark Mode di bagian atas halaman (kanan atas).
- Menambahkan logika JavaScript untuk mengganti tema dan menyimpannya di `localStorage` agar tema tidak reset saat halaman di-refresh.

#### 2. Upgrade Aksesibilitas (A11y)
- Menambahkan atribut ARIA pada elemen navigasi tab:
  - `<div class="tabs" role="tablist">`
  - `<button role="tab" aria-selected="true/false" aria-controls="id-halaman">`
- Menambahkan `role="tabpanel"` pada elemen `.page`.
- Memodifikasi fungsi JavaScript `show()` untuk mengupdate nilai `aria-selected` secara dinamis.

#### 3. Interaksi Antar Halaman & Navigasi
- Mengubah kotak-kotak di "Flowchart Penyiaran" menjadi elemen yang dapat diklik (dengan menambahkan `onclick="show('mcr', document.getElementById('tab-mcr'))"`, dst.) dan efek *cursor: pointer*.
- Membuat wadah tab navigasi (`.tabs`) menjadi *sticky* (`position: sticky`), sehingga tetap menempel di bagian atas layar meskipun halaman di-scroll ke bawah. Ini mempermudah perpindahan antar tab.

#### 4. Penambahan Gambar Ilustrasi
- Men-generate 3-4 gambar ilustrasi menggunakan alat pembuat gambar AI yang merepresentasikan:
  1. Master Control Room (MCR)
  2. Jaringan Fiber Optic / Transmisi
  3. Menara Pemancar DVB-T2
- Menyisipkan tag `<img>` pada halaman detail (`#mcr`, `#transmisi`, `#pemancar`) untuk mempercantik tampilan.

## Verification Plan

### Manual Verification
1. Membuka `index.html` dan mengklik tombol *Light/Dark Mode* untuk memastikan warna berubah dengan baik dan teks tetap terbaca.
2. Menguji navigasi *sticky* dengan men-scroll ke bawah lalu mengklik tab lain.
3. Menekan elemen di bagian "Flowchart" dan memastikan halaman otomatis berpindah ke detail yang tepat (misal: klik kotak MCR -> pindah ke tab MCR).
4. Memastikan kode JavaScript berjalan tanpa eror di *console* peramban web.
