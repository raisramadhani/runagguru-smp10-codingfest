# Tutorial Membuat Aplikasi KELOMPOK 1 dengan MIT App Inventor

Pastikan Anda sudah login ke MIT App Inventor dan berada di tampilan **Designer** (tombol di pojok kanan atas).

Karena Anda sudah selesai dengan `Screen1` (Login), kita akan melanjutkan pembuatan 4 Screen baru untuk menu Tips, Progres, dan Pencatatan Keuangan.

---

## TAHAP 1: Membuat Screen Baru

Kita perlu membuat 4 Screen baru sesuai konsep Anda.

1. Di bagian atas layar, klik tombol **Add Screen**.
2. Ketik nama: `HalamanUtama` lalu klik OK.
3. Ulangi langkah 1, ketik nama: `TipsTrik` lalu klik OK.
4. Ulangi langkah 1, ketik nama: `ProgresTabungan` lalu klik OK.
5. Ulangi langkah 1, ketik nama: `InputKeuangan` lalu klik OK.

_(Catatan: Pastikan penulisan nama Screen persis seperti di atas tanpa spasi)._

> **PENTING:** Silakan coba Run program, untuk memeriksa aplikasi apakah sudah benar tanpa error belum. Apabila ada error jangan lanjut ke tahap berikutnya.

---

## TAHAP 2: Desain & Blocks - HalamanUtama

Pastikan screen aktif di bagian atas adalah **HalamanUtama**. Di sini kita membuat 3 tombol menu utama.

### A. Desain (Designer)

1. Dari panel **Palette** > **User Interface**, tarik 3 komponen **Button** ke layar HP (Viewer).
2. **Tombol 1 (Tips & Trik):** Klik di komponennya, ubah **Text** menjadi: `Tips & Trik Menabung`. Lalu klik **Rename** menjadi: `Tombol_MenuTips`.
3. **Tombol 2 (Progres Tabungan):** Ubah **Text** menjadi: `Progres Tabungan & Target`. Klik **Rename** menjadi: `Tombol_MenuProgres`.
4. **Tombol 3 (Pemasukan & Pengeluaran):** Ubah **Text** menjadi: `Catat Pemasukan/Pengeluaran`. Klik **Rename** menjadi: `Tombol_MenuInput`.

### B. Kode (Blocks)

Pindah ke tampilan **Blocks**.

1. **Menu Tips:** Klik `Tombol_MenuTips`, tarik `when Tombol_MenuTips.Click do`. Dari kategori **Control**, tarik `open another screen screenName`. Isi dengan teks pink `"TipsTrik"`.
2. **Menu Progres:** Klik `Tombol_MenuProgres`, tarik blok buka layar, isi dengan teks pink `"ProgresTabungan"`.
3. **Menu Input:** Klik `Tombol_MenuInput`, tarik blok buka layar, isi dengan teks pink `"InputKeuangan"`.

> **PENTING:** Silakan coba Run program untuk memeriksa perpindahan layar.

---

## TAHAP 3: Desain & Blocks - TipsTrik

Ganti screen aktif ke **TipsTrik**. Karena deskripsi tips sangat panjang, kita akan membuatnya bisa di-scroll.

### A. Desain (Designer)

1. Dari **Palette** > **Layout**, tarik **ScrollVerticalArrangement** ke layar. Di Properties, set **Height** dan **Width** menjadi `Fill Parent`.
2. Di dalam kotak scroll tersebut, tarik sebuah **Label**.
   - Di Properties, cari **Text** dan masukkan semua teks tips menabung Anda di sana.
   - Rename menjadi: `Teks_Tips`.
3. Di bawah kotak scroll (di luar layout), tarik **Button**. Ubah Text menjadi: `Kembali`. Rename menjadi: `Tombol_Kembali`.

### B. Kode (Blocks)

1. Klik `Tombol_Kembali`, tarik `when Click do`. Gunakan kategori **Control**, pasang blok `open another screen screenName` dengan teks pink `"HalamanUtama"`.

---

## TAHAP 4: Desain & Blocks - ProgresTabungan

Ganti screen aktif ke **ProgresTabungan**. Halaman ini akan menghitung saldo secara otomatis dan menampilkan info target.

### A. Desain (Designer)

1. **Saldo Otomatis:** Tarik **Label**. Ubah Text: `Saldo Saat Ini: Rp 0`. Perbesar font dan centang FontBold. Rename: `Teks_SaldoOtomatis`.
2. **Wadah Input Target (VerticalArrangement):** Rename menjadi `Wadah_Input`. Di dalamnya tarik 3 **TextBox**:
   - TextBox 1 (Nama Barang) -> Rename: `Input_NamaBarang`.
   - TextBox 2 (Nominal Target) -> Rename: `Input_NominalTarget`. (Centang _NumbersOnly_).
   - TextBox 3 (Tanggal Target) -> Rename: `Input_TanggalTarget`.
   - Tambahkan **Button** -> Text: `Simpan Target`. Rename: `Tombol_SimpanTarget`.
3. **Wadah Info Target (VerticalArrangement):** Rename menjadi `Wadah_Info`. Set **Visible** di Properties menjadi `False` (uncheck). Di dalamnya tarik 3 **Label**:
   - Rename: `Teks_InfoNama`, `Teks_InfoNominal`, `Teks_InfoTanggal`.
   - Tambahkan **Button** -> Text: `Hapus & Buat Baru`. Rename: `Tombol_HapusTarget`.
4. **Alat Tambahan:** Tarik **TinyDB** (Rename: `Database_Utama`) dan **Notifier** (Rename: `Pesan_Notif`).

### B. Kode (Blocks)

1. **Saat Layar Dibuka (Initialize):**
   - Set `Teks_SaldoOtomatis.Text` dengan cara: Ambil `GetValue` (tag: "TotalPemasukan") dikurangi `GetValue` (tag: "TotalPengeluaran").
   - **Logika Muncul/Sembunyi:** Jika `GetValue` (tag: "Target_Nama") = `""` (kosong), maka set `Wadah_Input.Visible` = `True` dan `Wadah_Info.Visible` = `False`. Jika tidak kosong, sebaliknya.
2. **Tombol Simpan:** Klik `Tombol_SimpanTarget`. Gunakan `StoreValue` untuk menyimpan Nama, Nominal, dan Tanggal ke tag masing-masing. Lalu panggil Notifier "Berhasil" dan ganti Visibilitas wadah.
3. **Tombol Hapus:** Klik `Tombol_HapusTarget`. Gunakan `StoreValue` untuk mengisi tag "Target_Nama" dengan teks kosong `""`. Lalu ganti Visibilitas wadah agar Input muncul kembali.

---

## TAHAP 5: Desain & Blocks - InputKeuangan

Ganti screen aktif ke **InputKeuangan**.

### A. Desain (Designer)

1. **Input:** Tarik **TextBox** (Centang _NumbersOnly_, Rename: `Input_AngkaUang`).
2. **Tombol Aksi:** Tarik 2 **Button** bersampingan (bisa pakai HorizontalArrangement).
   - Button 1 -> Text: `Simpan Pemasukan`. Rename: `Tombol_SimpanPemasukan`.
   - Button 2 -> Text: `Simpan Pengeluaran`. Rename: `Tombol_SimpanPengeluaran`.
3. **Daftar Transaksi:** Tarik **ListView**. Rename: `Daftar_Transaksi`.
4. **Alat Tambahan:** Tarik **TinyDB** (Rename: `Database_Utama`) dan **Notifier**.

### B. Kode (Blocks)

1. **Inisialisasi List:** Buat variabel global `DaftarRiwayat` dan isi dengan `create empty list`.
2. **Saat Simpan Pemasukan:**
   - Ambil total lama dari database tag `"TotalPemasukan"`, tambahkan dengan isi `Input_AngkaUang.Text`, lalu `StoreValue` kembali ke tag `"TotalPemasukan"`.
   - Tambahkan ke list riwayat: Gunakan `add items to list`. Itemnya gunakan `join`: `"Pemasukan: Rp " + Input_AngkaUang.Text`.
   - Simpan list riwayat ke database tag `"Riwayat"`.
   - Update tampilan `Daftar_Transaksi.Elements` dengan list tersebut.
3. **Saat Simpan Pengeluaran:** Lakukan hal yang sama tapi simpan ke tag `"TotalPengeluaran"` dan keterangan di riwayat ganti menjadi `"Pengeluaran: Rp "`.

---

## CATATAN AKHIR

1. **Jangan lupa di save** project Anda.
2. **Coba jalankan secara penuh:** Input uang di Screen 5, lalu cek apakah saldo di Screen 4 berubah secara otomatis.
3. **Desain:** Anda bisa mempercantik warna tombol dan ukuran teks setelah semua fungsi blok berjalan lancar.
