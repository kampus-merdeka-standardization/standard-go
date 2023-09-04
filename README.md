# Dokumentasi Standard Bahasa Pemrograman Go (Golang)

Selamat datang di dokumentasi standard bahasa pemrograman Go! Dokumentasi ini akan memberikan panduan tentang cara mengembangkan 
aplikasi dengan bahasa Go.

## A. Pendahuluan

### Tujuan Dokumentasi

Dokumentasi ini dibuat untuk menghadirkan pedoman dan panduan standar dalam mengembangkan proyek dalam bahasa Go di perusahaan. 
Tujuan utamanya adalah meningkatkan konsistensi, kualitas, dan efisiensi pengembangan perangkat lunak.

### Ruang Lingkup

Dokumentasi ini mencakup pengenalan bahasa Go, praktik terbaik dalam penggunaan bahasa Go, struktur proyek, panduan 
penulisan kode, serta alur kerja kolaborasi.

### Referensi

- [Dokumentasi Resmi Go](https://go.dev/doc/)
- [Effectice Go](https://go.dev/doc/effective_go)
- [Go Project Layout](https://github.com/golang-standards/project-layout)
- [Dasar Pemrograman Golang](https://dasarpemrogramangolang.novalagung.com/)

## B. Pengenalan

Golang (atau biasa disebut dengan Go) adalah bahasa pemrograman yang dikembangkan di Google oleh Robert Griesemer, 
Rob Pike, dan Ken Thompson pada tahun 2007 dan mulai diperkenalkan ke publik tahun 2009. Penciptaan bahasa Go didasari 
bahasa C dan C++, oleh karena itu gaya sintaksnya mirip.

### Kelebihan Golang

- Mendukung konkurensi di level bahasa dengan pengaplikasian cukup mudah.
- Mendukung pemrosesan data dengan banyak prosesor dalam waktu yang bersamaan (pararel processing).
- Memiliki garbage collector.
- Proses kompilasi sangat cepat.
- Bukan bahasa pemrograman yang hirarkial dan bukan strict OOP, memberikan kebebasan ke developer perihal bagaimana cara 
penulisan kode.
- Dependensi dan tooling yang disediakan terbilang lengkap.
- Dukungan komunitas sangat bagus. Banyak tools yang tersedia secara gratis dan open source yang bisa langsung dimanfaatkan.
- Sudah banyak industri dan perusahaan yg menggunakan Go sampai level production, termasuk di antaranya adalah Google 
sendiri.

### Kekurangan Golang

- Golang relatif muda dalam hal umur bahasa pemrograman. Hal ini berarti lebih sedikit library yang ada, terutama 
ketika berinteraksi dengan platform lain.
- Karena usia bahasa pemrograman yang bisa dibilang muda, Komunitas bahasa pemrograman ini mungkin tidak sebesar bahasa-bahasa 
pemrograman lain di luar sana.

## C. Perbandingan Go dengan Bahasa Lain

- [Go vs PHP](https://github.com/gemm123/standard-go/perbandingan/go-php/README.md)
- [Go vs Python](https://github.com/gemm123/standard-go/perbandingan/go-python/README.md)
- [Go vs Node.js](https://github.com/gemm123/standard-go/perbandingan/go-nodejs/README.md)
- [Go vs Java](https://github.com/gemm123/standard-go/perbandingan/go-java/README.md)

## D. Instalasi Golang

### Windows

1. Download terlebih dahulu installer-nya di https://golang.org/dl/. Pilih installer untuk sistem operasi Windows sesuai jenis bit yang digunakan.
2. Setelah ter-download, jalankan installer, klik next hingga proses instalasi selesai. By default jika anda tidak merubah path pada saat instalasi, Go akan ter-install di C:\go. Path tersebut secara otomatis akan didaftarkan dalam PATH environment variable.
3. Buka Command Prompt / CMD, eksekusi perintah berikut untuk mengecek versi Go.
    ```shell 
    go version
    ````
4. Jika output adalah sama dengan versi Go yang ter-install, menandakan proses instalasi berhasil.

### MacOS

Cara termudah instalasi Go di MacOS adalah menggunakan [Homebrew](https://brew.sh).

1. Install terlebih dahulu Homebrew (jika belum ada), caranya jalankan perintah berikut di terminal.
    ```shell
    $ ruby -e "$(curl -fsSL http://git.io/pVOl)"
    ```
2. Install Go menggunakan command brew.
    ```shell
    $ brew install go
    ```
3. Tambahkan path binary Go ke PATH environment variable.
    ```shell
    $ echo "export PATH=$PATH:/usr/local/go/bin" >> ~/.bash_profile
    $ source ~/.bash_profile
    ```
4. Jalankan perintah berikut mengecek versi Go.
    ```shell
    go version
    ```
5. Jika output adalah sama dengan versi Go yang ter-install, menandakan proses instalasi berhasil.

### Linux

1. Unduh arsip installer dari https://golang.org/dl/, pilih installer untuk Linux yang sesuai dengan jenis bit komputer anda. 
Proses download bisa dilakukan lewat CLI, menggunakan `wget` atau `curl`.
    ```shell
    $ wget https://storage.googleapis.com/golang/go1...
    ```
2. Buka terminal, extract arsip tersebut ke /usr/local.
    ```shell
    $ tar -C /usr/local -xzf go1...
    ```
3. Tambahkan path binary Go ke PATH environment variable.
    ```shell
    $ echo "export PATH=$PATH:/usr/local/go/bin" >> ~/.bashrc
    $ source ~/.bashrc
    ```
4. Selanjutnya, eksekusi perintah berikut untuk mengetes apakah Go sudah terinstal dengan benar.
    ```shell
    go version
    ```
5. Jika output adalah sama dengan versi Go yang ter-install, menandakan proses instalasi berhasil.

### Variabel `GOROOT`

By default, setelah proses instalasi Go selesai, secara otomatis akan muncul environment variable GOROOT. Isi dari 
variabel ini adalah lokasi di mana Go ter-install. Sebagai contoh di Windows, ketika Go di-install di C:\go, maka path 
tersebut akan menjadi isi dari GOROOT. Silakan gunakan command go env untuk melihat informasi konfigurasi environment yang ada.

## E. Go Modules

### Penjelasan

Go modules meruapakan manajemen dependensi resmi untuk Go. Modules ini diperkenalkan pertama kali di `go1.11`, sebemum itu
pengembangan project Go dilakukan dalam `GOPATH`. Modules digunakan untuk menginisialisasi sebuah project, sekaligus melakukan
manajemen terhadap 3rd party atau library lain yang dipergunakan. Modules penggunaannya adalah lewat CLI. Dan jika teman-teman
sudah sukses meng-install Go, maka otomatis bisa mempergunakan Go Modules.

### Inisialisasi Project Menggunakan Go Modules

Command `go mod init` dingunakan untuk menginisialisasi project baru.
Skema penulisan command `go mod`:
```shell
go mod init <nama-project>
```
Untuk nama project, umumnya adalah simakan dengan nama direktori, tapi bisa saja sebenarnya menggunakan nama yang lain.
> Nama project dan nama module merupakan istilah yang sama

Eksekusi perintah `go mod init` menghasilkan satu buah file baru bernama `go.mod`. File ini digunakan oleh Go toolchain
untuk menandai bahwa folder di mana file tersebut berada adalah folder project.

Cukup itu saja cara inisialisasi project di Go. Sebenarnya selain Go Modules, setup project di Go juga bisa menggunakan
`$GOPATH`. Tapi inisialisasi project dengan GOPATH sudah outdate dan kurang dianjurkan untuk project-project yang dikembangkan
menggunakan Go versi terbaru (1.14 ke atas).

## F. Command

Pengembangan aplikasi Go tak jauh dari hal-hal yang berbau CLI atau _Command Line Interface_. Proses inisialisasi project,
kompilasi, testing, eksekusi program, semuanya dilakukan lewat command line.

### Command `go mod init`

_Command_ `go mod init` digunakan untuk inisialisasi project pada Go (menggunakan Go Modules). Untuk nama project bisa menggunakan
apapun, tapi umumnya adalah disamakan dengan nama direktori. Nama project ini penting karena nantinya berpengaruh pada
_import path sub packages_ yang ada dalam project tersebut.

```shell
mkdir <nama-project>
cd <nama-project>
go mod init <nama-project>
```
### Command `go run`

_Command_ `go run` digunakan untuk eksekusi file program (file ber-ekstensi `.go`). Cara penggunaannya dengan menuliskan
_command_ tersebut diikuti argumen nama file. Berikut adalah contoh penerapan `go run` untuk eksekusi file program `main.go`
```go
go run main.go
```
_Command_ `go run` hanya bisa digunakan pada file yang nama package-nya adalah `main`. Jika ada banyak file yang package-nya
`main` dan file-file tersebut berada pada satu direktori level dengan file utama, maka eksekusinya adalah dengan menuliskan
semua file sebagai argument _command_ `go run`. Contohnya bisa dilihat pada kode tersebut.
```go
go run main.go library.go
```
### Command `go test`

Go menyediakan package `testing`, berguna untuk keperluan unit test. File yang akan di-test harus memiliki akhiran `_test.go`.
Berikut adalah contoh penggunaan _command_ `go test`.
```go
go test main_test.go
```

### Command `go build`

_command_ ini digunakan untuk mengkompilasi file program. Sebenarnya ketika eksekusi program menggunakan `go run`, terjadi
proses kompilasi juga. File hasil kompilasi akan disimpan pada folder temporary untuk selanjutnya langsung dieksekusi.
Berbeda dengan `go build`, _command_ ini menghasilkan file _executable_ atau _binary_ pada folder yang sedang aktif. _Default_-nya
nama project akan otomatis dijadikan nama _binary_.

Untuk nama executable sendiri bisa diubah menggunakan flag `-o`. Contoh:
```go
go build -o <nama-executable>
go build -o program.exe
```
> Untuk sistem operasi non-windows, tidak perlu menambahkan akhiran `.exe` pada nama _binary_

### Command `go get`

_Command_ `go get` digunakan untuk men-download package. Berikut contoh ketika ingin men-download package Kafka driver untuk
Go pada project.
```go
go get github.com/segmentio/kafka-go
```
Pada contoh di atas, `github.com/segmentio/kafka-go` adalah URL package kafka-go. Package yang sudah terunduh tersimpan
dalam temporary folder yang ter-link dengan project folder di mana _command_ `go get` dieksekusi, menjadikan project tersebut
bisa meng-_import_ package terunduh.

Untuk mengunduh dependensi versi terbaru, gunakan flag `-u` pada command `go get`, misalnya:
```go
go get -u github.com/segmentio/kafka-go
```
Command `go get` harus dijalankan dalam folder project. Jika dijalankan di-luar project maka akan diunduh ke pada GOPATH.

### Command `go mod tidy`

_Command_ `go mod tidy` digunakan untuk memvalidasi dependensi. Jika ada dependensi yang belum ter-download, maka akan otomatis
di-download.

### Command `go mod vendor`

_Command_ ini digunakan untuk vendoring. Vendoring di GO merupakan kapabilitas untuk mengunduh semua dependensi atau 3rd
_party_, untuk disimpan di lokal dalam folder project, dalam folder bernama `vendor`. Dengan adanya folder tersebut, maka Go
tidak akan _lookup_ 3rd _party_ ke cache folder, melainkan langsung mempergunakan yang ada dalam folder `vendor`. Jadi tidak
perlu download lagi dari internet.

## Struktur Proyek

### Ringkasan

Berikut ini merupakan tata letak dasar untuk proyek aplikasi Go. ini `bukan standar resmi yang ditetapkan oleh tim pengembang inti Go`; 
namun, ini merupakan sejumlah pola tata letak proyek historis dan terkini yang umumnya digunakan dalam ekosistem Go. 
Beberapa pola ini lebih populer daripada yang lain.

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

Jangan menempatkan banyak kode di dalam direktori aplikasi. Jika anda berpikir bahwa kode tersebut dapat diimpor dan digunakan 
dalam proyek lain, maka kode tersebut harus ditempatkan di dalam direktori `/pkg`. Jika kode tersebut tidak dapat digunakan 
kembali atau jika anda tidak ingin orang lain menggunakannya kembali, letakkan kode tersebut di dalam direktori `/internal`.

Biasanya, terdapat fungsi `main` kecil yang mengimpor dan memanggil kode dari direktori `/internal` dan `/pkg`, 
dan tidak ada yang lain.

Untuk contoh-contoh lebih lanjut bisa lihat berikut:

- https://github.com/prometheus/prometheus/tree/main/cmd
- https://github.com/influxdata/influxdb/tree/master/cmd
- https://github.com/kubernetes/kubernetes/tree/master/cmd

`/internal`

Kode aplikasi dan library privat. Ini adalah kode anda yang tidak ingin diimpor oleh aplikasi atau library lain. 
Perlu dicatat bahwa pola tata letak ini dipaksakan atau dijaga oleh kompiler Go itu sendiri. Pehatikan bahwa anda tidak 
dibatasi pada direktori top level `internal` saja. Anda dapat memiliki banyak lebih dari satu direktori `internal` di setiap 
tingkatan proyek ada.

Secara opsional anda dapat menambahkan struktur tambahan ke paket internal anda, untuk memisahkan kode internal yang 
bersifat shared dan non-shared. Hal ini tidak diwajibkan (terutama untuk proyek-proyek kecil), tetapi bagus untuk memiliki 
petunjuk visual yang menunjukkan penggunaan paket yang dimaksudkan.

Sebenernya kode aplikasi dapat ditempatkan di direktori `/internal/app` (misalnya, `/internal/app/myapp`) dan kode yang 
dibagikan oleh aplikasi tersebut dapat ditempatkan di direktori `/internal/pkg` (mislanya, `/internal/pkg/myprivlib`).

`/pkg`

Kode library yang boleh digunakan oleh aplikasi eksternal (misalnya, `/pkg/mypubliclib`). Proyek lain akan mengimpor 
library ini dengan harapan dapat berfungsi. Direktori `internal`adalah cara yang lebih baik untuk memastikan paket 
pribadi anda tidak dapat diimpor karena dijaga oleh Go. Namun, direktori `/pkg` tetap cara yang baik untuk mengkonsumsi 
secara eksplisit bahwa kode di dalam direktori tersebut aman digunakan oleh orang lain.

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
