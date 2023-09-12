# Program Pertama: Hello World

## Inisialisasi Project

Buat direktori bernama `hello-world` bebas ditempatkan di mana. Lalu via CLI, masuk ke direktori tersebut dan jalankan 
command untuk inisialisasi project.

```shell
mkdir hello-world
cd hello-world
go mod init hello-world
```

## Menyiapkan File Program

Di dalam project yang telah dibuat, siapkan sebuah file dengan nama bebas, yang jelas harus ber-ekstensi `.go`. Pada contoh 
ini gunakan nama file `main.go`. Pembuatan file program bisa dilakukan lewat CLI atau browser, atau juga lewat editor. Pastikan 
file dibuat dalam project folder.

Di bawah ini merupakan contoh kode program sederhana untuk memunculkan text __Hello world__ ke layar output command prompt. 
Silakan salin kode berikut ke file program yang telah dibuat. Sebisa mungkin jangan copy paste. Biasakan untuk menulis dari 
awal, agar cepat terbiasa dan familiar dengan Go.

```go
package main

import "fmt"

func main() { 
    // menampilkan pesan Hello world
    fmt.Println("Hello world")
}
```

Setelah kode disalin, buka terminal (atau CMD bagi pengguna Windows), lalu masuk ke direktori proyek, kemudian jalankan 
program menggunakan perintah `go run`.

```shell
cd hello-world
go run main.go
```

Hasilnya, muncul tulisan __Hello world__ di layar console.

## Penggunaan Keyword `package`

Setiap file program harus memiliki __package__. Setiap project harus ada minimal satu file dengan nama package `main`. File yang 
ber-_package_ `main`, akan dieksekusi pertama kali ketika program di jalankan. Cara menentukan _package_ dengan menggunakan keyword 
`package`, berikut adalah contoh penulisannya.

```go
package <nama-package>
package main
```

## Penggunaan Keyword `import`

Keyword `import` digunakan untuk meng-_import_ atau memasukan _package_ lain ke dalam file program, agar isi dari package 
yang di-_import_ bisa dimanfaatkan. Package `fmt` merupakan salah satu _package_ bawaan yang disediakan oleh Go, isinya banyak 
fungsi untuk keperluan __I/O__ yang berhubungan dengan text. Berikut adalah skema penulisan keyword `import`:

```go
import "<nama-package>"
import "fmt"
```

## Penggunaan Fungsi `main()`

Dalam sebuah proyek harus ada file program yang di dalamnya berisi sebuah fungsi bernama `main()`. Fungsi tersebut harus 
berada di file yang package-nya bernama `main`. Fungsi `main()` adalah yang dipanggil pertama kali pada saat eksekusi program. 
Contoh penulisan fungsi `main`:

```go
func main() {

}
```

## Penggunaan Fungsi `fmt.Println()`

Fungsi `fmt.Println()` digunakan untuk memunculkan text ke layar (pada konteks ini, terminal atau CMD). Di program pertama 
yang telah kita buat, fungsi ini memunculkan tulisan __Hello world__. Skema penulisan keyword `fmt.Println()` bisa dilihat 
pada contoh berikut.

```go
fmt.Println("<isi-pesan>")
fmt.Println("Hello world")
```

Fungsi `fmt.Println()` berada dalam package `fmt`, maka untuk menggunakannya perlu package tersebut untuk di-import terlebih 
dahulu. Fungsi `fmt.Println()` dapat menampung parameter yang tidak terbatas jumlahnya. Semua data parameter akan dimunculkan 
dengan pemisah tanda spasi.

```go
fmt.Println("Hello", "world!", "how", "are", "you")
```

Contoh statement di atas akan menghasilkan output: __Hello world! how are you__.

## Komentar Inline

Penulisan komentar jenis ini di awali dengan tanda __double slash__ (`//`) lalu diikuti pesan komentarnya. Komentar inline 
hanya berlaku untuk satu baris pesan saja. Jika pesan komentar lebih dari satu baris, maka tanda `//` harus ditulis lagi di 
baris selanjutnya.

```go
// menampilkan pesan Hello world
fmt.Println("Hello world")
```

## Komentar

Komentar yang cukup panjang akan lebih rapi jika ditulis menggunakan teknik komentar multiline. Ciri dari komentar jenis 
ini adalah penulisannya diawali dengan tanda `/*` dan diakhiri `*/`.

```go
/*
    komentar kode
    menampilkan pesan hello world
*/
fmt.Println("hello world")
```

Sifat komentar ini sama seperti komentar inline, yaitu sama-sama diabaikan oleh compiler.