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

### Ringkasan

Berikut ini merupakan tata letak dasar untuk proyek aplikasi Go. ini `bukan standar resmi yang ditetapkan oleh tim pengembang inti Go`; namun, ini merupakan sejumlah pola tata letak proyek historis dan terkini yang umumnya digunakan dalam ekosistem Go. Beberapa pola ini lebih populer daripada yang lain.

### Pembagian Direktori

Proyek-proyek harus mengikuti struktur direktori yang seragam. Berikut adalah struktur yang direkomendasikan:

```
nama_proyek/
├── cmd/
├── internal/
├── pkg/
├── api/
├── tests/
├── sripts/
└── README.md
```

`/cmd`

Aplikasi utama untuk proyek ini.

Nama direktori untuk setiap aplikasi harus sesuai dengan nama file eksekusi yang diinginkan (misalnya, `/cmd/app`).

Jangan menempatkan banyak kode di dalam direktori aplikasi. Jika anda berpikir bahwa kode tersebut dapat diimpor dan digunakan dalam proyek lain, maka kode tersebut harus ditempatkan di dalam direktori `/pkg`. Jika kode tersebut tidak dapat digunakan kembali atau jika anda tidak ingin orang lain menggunakannya kembali, letakkan kode tersebut di dalam direktori `/internal`.

Biasanya, terdapat fungsi `main` kecil yang mengimpor dan memanggil kode dari direktori `/internal` dan `/pkg`, dan tidak ada yang lain.

Untuk contoh-contoh lebih lanjut bisa lihat berikut:

- https://github.com/prometheus/prometheus/tree/main/cmd
- https://github.com/influxdata/influxdb/tree/master/cmd
- https://github.com/kubernetes/kubernetes/tree/master/cmd

`/internal`

Kode aplikasi dan library privat. Ini adalah kode anda yang tidak ingin diimpor oleh aplikasi atau library lain. Perlu dicatat bahwa pola tata letak ini dipaksakan atau dijaga oleh kompiler Go itu sendiri. Pehatikan bahwa anda tidak tidak dibatasi pada direktori top level `internal` saja. Anda dapat memiliki banyak lebih dari satu direktori `internal` di setiap tingkatan proyek ada.

Secara opsional anda dapat menambahkan struktur tambahan ke paket internal anda, untuk memisahkan kode internal yang bersifat shared dan non-shared. Hal ini tidak diwajibkan (terutama untuk proyek-proyek kecil), tetapi bagus untuk memiliki petunjuk visual yang menunjukkan penggunaan paket yang dimaksudkan.

Sebenernya kode aplikasi dapat ditempatkan di direktori `/internal/app` (misalnya, `/internal/app/myapp`) dan kode yang dibagikan oleh aplikasi tersebut dapat ditempatkan di direktori `/internal/pkg` (mislanya, `/internal/pkg/myprivlib`).

`/pkg`

Kode library yang boleh digunakan oleh aplikasi eksternal (misalnya, `/pkg/mypubliclib`). Proyek lain akan mengimpor library ini dengan harapan dapat berfungsi. Direktori `internal`adalah cara yang lebih baik untuk memastikan paket pribadi anda tidak dapat diimpor karena dijaga oleh Go. Namun, direktori `/pkg` tetap cara yang baik untuk mengkonsumsi secara eksplisit bahwa kode di dalam direktori tersebut aman digunakan oleh orang lain.

Untuk contoh-contoh lebih lanjut bisa lihat berikut:

- https://github.com/kubernetes/kubernetes/tree/master/pkg
- https://github.com/grafana/grafana/tree/master/pkg
- https://github.com/influxdata/influxdb/tree/master/pkg

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
