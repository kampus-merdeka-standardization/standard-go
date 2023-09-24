# Variabel

Go mengadopsi dua jenis penulisan variabel, yaitu yang dituliskan tipe data-nya, dan juga yang tidak. Kedua cara tersebut 
valid dan tujuannya sama, pembedanya hanya cara penulisannya saja.

## Deklarasi Variabel Beserta Tipe Data

Go memiliki aturan cukup ketat dalam hal penulisan variabel. Ketika deklarasi, tipe data yg digunakan harus dituliskan juga. 
Istilah lain dari konsep ini adalah __manifest typing__. Berikut adalah contoh cara pembuatan variabel yang tipe datanya 
harus ditulis.

```go
package main

import "fmt"

func main() {
    var firstName string = "john"

    var lastName string
    lastName = "wick"

    fmt.Printf("halo %s %s!\n", firstName, lastName)
}
```

Keyword `var` di atas digunakan untuk deklarasi variabel, contohnya bisa dilihat pada `firstName` dan `lastName`. Nilai variabel 
`firstName` diisi langsung ketika deklarasi, berbeda dibanding `lastName` yang nilainya diisi setelah baris kode deklarasi, 
hal seperti ini diperbolehkan di Go.

## Deklarasi Variabel Menggunakan Keyword `var`

Pada kode di atas bisa dilihat bagaimana sebuah variabel dideklarasikan dan diisi nilainya. Keyword `var` digunakan untuk 
membuat variabel baru.

Skema penggunaan keyword var:

```go
var <nama-variabel> <tipe-data>
var <nama-variabel> <tipe-data> = <nilai>
```

Contoh:

```go
var lastName string
var firstName string = "john"
```

Nilai variabel bisa di-isi langsung pada saat deklarasi variabel.

- Penggunaan Fungsi `fmt.Printf()`

Fungsi ini digunakan untuk menampilkan output dalam bentuk tertentu. Kegunaannya sama seperti fungsi `fmt.Println()`, hanya 
saja struktur outputnya didefinisikan di awal. Perhatikan bagian `"halo %s %s!\n"`, karakter `%s` di situ akan diganti dengan 
data `string` yang berada di parameter ke-2, ke-3, dan seterusnya. Contoh lain, ketiga baris kode berikut ini akan menghasilkan 
output yang sama, meskipun cara penulisannya berbeda.

```go
fmt.Printf("halo john wick!\n")
fmt.Printf("halo %s %s!\n", firstName, lastName)
fmt.Println("halo", firstName, lastName + "!")
```

Tanda plus (`+`) jika ditempatkan di antara string, fungsinya adalah untuk penggabungan string atau _string concatenation_.
Fungsi `fmt.Printf()` tidak menghasilkan baris baru di akhir text, oleh karena itu digunakanlah literal newline yaitu `\n`, 
untuk memunculkan baris baru di akhir. Hal ini sangat berbeda jika dibandingkan dengan fungsi `fmt.Println()` yang secara 
otomatis menghasilkan new line (baris baru) di akhir.

## Deklarasi Variabel Tanpa Tipe Data

Selain _manifest typing_, Go juga mengadopsi konsep __type inference__, yaitu metode deklarasi variabel yang tipe data-nya 
ditentukan oleh tipe data nilainya, cara kontradiktif jika dibandingkan dengan cara pertama. Dengan metode jenis ini, keyword 
`var` dan tipe data tidak perlu ditulis.

```go
var firstName string = "john"
lastName := "wick"

fmt.Printf("halo %s %s!\n", firstName, lastName)
```

Variabel `lastName` dideklarasikan dengan menggunakan metode type inference. Penandanya tipe data tidak dituliskan pada 
saat deklarasi. Pada penggunaan metode ini, operand `=` harus diganti dengan `:=` dan keyword `var` dihilangkan. Tipe data 
`lastName` secara otomatis akan ditentukan menyesuaikan value atau nilai-nya. Jika nilainya adalah berupa `string` maka 
tipe data variabel adalah `string`. Pada contoh di atas, nilainya adalah string `"wick"`.

Diperbolehkan untuk tetap menggunakan keyword `var` pada saat deklarasi meskipun tanpa menuliskan tipe data, dengan ketentuan 
tidak menggunakan tanda `:=`, melainkan tetap menggunakan `=`.

```go
// menggunakan var, tanpa tipe data, menggunakan perantara "="
var firstName = "john"

// tanpa var, tanpa tipe data, menggunakan perantara ":="
lastName := "wick"
```

Kedua deklarasi di atas maksudnya sama.

Tanda `:=` hanya digunakan sekali di awal pada saat deklarasi. Untuk assignment nilai selanjutnya harus menggunakan tanda 
`=`, contoh:

```go
lastName := "wick"
lastName = "ethan"
lastName = "bourne"
```

> Perlu diketahui, deklarasi menggunakan := hanya bisa dilakukan di dalam blok fungsi.

## Deklarasi Multi Variabel

Go mendukung metode deklarasi banyak variabel secara bersamaan, caranya dengan menuliskan variabel-variabel-nya dengan pembatas 
tanda koma (`,`). Untuk pengisian nilainya-pun diperbolehkan secara bersamaan.

```go
var first, second, third string
first, second, third = "satu", "dua", "tiga"
```

Pengisian nilai juga bisa dilakukan bersamaan pada saat deklarasi. Caranya dengan menuliskan nilai masing-masing variabel 
berurutan sesuai variabelnya dengan pembatas koma (`,`).

```go
var fourth, fifth, sixth string = "empat", "lima", "enam"
```

Kalau ingin lebih ringkas:

```go
seventh, eight, ninth := "tujuh", "delapan", "sembilan"
```

Dengan menggunakan teknik type inference, deklarasi multi variabel bisa dilakukan untuk variabel-variabel yang tipe data 
satu sama lainnya berbeda.

```go
one, isFriday, twoPointTwo, say := 1, true, 2.2, "hello"
```

## Variabel Underscore `_`

Go memiliki aturan unik yang jarang dimiliki bahasa lain, yaitu tidak boleh ada satupun variabel yang menganggur. Artinya, 
semua variabel yang dideklarasikan harus digunakan. Jika ada variabel yang tidak digunakan tapi dideklarasikan, error akan 
muncul pada saat kompilasi dan program tidak akan bisa di-run.

Underscore (`_`) adalah _reserved variable_ yang bisa dimanfaatkan untuk menampung nilai yang tidak dipakai. Bisa dibilang variabel 
ini merupakan keranjang sampah.

```go
_ = "belajar Golang"
_ = "Golang itu mudah"
name, _ := "john", "wick"
```

Pada contoh di atas, variabel `name` akan berisikan text `john`, sedang nilai `wick` ditampung oleh variabel underscore, 
menandakan bahwa nilai tersebut tidak akan digunakan.

Variabel underscore adalah _predefined_, jadi tidak perlu menggunakan `:=` untuk pengisian nilai, cukup dengan `=` saja. Namun 
khusus untuk pengisian nilai multi variabel yang dilakukan dengan metode type inference, boleh di dalamnya terdapat variabel 
underscore. Biasanya variabel underscore sering dimanfaatkan untuk menampung nilai balik fungsi yang tidak digunakan. Perlu 
diketahui, bahwa isi variabel underscore tidak dapat ditampilkan. Data yang sudah masuk variabel tersebut akan hilang. 

## Deklarasi Variabel Menggunakan Keyword `new`

Keyword `new` digunakan untuk membuat variabel pointer dengan tipe data tertentu. Nilai data default-nya akan menyesuaikan 
tipe datanya.

```go
name := new(string)

fmt.Println(name)   // 0x20818a220
fmt.Println(*name)  // ""
```

Variabel `name` menampung data bertipe __pointer string__. Jika ditampilkan yang muncul bukanlah nilainya melainkan alamat 
memori nilai tersebut (dalam bentuk notasi heksadesimal). Untuk menampilkan nilai aslinya, variabel tersebut perlu di-__dereference__ 
terlebih dahulu, menggunakan tanda asterisk (`*`).

## Deklarasi Variabel Menggunakan Keyword `make`

Keyword ini hanya bisa digunakan untuk pembuatan beberapa jenis variabel saja, yaitu:
- channel 
- slice 
- map

## Konstanta

Konstanta adalah jenis variabel yang nilainya tidak bisa diubah. Inisialisasi nilai hanya dilakukan sekali di awal, setelah 
itu variabel tidak bisa diubah nilainya.

### Penggunaan Konstanta

Cara penerapan konstanta sama seperti deklarasi variabel biasa, selebihnya tinggal ganti keyword `var` dengan `const`.

```go
const firstName string = "john"
fmt.Print("halo ", firstName, "!\n")
```

Teknik type inference bisa diterapkan pada konstanta, caranya yaitu cukup dengan menghilangkan tipe data pada saat deklarasi.

```go
const lastName = "wick"
fmt.Print("nice to meet you ", lastName, "!\n")
```

- Penggunaan Fungsi `fmt.Print()`

Fungsi ini memiliki peran yang sama seperti fungsi `fmt.Println()`, pembedanya fungsi `fmt.Print()` tidak menghasilkan baris 
baru di akhir outputnya. Perbedaan lainnya adalah, nilai pada parameter-parameter yang dimasukkan ke fungsi tersebut digabungkan 
tanpa pemisah. Tidak seperti pada fungsi `fmt.Println()` yang nilai paremeternya digabung menggunakan penghubung spasi.

```go
fmt.Println("john wick")
fmt.Println("john", "wick")

fmt.Print("john wick\n")
fmt.Print("john ", "wick\n")
fmt.Print("john", " ", "wick\n")
```

Kode di atas menunjukkan perbedaan antara `fmt.Println()` dan `fmt.Print()`. Output yang dihasilkan oleh 5 statement di atas 
adalah sama, meski cara yang digunakan berbeda.

Bila menggunakan `fmt.Println()` tidak perlu menambahkan spasi di tiap kata, karena fungsi tersebut akan secara otomatis 
menambahkannya di sela-sela nilai. Berbeda dengan `fmt.Print()`, perlu ditambahkan spasi, karena fungsi ini tidak menambahkan 
spasi di sela-sela nilai parameter yang digabungkan.

### Deklarasi Multi Konstanta

Berikut adalah contoh deklarasi konstanta dengan tipe data dan nilai yang berbeda.

```go
const (
square          = "kotak"
isToday bool    = true
numeric uint8   = 1
floatNum        = 2.2
)
```

- `square`, dideklarasikan dengan metode _type inference_ dengan tipe data __string__ dan nilainya __"kotak"__
- `isToday`, dideklarasikan dengan metode _manifest typing_ dengan tipe data __bool__ dan nilainya __true__ 
- `numeric`, dideklarasikan dengan metode _manifest typing_ dengan tipe data __uint8__ dan nilainya __1__ 
- `floatNum`, dideklarasikan dengan metode _type inference_ dengan tipe data __float__ dan nilainya __2.2__

Contoh deklarasi konstanta dengan tipe data dan nilai yang sama:

```go
const (
a = "konstanta"
b
)
```

> Ketika tipe data dan nilai tidak dituliskan dalam deklarasi konstanta, maka tipe data dan nilai yang dipergunakan adalah 
> sama seperti konstanta yang dideklarasikan diatasnya.

- `a` dideklarasikan dengan metode _type inference_ dengan tipe data __string__ dan nilainya __"konstanta"__
- `b` dideklarasikan dengan metode _type inference_ dengan tipe data __string__ dan nilainya __"konstanta"__

Berikut contoh gabungan dari keduanya:

```go
const (
today string = "senin"
sekarang
isToday2 = true
)
```

- `today` dideklarasikan dengan metode _manifest typing_ dengan tipe data __string__ dan nilainya __"senin"__
- `sekarang` dideklarasikan dengan metode _manifest typing_ dengan tipe data __string__ dan nilainya __"senin"__
- `isToday2` dideklarasikan dengan metode _type inference_ dengan tipe data __bool__ dan nilainya __true__

Berikut contoh deklrasi multiple konstanta dalam satu baris:

```go
const satu, dua = 1, 2
const three, four string = "tiga", "empat"
```

- `satu`, dideklarasikan dengan metode _type inference_ dengan tipe data __int__ dan nilainya __1__ 
- `dua`, dideklarasikan dengan metode _type inference_ dengan tipe data __int__ dan nilainya __2__ 
- `three`, dideklarasikan dengan metode _manifest typing_ dengan tipe data __string__ dan nilainya __"tiga"__
- `four`, dideklarasikan dengan metode _manifest typing_ dengan tipe data __string__ dan nilainya __"empat"__