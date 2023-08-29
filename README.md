# Dokumentasi Standard Bahasa Pemrograman Go (Golang)

Selamat datang di dokumentasi standard bahasa pemrograman Go! Dokumentasi ini akan memberikan panduan tentang cara mengembangkan aplikasi dengan bahasa Go.

## Pendahuluan

### Tujuan Dokumentasi

Dokumentasi ini dibuat untuk menghadirkan pedoman dan panduan standar dalam mengembangkan proyek dalam bahasa Go di perusahaan. Tujuan utamanya adalah meningkatkan konsistensi, kualitas, dan efisiensi pengembangan perangkat lunak.

### Ruang Lingkup

Dokumentasi ini mencakup praktik terbaik dalam penggunaan bahasa Go, struktur proyek, panduan penulisan kode, pengujian, serta alur kerja kolaborasi.

### Referensi

- [Dokumentasi Resmi Go](https://go.dev/doc/)
- [Effectice Go](https://go.dev/doc/effective_go)
- [Go Project Layout](https://github.com/golang-standards/project-layout)

## Struktur Proyek

### Pembagian Direktori

Proyek-proyek harus mengikuti struktur direktori yang seragam. Berikut adalah struktur yang direkomendasikan:

```
nama_proyek/
├── cmd/
│   ├── main.go
├── internal/
├── pkg/
├── api/
├── tests/
├── sripts/
└── README.md
```

Untuk penjelasan lengkap setiap direktori dapat lihat di [Go Project Layout](https://github.com/golang-standards/project-layout)

### Modul Go

Modul Go harus diaktifkan untuk setiap proyek dengan menjalankan perintah berikut:

```go
go mod init nama-proyek
```

## Pedoman Penulisan Kode

### Penamaan

- Gunakan gaya penamaan camelCase untuk nama variabel, fungsi, metode, dan struktur.
- Nama fungsi atau metode harus menggambarkan tindakan yang dilakukan.
- Nama variabel harus deskriptif dan mengandung informasi tentang penggunaannya.

### Komentar Kode

- Gunakan komentar yang jelas dan informatif untuk menjelaskan algoritma, logika kompleks, atau tujuan fungsi.

## Panduan Pengujian

### Unit Testing

- Unit testing harus dilakukan untuk setiap fungsi atau metode yang ditulis.
- Gunakan paket `testing` bawaan Go untuk menulis unit test.

## Alur Kerja Kolaborasi

### Version Control

- Gunakan Git sebagai sistem kontrol versi utama.

### Pull Request

- Pull request (PR) harus melewati ulasan kode oleh rekan tim sebelum di-merge.

## Dokumentasi

### Komentar dalam Kode

- Semua komentar kode harus dijelaskan dengan komentar yang jelas.

### Dokumentasi Eksternal

- Buat dokumentasi eksternal yang mencakup penggunaan proyek, panduan instalasi, dan contoh penggunaan.

## Lisensi

- Pastikan penggunaan lisensi yang diizinkan.
