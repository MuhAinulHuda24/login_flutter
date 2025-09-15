# login_flutter

Proyek ini adalah aplikasi Flutter sederhana yang mendemonstrasikan fungsionalitas dasar autentikasi pengguna, meliputi halaman Login, Registrasi, dan Beranda (Home).

## Fitur
-   **Registrasi Pengguna**: Pengguna dapat mendaftarkan akun baru dengan nama lengkap, email, dan password.
-   **Login Pengguna**: Pengguna yang sudah terdaftar dapat masuk menggunakan email dan password.
-   **Logout**: Pengguna dapat keluar dari akunnya dan kembali ke halaman login.
-   **Simulasi Database**: Menggunakan `Map` di dalam Dart untuk menyimulasikan database pengguna secara lokal.

## Struktur Proyek
Berikut adalah file-file utama dalam proyek ini:
-   `lib/main.dart`: Titik masuk utama aplikasi. Mengatur tema dan halaman awal.
-   `lib/login_page.dart`: Berisi UI dan logika untuk halaman login.
-   `lib/register_page.dart`: Berisi UI dan logika untuk halaman registrasi.
-   `lib/home_page.dart`: Halaman yang ditampilkan setelah pengguna berhasil login.
-   `lib/data/user_data.dart`: File untuk simulasi database pengguna menggunakan struktur data `Map`.

## Langkah-Langkah Praktikum

### 1. Inisialisasi Proyek dan Penyiapan Dependensi
Proyek ini dibuat menggunakan `flutter create`. Dependensi yang ditambahkan adalah `google_fonts` untuk kustomisasi teks.

### 2. Simulasi Database Pengguna
Untuk menyederhanakan proses, data pengguna disimpan dalam sebuah `Map` global di `lib/data/user_data.dart`. Kunci dari `Map` adalah email pengguna, dan nilainya adalah `Map` lain yang berisi nama lengkap dan password.

```dart
// lib/data/user_data.dart
Map<String, Map<String, String>> userData = {
  'test@email.com': {
    'fullName': 'Test User',
    'password': 'password123',
  },
};
```

### 3. Membuat Halaman Registrasi (`register_page.dart`)
-   **UI**: Halaman ini terdiri dari beberapa `TextField` untuk input nama, email, dan password, serta sebuah `ElevatedButton` untuk submit. `TextEditingController` digunakan untuk mengambil data dari input.
-   **Logika**:
    1.  Saat tombol "Register" ditekan, fungsi `_register` akan dijalankan.
    2.  Fungsi ini mengambil teks dari setiap controller dan melakukan validasi sederhana untuk memastikan tidak ada field yang kosong.
    3.  Jika valid, data pengguna baru akan ditambahkan ke dalam `Map` `userData`.
    4.  Sebuah `AlertDialog` ditampilkan untuk memberitahu bahwa registrasi berhasil, dan pengguna diarahkan kembali ke halaman login.

### 4. Membuat Halaman Login (`login_page.dart`)
-   **UI**: Mirip dengan halaman registrasi, halaman ini memiliki `TextField` untuk email dan password, serta tombol "Login".
-   **Logika**:
    1.  Fungsi `_login` akan dijalankan saat tombol "Login" ditekan.
    2.  Fungsi ini memeriksa apakah email yang dimasukkan ada di dalam `userData` dan apakah password-nya cocok.
    3.  Jika berhasil, pengguna akan diarahkan ke `HomePage` menggunakan `Navigator.pushReplacement` agar tidak bisa kembali ke halaman login dengan tombol "back".
    4.  Jika gagal, `AlertDialog` akan muncul dengan pesan error.

### 5. Membuat Halaman Beranda (`home_page.dart`)
-   **UI**: Halaman ini bersifat `StatelessWidget` yang menampilkan pesan selamat datang beserta nama lengkap pengguna yang berhasil login. Nama ini diterima melalui constructor.
-   **Logika**: Terdapat tombol "Logout" yang ketika ditekan akan mengarahkan pengguna kembali ke `LoginPage`. Navigasi ini menggunakan `Navigator.pushAndRemoveUntil` untuk menghapus semua riwayat navigasi sebelumnya, sehingga pengguna tidak bisa kembali ke `HomePage` setelah logout.

### 6. Navigasi dan Pengelolaan State
-   **Navigasi**: Proyek ini menggunakan `MaterialPageRoute` untuk berpindah antar halaman.
    -   `Navigator.push()`: Untuk pindah ke halaman registrasi.
    -   `Navigator.pop()`: Untuk kembali dari halaman registrasi atau menutup dialog.
    -   `Navigator.pushReplacement()`: Digunakan setelah login berhasil.
    -   `Navigator.pushAndRemoveUntil()`: Digunakan untuk proses logout.
-   **State Management**: State dikelola secara lokal di setiap halaman yang membutuhkannya (`LoginPage` dan `RegisterPage`) menggunakan `StatefulWidget` dan `setState`.

## Cara Menjalankan Proyek
1.  Pastikan sudah menginstal Flutter SDK.
2.  Clone repositori ini.
3.  Buka terminal di direktori proyek, lalu jalankan `flutter pub get` untuk menginstal dependensi.
4.  Jalankan aplikasi dengan `flutter run`.

### HAsil Akhir
**login :**
<img width="329" height="694" alt="image" src="https://github.com/user-attachments/assets/68ebf4c1-c916-44bc-a3f6-a3a5a9cb1614" />

**Register :**
<img width="329" height="693" alt="image" src="https://github.com/user-attachments/assets/64fe095e-7746-41b7-bbbc-82f542f20807" />

**Setelah Register :**
<img width="323" height="689" alt="image" src="https://github.com/user-attachments/assets/8f2d4478-63f6-42ed-be68-954abd0b514a" />

**Ketika Login password / email salah :**
<img width="326" height="695" alt="image" src="https://github.com/user-attachments/assets/25c897ea-98b1-4e94-8e42-855edfa1839d" />

**Berhasil Login :**
<img width="328" height="691" alt="image" src="https://github.com/user-attachments/assets/24635342-b000-4675-9336-5c9b66512792" />




