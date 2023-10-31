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

- [Go vs PHP](https://github.com/gemm123/standard-go/blob/master/perbandingan/go-php/README.md)
- [Go vs Python](https://github.com/gemm123/standard-go/blob/master/perbandingan/go-python/README.md)
- [Go vs Node.js](https://github.com/gemm123/standard-go/blob/master/perbandingan/go-nodejs/README.md)
- [Go vs Java](https://github.com/gemm123/standard-go/blob/master/perbandingan/go-java/README.md)

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

## E. Go Dasar

- [Go Modules](https://github.com/gemm123/standard-go/blob/master/go-dasar/go-modules/README.md)
- [Go Command](https://github.com/gemm123/standard-go/blob/master/go-dasar/go-command/README.md)
- [Program Pertama: Hello World](https://github.com/gemm123/standard-go/blob/master/go-dasar/program-pertama/README.md)
- [Variabel](https://github.com/gemm123/standard-go/blob/master/go-dasar/variabel/README.md)
- [Tipe Data](https://github.com/gemm123/standard-go/blob/master/go-dasar/tipe-data/README.md)
- [Operator](https://github.com/gemm123/standard-go/blob/master/go-dasar/operator/README.md)
- [Seleksi Kondisi](https://github.com/gemm123/standard-go/blob/master/go-dasar/seleksi-kondisi/README.md)
- [Perulangan](https://github.com/gemm123/standard-go/blob/master/go-dasar/perulangan/README.md)
- [Array](https://github.com/gemm123/standard-go/blob/master/go-dasar/array/README.md)
- [Slice](https://github.com/gemm123/standard-go/blob/master/go-dasar/slice/README.md)
- [Map](https://github.com/gemm123/standard-go/blob/master/go-dasar/map/README.md)
- [Fungsi](https://github.com/gemm123/standard-go/blob/master/go-dasar/fungsi/README.md)
- [Pointer](https://github.com/gemm123/standard-go/blob/master/go-dasar/pointer/README.md)
- [Struct](https://github.com/gemm123/standard-go/blob/master/go-dasar/struct/README.md)
- [Method](https://github.com/gemm123/standard-go/blob/master/go-dasar/method/README.md)
- [Properti Public dan Private](https://github.com/gemm123/standard-go/blob/master/go-dasar/properti-public-private/README.md)
- [Interface](https://github.com/gemm123/standard-go/blob/master/go-dasar/interface/README.md)
- [Goroutine](https://github.com/gemm123/standard-go/blob/master/go-dasar/goroutine/README.md)
- [Channel](https://github.com/gemm123/standard-go/blob/master/go-dasar/channel/README.md)
- [Defer & Exit](https://github.com/gemm123/standard-go/blob/master/go-dasar/defer-exit/README.md)
- [Error, Panic, & Recover](https://github.com/gemm123/standard-go/blob/master/go-dasar/error-panic-recover/README.md)
- [Layout Format String](https://github.com/gemm123/standard-go/blob/master/go-dasar/layout-format-string/README.md)
- [Unit Test](https://github.com/gemm123/standard-go/blob/master/go-dasar/unit-test/README.md)
- [Wait Group](https://github.com/gemm123/standard-go/blob/master/go-dasar/wait-group/README.md)
- [Mutex](https://github.com/gemm123/standard-go/blob/master/go-dasar/mutex/README.md)
- [Go Vendoring](https://github.com/gemm123/standard-go/blob/master/go-dasar/go-vendoring/README.md)
- [Go Generics](https://github.com/gemm123/standard-go/blob/master/go-dasar/go-generics/README.md)

## F. Convention Code

### Penamaan file

- Go mengikuti konvensi di mana semua file sumber menggunakan huruf kecil dengan garis bawah yang memisahkan beberapa kata.
- Nama file gabungan dipisahkan dengan _.
- Nama file yang dimulai dengan “.” atau “_” diabaikan oleh go.
- File dengan akhiran `_test.go` hanya dikompilasi dan dijalankan oleh alat `go test`.

### Penamaan Variabel dan Fungsi

- Gunakan huruf kapital awal untuk nama yang akan diekspor (publik). Misalnya, `MyPublicFunction`.
- Gunakan huruf kecil untuk nama yang tidak diekspor (privat). Misalnya, `myPrivateFunction`.
- Hindari pemakaian singkatan jika tidak diperlukan.
- *Constant* harus menggunakan huruf kapital semua dan menggunakan garis bawah `_` untuk memisahkan kata.

### Error Handling

- Golang menganjurkan penggunaan multiple return values untuk error handling. Biasanya, hasil fungsi disertai dengan nilai error yang akan diuji setelah pemanggilan fungsi.
- Gunakan `if err != nil` untuk menangani kesalahan. Jangan mengabaikan error yang dikembalikan oleh fungsi.

### Pengelolaan Dependensi

Gunakan Go Modules (go mod) untuk mengelola dependensi.

## G. Go Lanjut

- [Project Layout Structure](https://github.com/gemm123/standard-go/blob/master/go-lanjut/project-layout-structure/README.md)
  
   Ada open source project yang sangat menarik untuk dipelajari, yaitu project-layout. Project tersebut isinya adalah project 
   layout pada Go yang merupakan hasil kombinasi dari banyak project layout Go terkenal, seperti kubernetes, nats.io, istio, 
   termasuk juga layout dari source code Go itu sendiri.


- [Go Web Framework](https://github.com/gemm123/standard-go/blob/master/go-lanjut/go-web-framework/README.md)

  Di Go, sama seperti bahasa pemrograman lainnya, ada banyak library dan framework yang siap pakai. Ada framework yang sifatnya 
  sudah komplit, lengkap isinya dari ujung ke ujung, mulai dari setup project hingga testing dan build/deployment sudah ada 
  semua tooling-nya. Ada juga framework yg scope-nya lebih spesifik (biasa disebut library), seperti lib untuk mempermudah 
  operasi di data layer, lib untuk routing, dan lainnya.


- [Go Library](https://github.com/gemm123/standard-go/blob/master/go-lanjut/go-library/README.md)

  Library dalam bahasa pemrograman Go (Golang) merujuk pada kumpulan paket atau modul yang telah dikembangkan dan dapat digunakan 
  kembali untuk menyederhanakan pengembangan perangkat lunak. Go memiliki ekosistem library yang cukup luas, yang mencakup 
  berbagai bidang seperti pemrosesan data, pengembangan web, keamanan, dan lainnya. Dengan menggunakan library, para pengembang 
  dapat menghemat waktu dan upaya dalam membangun aplikasi, karena mereka dapat memanfaatkan kode yang sudah ada untuk menyelesaikan 
  tugas-tugas umum atau kompleks.

