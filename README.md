# Isyarat Ceria ✨  
**Aplikasi Android Pembelajaran Bahasa Isyarat Interaktif & Ramah Anak**

Isyarat Ceria adalah aplikasi Android berbasis Java yang dirancang khusus dengan tema kanak-kanak untuk membantu proses belajar bahasa isyarat (alfabet dan kata sederhana) menjadi lebih menyenangkan, interaktif, dan mudah dipahami. 

Aplikasi ini menggunakan arsitektur data lokal (JSON & SharedPreferences) yang ringan, menjadikannya sangat cepat dijalankan tanpa koneksi internet (*offline*) serta mudah untuk dikembangkan lebih lanjut (*scalable*).

---

## 🚀 Fitur Utama Uygulama

Saat ini, aplikasi memiliki **5 fitur utama** yang saling terintegrasi:

1. **📚 Modul Belajar (Daftar Isyarat)**
   Menampilkan daftar lengkap huruf dan kata bahasa isyarat dalam bentuk kartu visual yang menarik (*CardView*) menggunakan komponen `RecyclerView` yang efisien.
   
2. **🔊 Detail Isyarat**
   Ketika salah satu isyarat ditekan, halaman detail akan terbuka menampilkan gambar berukuran besar dan petunjuk gerakan yang jelas. Dilengkapi dengan tombol pengucapan suara bertenaga AI (*Text-to-Speech*) dalam Bahasa Indonesia.

3. **⭐ Kata Favorit Pengguna**
   Anak-anak dapat menandai huruf atau kata yang mereka sukai menggunakan tombol bintang. Item terpilih akan disimpan secara permanen ke `SharedPreferences` dan dapat diakses dengan mudah pada halaman khusus "Kata Favoritku".

4. **🎮 Kuis Tebak Isyarat & Skor Tertinggi**
   Menguji pemahaman dengan menampilkan isyarat acak tanpa teks bantuan. Setiap jawaban benar menghasilkan +10 poin. Jika skor akhir kuis berhasil melampaui rekor sebelumnya, sistem akan memperbarui rekor *High Score* di Menu Utama secara *real-time*.

5. **⏱️ Kuis Ketangkasan dengan Timer**
   Menguji pemahaman dengan menampilkan isyarat acak tanpa teks bantuan. Setiap soal dilengkapi dengan **hitungan mundur 15 detik** menggunakan `CountDownTimer`. Teks waktu akan berubah menjadi merah saat kritis (< 5 detik), dan jika waktu habis soal otomatis dianggap salah untuk melatih ketangkasan anak.

---

## 🛠️ Struktur Kode & Manajemen Data

Aplikasi ini dibangun menggunakan bahasa pemrograman **Java** dengan komponen utama sebagai berikut:

* **`MainActivity.java`**: Menu utama aplikasi, menampilkan navigasi fitur dan pemuatan *high score*.
* **`LearnActivity.java`**: Membaca data JSON lokal dan menampilkannya ke dalam `RecyclerView`.
* **`SignAdapter.java`**: Menghubungkan data model dengan tampilan kartu isyarat dan menangani logika interaksi (klik detail & favorit).
* **`DetailActivity.java`**: Mengurus tampilan detail visual serta integrasi mesin *Text-to-Speech* Android.
* **`FavoriteActivity.java`**: Menyaring dan menampilkan daftar item yang telah ditandai favorit oleh pengguna.
* **`QuizActivity.java`**: Mengatur jalannya kuis (pengacakan soal dengan `Collections.shuffle`) dan kalkulasi skor akhir.
* **`SignModel.java`**: Kelas model objek data (*POJO*) terstruktur.

### 📦 Penyimpanan Data Lokal:
* **`assets/sign_language_data.json`**: Berfungsi sebagai *database* lokal yang menampung relasi ID, teks huruf/kata, nama file gambar, dan teks deskripsi arti gerakan.
* **`res/drawable/`**: Menyimpan seluruh aset ilustrasi bahasa isyarat tangan berformat `.png` transparan (menggunakan nama file huruf kecil dengan pemisah *underscore*, contoh: `sign_a.png`).
* **`SharedPreferences`**: Digunakan untuk menyimpan data progres yang bersifat persisten (Skor tertinggi kuis dan Set ID dari item favorit).

---

## 🎨 Palet Warna Tema Anak (Kids Theme)

Desain antarmuka aplikasi ini menggunakan skema warna pastel cerah yang kontras namun tetap lembut di mata anak-anak:
* **Biru Ceria (`#4D96FF`)** — Warna Utama / Header / Kuis
* **Merah Muda (`#FF6B6B`)** — Aksen / Tombol Mulai Belajar
* **Kuning Bintang (`#FFD93D`)** — Sorotan / Skor / Tombol Favorit
* **Hijau Daun (`#6BCB77`)** — Notifikasi Jawaban Benar / Tombol Kuis

---

## 📈 Rencana Pengembangan Selanjutnya (*Scalability Roadmap*)

Arsitektur aplikasi ini sengaja dibuat mandiri agar siap dikembangkan ke skala yang lebih besar di masa mendatang:
1. **Migrasi ke MVVM Pattern:** Memisahkan logika data menggunakan `ViewModel` dan `Repository` agar kode semakin bersih.
2. **Migrasi ke Room Database:** Mengganti pembacaan *raw* file JSON dengan database lokal SQLite/Room jika jumlah kata isyarat sudah mencapai ratusan atau ribuan.
3. **Kuis Pilihan Ganda:** Mengubah kolom input ketik teks pada `QuizActivity` menjadi 4 pilihan tombol opsi dinamis.
4. **Kategori Materi:** Memisahkan data JSON menjadi beberapa segmen (Kategori Alfabet, Angka, dan Kata Sehari-hari).
5. **Animasi Lottie & Audio:** Menambahkan animasi bintang/kembang api (`LottieAnimationView`) serta efek suara ceria saat anak menjawab kuis dengan benar.

---

## 📄 Lisensi

Proyek ini dibuat untuk tujuan edukasi pembelajaran bahasa isyarat yang inklusif bagi anak-anak.
