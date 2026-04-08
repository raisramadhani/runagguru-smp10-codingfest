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

Pastikan screen aktif di bagian atas adalah **HalamanUtama**. Di sini kita akan membuat Header dengan Logo terlebih dahulu (yang nanti akan kita copy ke layar lain), baru kemudian membuat 3 tombol menu utama.

### A. Desain (Designer)

1. **Membuat Header & Logo (Untuk di-copy nanti):**
   - Dari panel **Palette** > **Layout**, tarik **HorizontalArrangement** ke layar bagian paling atas.
   - Dari **Palette** > **User Interface**, tarik komponen **Image** ke dalam kotak HorizontalArrangement tadi.
   - Di panel **Components**, klik tombol **Rename** pada gambar tersebut, ubah namanya menjadi: `Logo_Aplikasi`.
   - Di panel **Properties**, cari kotak centang bernama **Clickable** dan **wajib dicentang** (agar logo bisa ditekan).
   - _(Opsional)_ Tarik **Label** di sebelah logo jika ingin memberi teks judul aplikasi.
2. **Membuat Tombol 1 (Tips & Trik):** - Tarik komponen **Button** ke bawah header.
   - Ubah **Text** menjadi: `Tips & Trik Menabung`. Lalu klik **Rename** menjadi: `Tombol_MenuTips`.
3. **Membuat Tombol 2 (Progres Tabungan):** - Tarik **Button** lagi. Ubah **Text** menjadi: `Progres Tabungan & Target`. Klik **Rename** menjadi: `Tombol_MenuProgres`.
4. **Membuat Tombol 3 (Pemasukan & Pengeluaran):** - Tarik **Button** lagi. Ubah **Text** menjadi: `Catat Pemasukan/Pengeluaran`. Klik **Rename** menjadi: `Tombol_MenuInput`.

### B. Kode (Blocks)

Pindah ke tampilan **Blocks**.

1. **Logika Logo (Kembali ke Home):** Klik `Logo_Aplikasi` di panel kiri, tarik `when Logo_Aplikasi.Click do`. Dari kategori **Control**, tarik `open another screen screenName`. Isi dengan teks pink `"HalamanUtama"`. _(Blok ini juga akan ikut tercopy ke halaman lain nanti)._
2. **Menu Tips:** Klik `Tombol_MenuTips`, tarik `when Tombol_MenuTips.Click do`. Tarik blok buka layar, isi dengan teks pink `"TipsTrik"`.
3. **Menu Progres:** Klik `Tombol_MenuProgres`, tarik blok buka layar, isi dengan teks pink `"ProgresTabungan"`.
4. **Menu Input:** Klik `Tombol_MenuInput`, tarik blok buka layar, isi dengan teks pink `"InputKeuangan"`.

> **PENTING:** Silakan coba Run program untuk memeriksa perpindahan layar.

---

## TAHAP 3: Desain & Blocks - TipsTrik

Ganti screen aktif ke **TipsTrik**.

### A. Desain (Designer)

1. **Copy-Paste Header:** - Ganti screen kembali ke `HalamanUtama` sebentar.
   - Klik komponen `HorizontalArrangement` (Header) yang berisi Logo Anda.
   - Tekan tombol **Ctrl + C** (Copy) di keyboard Anda.
   - Ganti screen ke `TipsTrik`. Tekan tombol **Ctrl + V** (Paste). Header dan Logo akan otomatis muncul beserta blok logikanya!
2. **Membuat Wadah Tips:**
   - Dari **Palette** > **Layout**, tarik **ScrollVerticalArrangement** ke layar di bawah header. Di Properties, set **Height** dan **Width** menjadi `Fill Parent`.
3. **Memasukkan Teks Tips:**
   - Di dalam kotak scroll tersebut, tarik sebuah **Label**.
   - Di Properties, cari **Text** dan masukkan semua teks tips menabung Anda di sana.
   - Rename menjadi: `Teks_Tips`.

### B. Kode (Blocks)

Pindah ke tampilan **Blocks**. Anda tidak perlu menambahkan blok apapun di layar ini karena teks bersifat statis, dan blok untuk `Logo_Aplikasi` (kembali ke Halaman Utama) sudah otomatis terbawa dari hasil _copy-paste_ tadi.

---

## TAHAP 4: Desain & Blocks - ProgresTabungan

Ganti screen aktif ke **ProgresTabungan**.

### A. Desain (Designer)

1. **Paste Header:** Langsung tekan tombol **Ctrl + V** (Paste) di keyboard Anda untuk memunculkan Header dan Logo kembali ke layar ini.
2. **Saldo Otomatis:** Tarik **Label**. Ubah Text: `Saldo Saat Ini: Rp 0`. Perbesar font dan centang FontBold. Rename: `Teks_SaldoOtomatis`.
3. **Wadah Input Target (VerticalArrangement):** Rename menjadi `Wadah_Input`. Di dalamnya tarik 3 **TextBox**:
   - TextBox 1 (Nama Barang) -> Rename: `Input_NamaBarang`.
   - TextBox 2 (Nominal Target) -> Rename: `Input_NominalTarget`. (Centang _NumbersOnly_).
   - TextBox 3 (Tanggal Target) -> Rename: `Input_TanggalTarget`.
   - Tambahkan **Button** -> Text: `Simpan Target`. Rename: `Tombol_SimpanTarget`.
4. **Wadah Info Target (VerticalArrangement):** Rename menjadi `Wadah_Info`. Set **Visible** di Properties menjadi `False` (uncheck). Di dalamnya tarik 3 **Label**:
   - Rename: `Teks_InfoNama`, `Teks_InfoNominal`, `Teks_InfoTanggal`.
   - Tambahkan **Button** -> Text: `Hapus & Buat Baru`. Rename: `Tombol_HapusTarget`.
5. **Alat Tambahan:** Tarik **TinyDB** (Rename: `Database_Utama`) dan **Notifier** (Rename: `Pesan_Notif`).

### B. Kode (Blocks)

1. **Saat Layar Dibuka (Initialize):**
   - Tarik blok `when ProgresTabungan.Initialize do`.
   - Set `Teks_SaldoOtomatis.Text` dengan cara: Ambil `GetValue` (tag: "TotalPemasukan") dikurangi `GetValue` (tag: "TotalPengeluaran").
   - **Logika Muncul/Sembunyi:** Gunakan blok `if then else`. Jika `GetValue` (tag: "Target_Nama") = `""` (kosong), maka set `Wadah_Input.Visible` = `True` dan `Wadah_Info.Visible` = `False`. Jika tidak kosong, sebaliknya.
2. **Tombol Simpan:** Klik `Tombol_SimpanTarget`. Gunakan `StoreValue` untuk menyimpan Nama, Nominal, dan Tanggal ke tag masing-masing. Lalu panggil Notifier "Berhasil" dan ganti Visibilitas wadah.
3. **Tombol Hapus:** Klik `Tombol_HapusTarget`. Gunakan `StoreValue` untuk mengisi tag "Target_Nama" dengan teks kosong `""`. Lalu ganti Visibilitas wadah agar Input muncul kembali.

---

## TAHAP 5: Desain & Blocks - InputKeuangan

Ganti screen aktif ke **InputKeuangan**.

### A. Desain (Designer)

1. **Paste Header:** Tekan tombol **Ctrl + V** (Paste) di keyboard Anda agar Header dan Logo kembali muncul.
2. **Input Angka:** Tarik **TextBox** (Centang _NumbersOnly_, Rename: `Input_AngkaUang`).
3. **Tombol Aksi:** Tarik 2 **Button** bersampingan (bisa di dalam HorizontalArrangement).
   - Button 1 -> Text: `Simpan Pemasukan`. Rename: `Tombol_SimpanPemasukan`.
   - Button 2 -> Text: `Simpan Pengeluaran`. Rename: `Tombol_SimpanPengeluaran`.
4. **Daftar Transaksi:** Tarik **ListView**. Rename: `Daftar_Transaksi`.
5. **Alat Tambahan:** Tarik **TinyDB** (Rename: `Database_Utama`) dan **Notifier** (Rename: `Pesan_Notif`).

### B. Kode (Blocks)

1. **Inisialisasi List:** Buat variabel global `DaftarRiwayat` dan isi dengan `create empty list`.
2. **Saat Simpan Pemasukan:**
   - Tarik blok `when Tombol_SimpanPemasukan.Click do`.
   - Ambil total lama dari database tag `"TotalPemasukan"`, tambahkan dengan isi `Input_AngkaUang.Text`, lalu `StoreValue` kembali ke tag `"TotalPemasukan"`.
   - Tambahkan ke list riwayat: Gunakan `add items to list`. Itemnya gunakan `join`: `"Pemasukan: Rp " + Input_AngkaUang.Text`.
   - Simpan list riwayat ke database tag `"Riwayat"`.
   - Update tampilan `Daftar_Transaksi.Elements` dengan list tersebut.
3. **Saat Simpan Pengeluaran:** - Tarik blok `when Tombol_SimpanPengeluaran.Click do`.
   - Lakukan hal yang sama tapi simpan ke tag `"TotalPengeluaran"` dan keterangan di riwayat ganti menjadi `"Pengeluaran: Rp "`.

---

## CATATAN AKHIR

1. **Jangan lupa di save** project Anda.
2. **Coba jalankan secara penuh:** Klik logo di atas untuk kembali ke halaman utama. Input uang di menu Pencatatan, lalu cek apakah saldo di menu Progres berubah secara otomatis.
3. **Desain:** Anda bisa mempercantik warna tombol dan ukuran teks setelah semua fungsi blok berjalan lancar.
