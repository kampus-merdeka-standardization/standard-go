# Go Command

Pengembangan aplikasi Go tak jauh dari hal-hal yang berbau CLI atau _Command Line Interface_. Proses inisialisasi project,
kompilasi, testing, eksekusi program, semuanya dilakukan lewat command line.

## Command `go mod init`

_Command_ `go mod init` digunakan untuk inisialisasi project pada Go (menggunakan Go Modules). Untuk nama project bisa menggunakan
apapun, tapi umumnya adalah disamakan dengan nama direktori. Nama project ini penting karena nantinya berpengaruh pada
_import path sub packages_ yang ada dalam project tersebut.

```shell
mkdir <nama-project>
cd <nama-project>
go mod init <nama-project>
```
## Command `go run`

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
## Command `go test`

Go menyediakan package `testing`, berguna untuk keperluan unit test. File yang akan di-test harus memiliki akhiran `_test.go`.
Berikut adalah contoh penggunaan _command_ `go test`.
```go
go test main_test.go
```

## Command `go build`

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

## Command `go get`

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

## Command `go mod tidy`

_Command_ `go mod tidy` digunakan untuk memvalidasi dependensi. Jika ada dependensi yang belum ter-download, maka akan otomatis
di-download.

## Command `go mod vendor`

_Command_ ini digunakan untuk vendoring. Vendoring di GO merupakan kapabilitas untuk mengunduh semua dependensi atau 3rd
_party_, untuk disimpan di lokal dalam folder project, dalam folder bernama `vendor`. Dengan adanya folder tersebut, maka Go
tidak akan _lookup_ 3rd _party_ ke cache folder, melainkan langsung mempergunakan yang ada dalam folder `vendor`. Jadi tidak
perlu download lagi dari internet.