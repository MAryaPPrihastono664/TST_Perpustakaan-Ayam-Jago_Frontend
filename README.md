# TST_Perpustakaan-Ayam-Jago_Frontend


Aplikasi web manajemen perpustakaan modern yang dibangun menggunakan **Vanilla JavaScript** dan **Bootstrap 5**. Frontend ini berinteraksi dengan REST API backend untuk pengelolaan buku dan peminjaman, serta mengintegrasikan **Microservice External** untuk menampilkan rating/ulasan buku secara real-time.

**Live Demo:** [[https://tst-perpustakaan-ayam-jago-frontend.vercel.app](https://tst-perpustakaan-ayam-jago-frontend.vercel.app)]

---

## Fitur Utama

### 1. Otentikasi & Keamanan
* **Login & Register:** Sistem otentikasi menggunakan **JWT (JSON Web Token)**.
* **Auto Redirect:** Proteksi halaman (user tanpa token otomatis diarahkan ke login).
* **Session Handling:** Token disimpan aman di LocalStorage dan divalidasi setiap request.

### 2. Manajemen Buku (Dashboard)
* **Katalog Buku:** Menampilkan daftar buku dengan pagination.
* **Pencarian (Search):** Mencari buku berdasarkan judul secara real-time.
* **Stock Monitoring:** Indikator visual jika stok buku habis.

### 3. Integrasi Microservice (External Rating)
Fitur unggulan yang mengambil data dari sumber eksternal tanpa membebani backend utama.
* Setiap kartu buku melakukan *asynchronous request* ke API `thegift.theokaitou.my.id`.
* Menampilkan **Average Rating** (Bintang) jika buku ditemukan di database eksternal.
* Fallback tampilan jika data review tidak tersedia.

### 4. Transaksi Peminjaman
* **Pinjam Buku:** Validasi stok sebelum meminjam.
* **Pengembalian:** Riwayat peminjaman lengkap dengan status (Borrowed/Returned).
* **History:** Tab khusus untuk melihat jejak peminjaman user.

---

## Teknologi yang Digunakan

* **Core:** HTML5, CSS3, JavaScript (ES6+).
* **Styling:** [Bootstrap 5.3](https://getbootstrap.com/) (Responsive Design) & FontAwesome Icons.
* **HTTP Client:** Fetch API (Native Browser).
* **Deployment:** Vercel.

---

## Integrasi API

Frontend ini menghubungkan dua layanan API yang berbeda:

| Layanan | Endpoint Base URL | Fungsi |
| :--- | :--- | :--- |
| **Main Backend** | `https://arya.theokaitou.my.id/api` | Auth, Data Buku, Stok, Transaksi Peminjaman. |
| **Rating Service** | `https://thegift.theokaitou.my.id/` | Microservice publik untuk mengambil rating buku. |

---

## Struktur File

```text
/
├── index.html      # Dashboard Utama (Katalog & Riwayat)
├── login.html      # Halaman Masuk
├── register.html   # Halaman Pendaftaran
├── debug.html      # (Optional) Tool untuk cek koneksi token
└── README.md       # Dokumentasi Proyek