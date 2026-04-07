# Tutorial Membuat Aplikasi KELOMPOK 4 dengan MIT App Inventor

Pastikan Anda sudah login ke MIT App Inventor dan berada di tampilan **Designer** (tombol di pojok kanan atas).

Karena Anda sudah selesai dengan `Screen1` (Login), kita akan langsung membuat halaman selanjutnya sesuai dengan konsep manajemen keuangan dan target impian Anda.

---

## TAHAP 1: Membuat Screen Baru

Kita perlu membuat 4 Screen baru.

1. Di bagian atas layar, klik tombol **Add Screen**.
2. Ketik nama: `HalamanUtama` lalu klik OK.
3. Ulangi langkah 1, ketik nama: `SaldoTarget` lalu klik OK.
4. Ulangi langkah 1, ketik nama: `Pemasukan` lalu klik OK.
5. Ulangi langkah 1, ketik nama: `Pengeluaran` lalu klik OK.

_(Catatan: Pastikan penulisan nama Screen persis seperti di atas tanpa spasi)._

> **PENTING:** Silakan coba Run program, untuk memeriksa aplikasi apakah sudah benar tanpa error belum. Apabila ada error jangan lanjut ke tahap berikutnya.

---

## TAHAP 2: Desain & Blocks - HalamanUtama

Pastikan screen aktif di bagian atas adalah **HalamanUtama**. Di sini kita membuat 4 tombol menu utama.

### A. Desain (Designer)

1. Dari panel **Palette** > **User Interface**, tarik 4 komponen **Button** ke layar HP (Viewer) secara berurutan ke bawah.
2. **Tombol 1 (Pemasukan):** Klik di komponennya, ubah **Text** di Properties menjadi: `Input Pemasukan`. Lalu klik **Rename** menjadi: `Tombol_MenuPemasukan`.
3. **Tombol 2 (Pengeluaran):** Ubah **Text** menjadi: `Input Pengeluaran`. Klik **Rename** menjadi: `Tombol_MenuPengeluaran`.
4. **Tombol 3 (Saldo):** Ubah **Text** menjadi: `Cek Saldo`. Klik **Rename** menjadi: `Tombol_MenuSaldo`.
5. **Tombol 4 (Target):** Ubah **Text** menjadi: `Target Impian`. Klik **Rename** menjadi: `Tombol_MenuTarget`.

### B. Kode (Blocks)

Pindah ke tampilan **Blocks**.

1. **Menu Pemasukan:** Klik `Tombol_MenuPemasukan`, tarik `when Tombol_MenuPemasukan.Click do`. Dari kategori **Control**, tarik `open another screen screenName`. Isi dengan teks pink `"Pemasukan"`.
2. **Menu Pengeluaran:** Klik `Tombol_MenuPengeluaran`, tarik `when Tombol_MenuPengeluaran.Click do`. Tarik blok buka layar, isi dengan teks pink `"Pengeluaran"`.
3. **Menu Saldo:** Klik `Tombol_MenuSaldo`, tarik `when Tombol_MenuSaldo.Click do`. Tarik blok buka layar, isi dengan teks pink `"SaldoTarget"`.
4. **Menu Target:** Klik `Tombol_MenuTarget`, tarik `when Tombol_MenuTarget.Click do`. Tarik blok buka layar, isi dengan teks pink `"SaldoTarget"`. _(Catatan: Menu Saldo dan Target diarahkan ke layar yang sama sesuai konsep)._

> **PENTING:** Silakan coba Run program, untuk memeriksa aplikasi apakah sudah benar tanpa error belum. Apabila ada error jangan lanjut ke tahap berikutnya.

---

## TAHAP 3: Desain & Blocks - SaldoTarget

Ganti screen aktif ke **SaldoTarget**. Di sini kita akan membuat sistem perhitungan saldo otomatis dan form target yang bisa disembunyikan.

### A. Desain (Designer)

1. **Info Saldo:** Tarik **Label**. Ubah Text menjadi: `Sisa Saldo Anda: Rp 0`. Perbesar ukuran font, dan centang FontBold. Rename menjadi: `Teks_TotalSaldo`.
2. **Wadah Form Target:** Dari **Palette** > **Layout**, tarik **VerticalArrangement**. Rename menjadi: `Wadah_FormTarget`.
   - Di dalam wadah ini, tarik 4 **TextBox**:
     - TextBox 1 -> Hint: `Nama Barang`, Rename: `Input_NamaTarget`.
     - TextBox 2 -> Hint: `URL / Link Barang`, Rename: `Input_URLTarget`.
     - TextBox 3 -> Hint: `Nominal Target`, Centang _NumbersOnly_, Rename: `Input_NominalTarget`.
     - TextBox 4 -> Hint: `Tanggal (Due Date)`, Rename: `Input_TanggalTarget`.
   - Tarik 1 **Button** ke dalam wadah ini. Ubah Text: `Simpan Target`. Rename: `Tombol_SimpanTarget`.
3. **Wadah Info Target (Jika Target Sudah Ada):** Tarik **VerticalArrangement** baru ke bawah layar. Rename: `Wadah_InfoTarget`.
   - Di dalam wadah ini, tarik 4 **Label** berurutan ke bawah. Rename masing-masing menjadi: `Teks_InfoNama`, `Teks_InfoURL`, `Teks_InfoNominal`, `Teks_InfoTanggal`. (Isi Text-nya biarkan bawaan dulu).
   - Tarik 1 **Button** ke dalam wadah ini. Ubah Text: `Hapus Target (Bikin Baru)`. Rename: `Tombol_HapusTarget`.
   - **PENTING:** Di panel Properties `Wadah_InfoTarget`, hilangkan centang **Visible** (agar disembunyikan saat layar pertama kali dibuka).
4. **Tombol Kembali:** Tarik **Button** ke paling bawah layar (di luar wadah). Text: `Kembali`, Rename: `Tombol_Kembali`.
5. **Database:** Tarik **TinyDB** dari Storage (Rename: `Database_Aplikasi`). Tarik **Notifier** dari User Interface (Rename: `Notifikasi_Pesan`).

### B. Kode (Blocks)

Pindah ke tampilan **Blocks**.

**Bagian 1: Memuat Data Saat Layar Dibuka**

1. Klik komponen `SaldoTarget` (ikon layar paling atas di panel kiri), tarik blok kuning `when SaldoTarget.Initialize do`.
2. **Hitung Saldo:** Klik `Teks_TotalSaldo`, tarik `set Teks_TotalSaldo.Text to`.
   - Pasangkan blok `join` (dari Text). Lubang 1 isi dengan teks pink `"Sisa Saldo Anda: Rp "`.
   - Lubang 2: Tarik blok Math kurang `-`.
   - Di sisi kiri blok `-`: tarik `call Database_Aplikasi.GetValue`, isi tag dengan `"TotalPemasukan"`, default `0`.
   - Di sisi kanan blok `-`: tarik `call Database_Aplikasi.GetValue`, isi tag dengan `"TotalPengeluaran"`, default `0`.
3. **Cek Target:** Dari kategori **Control**, tarik blok `if then else` dan pasangkan di bawah set Saldo tadi (masih di dalam Initialize).
   - Di bagian `if`: tarik blok Math sama dengan `=`. Sisi kiri isi dengan `call Database_Aplikasi.GetValue` (tag: `"Target_Nama"`, default: `""`). Sisi kanan isi dengan teks pink kosong `""`.
   - Di bagian `then` (Artinya belum punya target): set `Wadah_FormTarget.Visible to true` dan set `Wadah_InfoTarget.Visible to false`.
   - Di bagian `else` (Artinya sudah punya target): set `Wadah_FormTarget.Visible to false` dan set `Wadah_InfoTarget.Visible to true`.
   - _(Tambahan di dalam else)_: Set teks keempat Info (Nama, URL, Nominal, Tanggal) dengan mengambil nilainya dari Database menggunakan tag `"Target_Nama"`, `"Target_URL"`, `"Target_Nominal"`, dan `"Target_Tanggal"`.

**Bagian 2: Tombol Simpan & Hapus Target**

1. **Simpan:** Klik `Tombol_SimpanTarget`, tarik `when Click do`.
   - Tarik 4 blok ungu `StoreValue` dari Database. Simpan masing-masing input TextBox ke tag-nya masing-masing (`"Target_Nama"`, dll).
   - Tarik blok `ShowAlert` dari Notifier, isi pesan: `"Target Disimpan!"`.
   - Panggil blok agar Info Target muncul: set `Wadah_FormTarget.Visible to false`, dan `Wadah_InfoTarget.Visible to true`. (Jangan lupa set teks infonya dengan data yang baru diinput).
2. **Hapus:** Klik `Tombol_HapusTarget`, tarik `when Click do`.
   - Tarik blok ungu `StoreValue`, isi tag `"Target_Nama"` dengan teks pink kosong `""` (Ini untuk me-reset database targetnya).
   - Balikkan visibilitas: set `Wadah_FormTarget.Visible to true` dan `Wadah_InfoTarget.Visible to false`.
3. **Kembali:** Tarik blok click `Tombol_Kembali`, pasang blok buka layar `"HalamanUtama"`.

> **PENTING:** Silakan coba Run program, untuk memeriksa aplikasi apakah sudah benar tanpa error belum. Apabila ada error jangan lanjut ke tahap berikutnya.

---

## TAHAP 4: Desain & Blocks - Pemasukan

Ganti screen aktif ke **Pemasukan**.

### A. Desain (Designer)

1. Tarik **TextBox**, centang _NumbersOnly_, Hint: `Nominal Pemasukan`, Rename: `Input_Pemasukan`.
2. Tarik **Button**, Text: `Simpan Pemasukan`, Rename: `Tombol_SimpanPemasukan`.
3. Tarik **Button**, Text: `Kembali`, Rename: `Tombol_Kembali`.
4. Tarik **TinyDB** (Rename: `Database_Aplikasi`) dan **Notifier** (Rename: `Notifikasi_Pesan`).

### B. Kode (Blocks)

1. Klik `Tombol_SimpanPemasukan`, tarik `when Click do`.
2. Tarik `call Database_Aplikasi.StoreValue`. Isi tag dengan teks pink `"TotalPemasukan"`.
3. Di bagian `valueToStore`, tarik blok Math tambah `+`.
   - Sisi kiri: tarik `call Database_Aplikasi.GetValue`, isi tag `"TotalPemasukan"`, default `0` (Mengambil total pemasukan yang sudah ada sebelumnya).
   - Sisi kanan: tarik `Input_Pemasukan.Text` (Menambahkan dengan yang baru).
4. Tarik blok `ShowAlert` Notifier, isi pesan `"Pemasukan Berhasil Ditambah!"`.
5. Tarik blok click `Tombol_Kembali`, pasang blok buka layar `"HalamanUtama"`.

> **PENTING:** Silakan coba Run program, untuk memeriksa aplikasi apakah sudah benar tanpa error belum. Apabila ada error jangan lanjut ke tahap berikutnya.

---

## TAHAP 5: Desain & Blocks - Pengeluaran

Ganti screen aktif ke **Pengeluaran**. (Tahap ini hampir sama persis dengan Pemasukan).

### A. Desain (Designer)

1. Tarik **TextBox**, centang _NumbersOnly_, Hint: `Nominal Pengeluaran`, Rename: `Input_Pengeluaran`.
2. Tarik **Button**, Text: `Simpan Pengeluaran`, Rename: `Tombol_SimpanPengeluaran`.
3. Tarik **Button**, Text: `Kembali`, Rename: `Tombol_Kembali`.
4. Tarik **TinyDB** (Rename: `Database_Aplikasi`) dan **Notifier** (Rename: `Notifikasi_Pesan`).

### B. Kode (Blocks)

1. Klik `Tombol_SimpanPengeluaran`, tarik `when Click do`.
2. Tarik `call Database_Aplikasi.StoreValue`. Isi tag dengan teks pink `"TotalPengeluaran"`.
3. Di bagian `valueToStore`, tarik blok Math tambah `+`.
   - Sisi kiri: tarik `call Database_Aplikasi.GetValue`, isi tag `"TotalPengeluaran"`, default `0`.
   - Sisi kanan: tarik `Input_Pengeluaran.Text`.
   - _(Catatan: Di sini kita menjumlahkan total pengeluarannya, pengurangannya terjadi nanti di halaman Saldo)._
4. Tarik blok `ShowAlert` Notifier, isi pesan `"Pengeluaran Berhasil Dicatat!"`.
5. Tarik blok click `Tombol_Kembali`, pasang blok buka layar `"HalamanUtama"`.

> **PENTING:** Silakan coba Run program, untuk memeriksa aplikasi apakah sudah benar tanpa error belum. Apabila ada error jangan lanjut ke tahap berikutnya.

---

## CATATAN AKHIR

1. **Jangan lupa di save** project Anda di MIT App Inventor.
2. **Ini Hanya prototype saja** alias aplikasi mu belum selesai. Lanjutkan desain secantik mungkin pada masing-masing halaman. Hati-hati saat mendesain agar fitur (Blocks) yang sudah ada tidak error.
