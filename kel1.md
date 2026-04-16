# Tutorial Membuat Aplikasi KELOMPOK 1 (SMP 1 Surakarta)

Pastikan Anda sudah login ke MIT App Inventor, membuat project baru, dan berada di tampilan **Designer** (tombol di pojok kanan atas).

---

## TAHAP 0: Membuat Halaman Login (Screen1)

Kita akan membuat halaman Login terlebih dahulu di **Screen1** (Screen bawaan saat pertama kali membuat project).

### A. Desain (Designer)

1. **Input Username:** Dari panel **Palette** > **User Interface**, tarik komponen **TextBox** ke layar.
   - Di panel **Properties** (sebelah kanan), ubah **Hint** menjadi: `Masukkan Username`.
   - Di panel **Components**, klik **Rename Component** dan ubah namanya menjadi: `InputUsername`.
2. **Input Password:** Dari panel **Palette** > **User Interface**, tarik komponen **PasswordTextBox** ke layar.
   - Di panel **Properties**, ubah **Hint** menjadi: `Masukkan Password`.
   - Klik **Rename Component**, ubah menjadi: `InputPassword`.
3. **Tombol Login:** Dari **Palette**, tarik komponen **Button** ke layar.
   - Di panel **Properties**, ubah **Text** menjadi: `Masuk / Login`.
   - Klik **Rename Component**, ubah menjadi: `Tombol_Masuk`.
4. **Pesan Notifikasi:** Dari panel **Palette**, tarik komponen **Notifier** ke layar (komponen ini akan muncul di bawah layar). Biarkan namanya tetap `Notifier1`.

### B. Kode (Blocks)

Pindah ke tampilan **Blocks** (pojok kanan atas).

1. Di panel kiri, klik `Tombol_Masuk`, tarik blok kuning paling atas: `when Tombol_Masuk.Click do`.
2. Dari kategori **Control** (warna oranye), tarik blok `if then else` ke dalam blok kuning.
3. **Mengatur Syarat Login (Bagian if):**
   - Dari kategori **Logic** (hijau terang), tarik blok `and` pasangkan ke sebelah `if`.
   - Di lubang kiri `and`: Tarik blok sama dengan `=` dari kategori **Logic**. Sisi kirinya isi dengan blok hijau tua `InputUsername.Text`, sisi kanannya isi dengan teks pink `" "` dan ketik `123`.
   - Di lubang kanan `and`: Tarik blok `=` lagi. Sisi kirinya isi dengan blok hijau tua `InputPassword.Text`, sisi kanannya isi dengan teks pink `" "` dan ketik `123`.
4. **Jika Login Benar (Bagian then):**
   - Klik `Notifier1`, tarik blok ungu `call Notifier1.ShowAlert notice`. Pasangkan ke dalam `then`. Isi dengan teks pink `" "` dan ketik: `Selamat datang kembali!`.
   - Dari kategori **Control**, tarik blok `open another screen screenName`. Isi dengan teks pink `" "` dan ketik: `HalamanUtama`.
5. **Jika Login Salah (Bagian else):**
   - Tarik lagi blok ungu `call Notifier1.ShowAlert notice` ke dalam `else`. Isi dengan teks pink `" "` dan ketik: `Password Salah kak`.

---

## TAHAP 1: Membuat Screen Baru

Kita perlu membuat 5 Screen baru sesuai konsep aplikasi Anda.

1. Di bagian atas layar, klik tombol **Add Screen**.
2. Ketik nama: `HalamanUtama` lalu klik OK.
3. Ulangi langkah 1, ketik nama: `TipsTrik` lalu klik OK.
4. Ulangi langkah 1, ketik nama: `Pemasukan` lalu klik OK.
5. Ulangi langkah 1, ketik nama: `Pengeluaran` lalu klik OK.
6. Ulangi langkah 1, ketik nama: `ProgresTabungan` lalu klik OK.

_(Catatan: Pastikan penulisan nama Screen persis seperti di atas tanpa spasi)._

> **PENTING:** Silakan coba Run program di HP Anda untuk memastikan bisa login dengan username "123" dan password "123".

---

## TAHAP 2: Desain & Blocks - HalamanUtama

Pastikan screen aktif di bagian atas adalah **HalamanUtama**. Di sini kita akan membuat Header dengan Logo terlebih dahulu (yang nanti akan kita _copy_ ke layar lain), lalu membuat 4 tombol menu utama.

### A. Desain (Designer)

1. **Membuat Header & Logo (Untuk di-copy nanti):**
   - Dari panel **Palette** > **Layout**, tarik **HorizontalArrangement** ke layar bagian paling atas.
   - Dari **Palette** > **User Interface**, tarik komponen **Image** ke dalam kotak HorizontalArrangement tadi.
   - Di panel **Components**, klik tombol **Rename Component** pada gambar tersebut, ubah namanya menjadi: `Logo_Aplikasi`.
   - Di panel **Properties**, cari kotak centang bernama **Clickable** dan **wajib dicentang** (agar logo bisa ditekan untuk kembali ke home).
2. **Membuat 4 Tombol Menu:** Tarik 4 komponen **Button** ke bawah header secara berurutan.
   - Button 1 -> Text: `Tips & Trik Menabung`. Rename: `Tombol_MenuTips`.
   - Button 2 -> Text: `Input Pemasukan`. Rename: `Tombol_MenuPemasukan`.
   - Button 3 -> Text: `Input Pengeluaran`. Rename: `Tombol_MenuPengeluaran`.
   - Button 4 -> Text: `Progres Tabungan & Target`. Rename: `Tombol_MenuProgres`.

### B. Kode (Blocks)

Pindah ke tampilan **Blocks**.

1. **Logika Logo (Kembali ke Home):** Klik `Logo_Aplikasi` di panel kiri, tarik `when Logo_Aplikasi.Click do`. Dari kategori **Control**, tarik `open another screen screenName`. Isi dengan teks pink `"HalamanUtama"`. _(Blok ini juga akan ikut tercopy ke halaman lain nanti)._
2. **Navigasi Menu:** Buat blok `when Click do` untuk keempat tombol tadi. Dari kategori **Control**, pasangkan blok `open another screen screenName` dan isi teks pink sesuai tujuannya:
   - `Tombol_MenuTips` arahkan ke `"TipsTrik"`
   - `Tombol_MenuPemasukan` arahkan ke `"Pemasukan"`
   - `Tombol_MenuPengeluaran` arahkan ke `"Pengeluaran"`
   - `Tombol_MenuProgres` arahkan ke `"ProgresTabungan"`

---

## TAHAP 3: Desain & Blocks - TipsTrik

Ganti screen aktif ke **TipsTrik**. Di sini kita akan membuat daftar list yang bisa diklik untuk membaca deskripsi tips.

### A. Desain (Designer)

1. **Copy-Paste Header:**
   - Ganti screen kembali ke `HalamanUtama` sebentar. Klik komponen `HorizontalArrangement` (Header) yang berisi Logo Anda. Tekan tombol **Ctrl + C** (Copy).
   - Ganti screen ke `TipsTrik`. Tekan tombol **Ctrl + V** (Paste). Header dan Logo akan otomatis muncul beserta blok logikanya!
2. **Membuat Daftar Judul:** Dari **Palette** > **User Interface**, tarik komponen **ListView** ke layar.
   - Di panel **Properties**, ubah **Height** menjadi `30 Percent`.
   - Rename: `Daftar_TipsTrik`.
3. **Membuat Wadah Deskripsi:** Dari **Palette** > **Layout**, tarik **ScrollVerticalArrangement** ke bawah ListView tadi. Set **Height** dan **Width** menjadi `Fill Parent`.
4. **Menyiapkan Teks Deskripsi:** Di dalam kotak scroll tersebut, tarik sebuah **Label**.
   - Rename: `Teks_Deskripsi`. Ubah teks bawaannya menjadi: `Silakan klik salah satu judul tips di atas untuk membaca detailnya.`

### B. Kode (Blocks)

Pindah ke **Blocks**. Kita akan membuat dua buah List variabel (Judul & Deskripsi).

1. **Variabel Data:** Di kategori **Variables**, buat dua variabel global.
   - `initialize global DataJudul to`: Pasangkan blok `make a list` (isi 3 teks pink dengan judul, misal: `"1. Konsisten Menabung"`, `"2. Bawa Bekal"`, `"3. Tabungan Receh"`).
   - `initialize global DataDeskripsi to`: Pasangkan blok `make a list` (isi 3 teks pink dengan penjelasan panjang sesuai urutan judul).
2. **Tampilkan Judul:** Tarik blok kuning `when TipsTrik.Initialize do`. Klik `Daftar_TipsTrik`, tarik `set Daftar_TipsTrik.Elements to` dan pasangkan dengan blok merah `get global DataJudul`.
3. **Tampilkan Deskripsi Saat Diklik:** - Tarik blok kuning `when Daftar_TipsTrik.AfterPicking do`.
   - Tarik `set Teks_Deskripsi.Text to`. Gunakan blok `join` dengan 3 lubang.
   - Lubang 1: Blok hijau tua `Daftar_TipsTrik.Selection`.
   - Lubang 2: Teks pink `" "` ketik `\n\n` (untuk membuat enter/baris baru).
   - Lubang 3: Tarik blok biru muda `select list item`. Bagian list isi dengan `get global DataDeskripsi`. Bagian index isi dengan `Daftar_TipsTrik.SelectionIndex`.

---

## TAHAP 4: Desain & Blocks - Pemasukan

Ganti screen aktif ke **Pemasukan**.

### A. Desain (Designer)

1. **Paste Header:** Tekan **Ctrl + V** (Paste) agar Header dan Logo kembali muncul.
2. **Input Data:** Tarik 2 komponen **TextBox**.
   - TextBox 1 -> Hint: `Keterangan (Contoh: Uang Saku)`, Rename: `Input_KeteranganMasuk`.
   - TextBox 2 -> Hint: `Nominal Pemasukan`, centang _NumbersOnly_, Rename: `Input_NominalMasuk`.
3. **Simpan & Riwayat:** Tarik **Button** (Text: `Simpan Pemasukan`, Rename: `Tombol_SimpanPemasukan`) dan **ListView** (Rename: `Daftar_Pemasukan`).
4. **Alat Tambahan:** Tarik **TinyDB** (Rename: `Database_Utama`) dan **Notifier** (Rename: `Pesan_Notif`).

### B. Kode (Blocks)

Pindah ke **Blocks**.

1. **Variabel & Inisialisasi:** Buat variabel `global RiwayatMasuk` isi dengan `create empty list`. Saat `when Pemasukan.Initialize do`, set `global RiwayatMasuk` dengan `GetValue` tag `"DataPemasukan"`. Tampilkan ke `set Daftar_Pemasukan.Elements to` `get global RiwayatMasuk`.
2. **Logika Tombol Simpan:** Saat `Tombol_SimpanPemasukan.Click do`:
   - **Total Saldo:** `StoreValue` tag `"TotalPemasukan"`. Isi dengan blok Math `+` (`GetValue` tag `"TotalPemasukan"` ditambah `Input_NominalMasuk.Text`).
   - **Riwayat:** Gunakan `add items to list` (list: `get global RiwayatMasuk`). Itemnya `join` (`Input_KeteranganMasuk.Text`, `" - Rp "`, `Input_NominalMasuk.Text`).
   - **Simpan & Tampil:** `StoreValue` tag `"DataPemasukan"` isinya `get global RiwayatMasuk`. Update `Daftar_Pemasukan.Elements`.
   - **Notifikasi:** `ShowAlert` pesan `"Pemasukan Berhasil Disimpan!"`.

---

## TAHAP 5: Desain & Blocks - Pengeluaran

Ganti screen aktif ke **Pengeluaran**. Tahap ini hampir sama persis dengan Pemasukan.

### A. Desain (Designer)

1. **Paste Header:** Tekan **Ctrl + V** (Paste).
2. **Input Data:** Tarik 2 komponen **TextBox**.
   - TextBox 1 -> Hint: `Keterangan (Contoh: Beli Makan)`, Rename: `Input_KetKeluar`.
   - TextBox 2 -> Hint: `Nominal Pengeluaran`, centang _NumbersOnly_, Rename: `Input_NominalKeluar`.
3. **Simpan & Riwayat:** Tarik **Button** (Text: `Simpan Pengeluaran`, Rename: `Tombol_SimpanPengeluaran`) dan **ListView** (Rename: `Daftar_Pengeluaran`).
4. **Alat Tambahan:** Tarik **TinyDB** (Rename: `Database_Utama`) dan **Notifier** (Rename: `Pesan_Notif`).

### B. Kode (Blocks)

Pindah ke **Blocks**. Ikuti pola yang persis sama seperti Pemasukan.

1. **Variabel & Inisialisasi:** Buat `global RiwayatKeluar`. Saat `Initialize`, ambil `GetValue` tag `"DataPengeluaran"` dan tampilkan ke `Daftar_Pengeluaran.Elements`.
2. **Tombol Simpan:** Saat `Tombol_SimpanPengeluaran.Click do`:
   - **Total Saldo:** `StoreValue` tag `"TotalPengeluaran"` (tambahkan `GetValue` "TotalPengeluaran" dengan `Input_NominalKeluar.Text`).
   - **Riwayat:** `add items to list` (item `join`: `Input_KetKeluar.Text`, `" - Rp "`, `Input_NominalKeluar.Text`).
   - **Simpan & Tampil:** `StoreValue` tag `"DataPengeluaran"`. Update Elements.
   - **Notifikasi:** `ShowAlert` pesan `"Pengeluaran Berhasil Dicatat!"`.

---

## TAHAP 6: Desain & Blocks - ProgresTabungan

Ganti screen aktif ke **ProgresTabungan**.

### A. Desain (Designer)

1. **Paste Header:** Tekan **Ctrl + V** (Paste).
2. **Saldo Otomatis:** Tarik **Label**. Text: `Saldo Saat Ini: Rp 0`. Perbesar font, centang FontBold. Rename: `Teks_SaldoOtomatis`.
3. **Wadah Input Target:** Tarik **VerticalArrangement** (Rename: `Wadah_Input`). Di dalamnya tarik:
   - TextBox 1 -> Hint: `Nama Barang`, Rename: `Input_NamaBarang`.
   - TextBox 2 -> Hint: `Nominal Target`, _NumbersOnly_, Rename: `Input_NominalTarget`.
   - TextBox 3 -> Hint: `Tanggal Target`, Rename: `Input_TanggalTarget`.
   - Button -> Text: `Simpan Target`, Rename: `Tombol_SimpanTarget`.
4. **Wadah Info Target:** Tarik **VerticalArrangement** baru (Rename: `Wadah_Info`). **PENTING:** Hilangkan centang **Visible** di Properties. Di dalamnya tarik:
   - 3 Label -> Rename: `Teks_InfoNama`, `Teks_InfoNominal`, `Teks_InfoTanggal`.
   - Button -> Text: `Hapus & Buat Baru Target`, Rename: `Tombol_HapusTarget`.
5. **Alat Tambahan:** Tarik **TinyDB** (`Database_Utama`) dan **Notifier** (`Pesan_Notif`).

### B. Kode (Blocks)

Pindah ke **Blocks**.

1. **Menghitung Saldo & Cek Target (Saat Layar Dibuka):**
   - Tarik blok kuning `when ProgresTabungan.Initialize do`.
   - **Saldo:** Set `Teks_SaldoOtomatis.Text` dengan `join` (`"Saldo Saat Ini: Rp "` digabung blok `-` antara `GetValue` tag `"TotalPemasukan"` dan `GetValue` tag `"TotalPengeluaran"`).
   - **Cek Target:** Gunakan `if then else`. Jika `GetValue` tag `"Target_Nama"` sama dengan teks kosong `" "`:
     - **Then:** set `Wadah_Input.Visible` ke `true`, set `Wadah_Info.Visible` ke `false`.
     - **Else:** set `Wadah_Input.Visible` ke `false`, set `Wadah_Info.Visible` ke `true`. Lalu set teks `Teks_InfoNama`, `Teks_InfoNominal`, `Teks_InfoTanggal` dengan `GetValue` tag masing-masing.
2. **Tombol Simpan Target:**
   - Saat `Tombol_SimpanTarget.Click`: Gunakan `StoreValue` untuk menyimpan `"Target_Nama"`, `"Target_Nominal"`, dan `"Target_Tanggal"` dari input form.
   - Set `Wadah_Input.Visible` `false`, `Wadah_Info.Visible` `true`. Tampilkan Notifier `"Target Berhasil Dibuat!"`.
3. **Tombol Hapus Target:**
   - Saat `Tombol_HapusTarget.Click`: Gunakan `StoreValue` isi tag `"Target_Nama"` dengan teks kosong `" "`.
   - Set `Wadah_Input.Visible` `true`, `Wadah_Info.Visible` `false`.

> **PENTING:** Jangan lupa Save project Anda. Coba jalankan secara penuh mulai dari login, input pemasukan/pengeluaran, hingga mengecek Progres Tabungan!
