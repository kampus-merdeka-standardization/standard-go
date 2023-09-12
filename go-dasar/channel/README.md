# Channel

**Channel** digunakan untuk menghubungkan goroutine satu dengan goroutine lain. Mekanisme yang dilakukan adalah serah-terima 
data lewat channel tersebut. Dalam komunikasinya, sebuah channel difungsikan sebagai pengirim di sebuah goroutine, dan juga 
sebagai penerima di goroutine lainnya. Pengiriman dan penerimaan data pada channel bersifat **blocking** atau **synchronous**.

## Penerapan Channel

Channel merupakan sebuah variabel, dibuat dengan menggunakan kombinasi keyword `make` dan `chan`. Variabel channel memiliki 
satu tugas, menjadi pengirim, atau penerima data. Program berikut adalah contoh implementasi channel. 3 buah goroutine dieksekusi, 
di masing-masing goroutine terdapat proses pengiriman data lewat channel. Data tersebut akan diterima 3 kali di goroutine utama `main`.

```go
package main

import "fmt"
import "runtime"

func main() {
    runtime.GOMAXPROCS(2)

    var messages = make(chan string)

    var sayHelloTo = func(who string) {
        var data = fmt.Sprintf("hello %s", who)
        messages <- data
    }

    go sayHelloTo("john wick")
    go sayHelloTo("ethan hunt")
    go sayHelloTo("jason bourne")

    var message1 = <-messages
    fmt.Println(message1)

    var message2 = <-messages
    fmt.Println(message2)

    var message3 = <-messages
    fmt.Println(message3)
}
```

Pada kode di atas, variabel `messages` dideklarasikan bertipe channel `string`. Cara pembuatan channel yaitu dengan menuliskan 
keyword `make` dengan isi keyword `chan` diikuti dengan tipe data channel yang diinginkan.

```go
var messages = make(chan string)
```

Selain itu disiapkan juga closure `sayHelloTo` yang tugasnya membuat sebuah pesan string yang kemudian dikirim via channel. 
Pesan string tersebut dikirim lewat channel `messages`. Tanda `<-` jika dituliskan di sebelah kiri nama variabel, berarti 
sedang berlangsung proses pengiriman data dari variabel yang berada di kanan lewat channel yang berada di kiri (pada konteks 
ini, variabel `data` dikirim lewat channel `messages`).

```go
var sayHelloTo = func(who string) {
    var data = fmt.Sprintf("hello %s", who)
    messages <- data
}
```

Fungsi `sayHelloTo` dieksekusi tiga kali sebagai goroutine berbeda. Menjadikan tiga proses ini berjalan secara **asynchronous** 
atau tidak saling tunggu.

> Sekali lagi perlu diingat bahwa eksekusi goroutine adalah _asynchronous_, sedangkan serah-terima data antar channel adalah 
> _synchronous_.

```go
go sayHelloTo("john wick")
go sayHelloTo("ethan hunt")
go sayHelloTo("jason bourne")
```

Dari ketiga fungsi tersebut, goroutine yang selesai paling awal akan mengirim data lebih dulu, datanya kemudian diterima 
variabel `message1`. Tanda `<-` jika dituliskan di sebelah kiri channel, menandakan proses penerimaan data dari channel 
yang di kanan, untuk disimpan ke variabel yang di kiri.

```go
var message1 = <-messages
fmt.Println(message1)
```

Penerimaan channel bersifat blocking. Artinya statement `var message1 = <-messages` hingga setelahnya tidak akan dieksekusi 
sebelum ada data yang dikirim lewat channel. Ke semua data yang dikirim dari tiga goroutine berbeda tersebut datanya akan 
diterima secara berurutan oleh `message1`, `message2`, `message3`; untuk kemudian ditampilkan.

## Channel Sebagai Tipe Data Parameter

Variabel channel bisa di-pass ke fungsi lain sebagai parameter. Cukup tambahkan keyword `chan` pada deklarasi parameter agar 
operasi pass channel variabel bisa dilakukan. Siapkan fungsi `printMessage` dengan parameter adalah channel. Lalu ambil 
data yang dikirimkan lewat channel tersebut untuk ditampilkan.

```go
func printMessage(what chan string) {
    fmt.Println(<-what)
}
```

Setelah itu ubah implementasi di fungsi `main`.

```go
func main() {
    runtime.GOMAXPROCS(2)

    var messages = make(chan string)

    for _, each := range []string{"wick", "hunt", "bourne"} {
        go func(who string) {
            var data = fmt.Sprintf("hello %s", who)
            messages <- data
        }(each)
    }

    for i := 0; i < 3; i++ {
        printMessage(messages)
    }
}
```

Output program di atas sama dengan program sebelumnya. Parameter `what` fungsi `printMessage` bertipe channel `string`, bisa 
dilihat dari kode `chan string` pada cara deklarasinya. Operasi serah-terima data akan bisa dilakukan pada variabel tersebut, 
dan akan berdampak juga pada variabel `messages` di fungsi `main`. Passing data bertipe channel lewat parameter sifatnya 
**pass by reference**, yang di transferkan adalah pointer datanya, bukan nilai datanya.

# Buffered Channel

Proses transfer data pada channel secara default dilakukan dengan cara **un-buffered**, atau tidak di-buffer di memori. Ketika 
terjadi proses kirim data via channel dari sebuah goroutine, maka harus ada goroutine lain yang menerima data dari channel 
yang sama, dengan proses serah-terima yang bersifat blocking. Maksudnya, baris kode setelah kode pengiriman dan penerimaan 
data tidak akan di proses sebelum proses serah-terima itu sendiri selesai.

Buffered channel sedikit berbeda. Pada channel jenis ini, ditentukan angka jumlah buffer-nya. Angka tersebut menjadi penentu 
jumlah data yang bisa dikirimkan bersamaan. Selama jumlah data yang dikirim tidak melebihi jumlah buffer, maka pengiriman 
akan berjalan **asynchronous** (tidak blocking).

Ketika jumlah data yang dikirim sudah melewati batas buffer, maka pengiriman data hanya bisa dilakukan ketika salah satu 
data yang sudah terkirim adalah sudah diambil dari channel di goroutine penerima, sehingga ada slot channel yang kosong. 
Proses pengiriman data pada buffered channel adalah _asynchronous_ ketika jumlah data yang dikirim tidak melebihi batas buffer. 
Namun pada bagian channel penerimaan data selalu bersifat _synchronous_.

## Penerapan Buffered Channel

Penerapan buffered channel pada dasarnya mirip seperti channel biasa. Perbedaannya hanya pada penulisan deklarasinya, perlu ditambahkan angka buffer sebagai argumen `make()`. 
Berikut adalah contoh penerapan buffered channel. Program di bawah ini merupakan pembuktian bahwa pengiriman data lewat 
buffered channel adalah asynchronous selama jumlah data yang sedang di-buffer oleh channel tidak melebihi kapasitas buffer.

```go
package main

import "fmt"
import "runtime"

func main() {
    runtime.GOMAXPROCS(2)

    messages := make(chan int, 3)

    go func() {
        for {
            i := <-messages
            fmt.Println("receive data", i)
        }
    }()

    for i := 0; i < 5; i++ {
        fmt.Println("send data", i)
        messages <- i
    }
}
```

Parameter kedua fungsi `make()` adalah representasi jumlah buffer. Perlu diperhatikan bahwa nilai buffered channel dimulai 
dari `0`. Ketika nilainya adalah **3** berarti jumlah buffer maksimal ada **4**. Terdapat IIFE goroutine yang isinya proses
penerimaan data dari channel `messages`, untuk kemudian datanya ditampilkan. Setelah goroutine tersebut dieksekusi, perulangan 
dijalankan dengan di-masing-masing perulangan dilakukan pengiriman data. Total ada 5 data dikirim lewat channel `messages` 
secara sekuensial.

Pengiriman data indeks ke 0, 1, 2 dan 3 akan berjalan secara asynchronous, hal ini karena channel ditentukan nilai buffer-nya 
sebanyak 3 (ingat, jika nilai buffer adalah 3, maka 4 data yang akan di-buffer). Pengiriman selanjutnya (indeks 5) hanya 
akan terjadi jika ada salah satu data dari ke-empat data yang sebelumnya telah dikirimkan sudah diterima (dengan serah terima 
data yang bersifat blocking). Setelahnya, pengiriman data kembali dilakukan secara asynchronous (karena sudah ada slot buffer 
ada yang kosong).

# Channel - Select

Select ini mempermudah kontrol komunikasi data lewat satu ataupun banyak channel. Cara penggunaan `select` untuk kontrol 
channel sama seperti penggunaan `switch` untuk seleksi kondisi.

## Penerapan Keyword `select`

Program berikut merupakan contoh sederhana penerapan select dalam channel. Dipersiapkan 2 buah goroutine, satu untuk pencarian 
rata-rata, dan satu untuk nilai tertinggi. Hasil operasi di masing-masing goroutine dikirimkan ke fungsi `main()` via channel 
(ada dua channel). Di fungsi `main()` sendiri, data tersebut diterima dengan memanfaatkan keyword `select`.

Pertama, siapkan 2 fungsi yang sudah dibahas di atas. Fungsi pertama digunakan untuk mencari rata-rata, dan fungsi kedua 
untuk penentuan nilai tertinggi dari sebuah slice.

```go
package main

import "fmt"
import "runtime"

func getAverage(numbers []int, ch chan float64) {
    var sum = 0
    for _, e := range numbers {
        sum += e
    }
    ch <- float64(sum) / float64(len(numbers))
}

func getMax(numbers []int, ch chan int) {
    var max = numbers[0]
    for _, e := range numbers {
        if max < e {
            max = e
        }
    }
    ch <- max
}
```

Kedua fungsi tersebut dijalankan sebagai goroutine. Di akhir blok masing-masing fungsi, hasil kalkulasi dikirimkan via channel 
yang sudah dipersiapkan, yaitu `ch1` untuk menampung data rata-rata, `ch2` untuk data nilai tertinggi. Buat implementasinya 
pada fungsi `main()`.

```go
func main() {
    runtime.GOMAXPROCS(2)

    var numbers = []int{3, 4, 3, 5, 6, 3, 2, 2, 6, 3, 4, 6, 3}
    fmt.Println("numbers :", numbers)

    var ch1 = make(chan float64)
    go getAverage(numbers, ch1)

    var ch2 = make(chan int)
    go getMax(numbers, ch2)

    for i := 0; i < 2; i++ {
        select {
        case avg := <-ch1:
            fmt.Printf("Avg \t: %.2f \n", avg)
        case max := <-ch2:
            fmt.Printf("Max \t: %d \n", max)
        }
    }
}
```

Pada kode di atas, pengiriman data pada channel `ch1` dan `ch2` dikontrol menggunakan `select`. Terdapat 2 buah `case` kondisi 
penerimaan data dari kedua channel tersebut. 
- Kondisi `case avg := <-ch1` akan terpenuhi ketika ada penerimaan data dari channel `ch1`, yang kemudian akan ditampung oleh variabel `avg`. 
- Kondisi `case max := <-ch2` akan terpenuhi ketika ada penerimaan data dari channel `ch2`, yang kemudian akan ditampung oleh variabel `max`. 

Karena ada 2 buah channel, maka perlu disiapkan perulangan 2 kali sebelum penggunaan keyword `select`.

# Channel - Range dan Close

Proses _retrieving_ data dari banyak channel bisa lebih mudah dilakukan dengan memanfaatkan kombinasi keyword `for` - `range`.

`for` - `range` jika diterapkan pada channel berfungsi untuk handle penerimaan data. Setiap kali ada pengiriman data via channel, 
maka akan men-trigger perulangan `for` - `range`. Perulangan akan berlangsung terus-menerus seiring pengiriman data ke channel 
yang dipergunakan. Dan perulangan hanya akan berhenti jika channel yang digunakan tersebut di **close** atau di non-aktifkan. 
Fungsi `close` digunakan utuk me-non-aktifkan channel.

Channel yang sudah di-close tidak bisa digunakan lagi baik untuk menerima data ataupun untuk mengirim data, itulah mengapa 
perulangan `for` - `range` juga berhenti.

## Penerapan `for` - `range` - `close` Pada Channel

Pertama siapkan fungsi `sendMessage()` yang tugasnya mengirim data via channel. Di dalam fungsi ini dijalankan perulangan 
sebanyak 20 kali, ditiap perulangannya data dikirim ke channel. Channel di-close setelah semua data selesai dikirim.

```go
func sendMessage(ch chan<- string) {
    for i := 0; i < 20; i++ {
        ch <- fmt.Sprintf("data %d", i)
    }
    close(ch)
}
```

Buat channel baru dalam fungsi `main()`, jalankan `sendMessage()` sebagai goroutine (dengan ini 20 data yang berada dalam 
fungsi tersebut dikirimkan via goroutine baru). Tak lupa jalankan juga fungsi `printMessage()`.

```go
func main() {
    runtime.GOMAXPROCS(2)

    var messages = make(chan string)
    go sendMessage(messages)
    printMessage(messages)
}
```

Setelah 20 data sukses dikirim dan diterima, channel `ch` di-non-aktifkan (`close(ch)`). Membuat perulangan data channel dalam 
`printMessage()` juga akan berhenti.

### Channel Direction

Ada yang unik dengan fitur parameter channel yang disediakan oleh Go. Level akses channel bisa ditentukan, apakah hanya 
sebagai penerima, pengirim, atau penerima sekaligus pengirim. Konsep ini disebut dengan **channel direction**.

Cara pemberian level akses adalah dengan menambahkan tanda `<-` sebelum atau setelah keyword `chan`. Untuk lebih jelasnya bisa 
dilihat di list berikut.

| Sintaks          | Penjelasan                                                   |
|------------------|--------------------------------------------------------------|
| ch chan string   | Parameter ch bisa digunakan untuk mengirim dan menerima data |
| ch chan<- string | Parameter ch hanya bisa digunakan untuk mengirim data        |
| ch <-chan string | Parameter ch hanya bisa digunakan untuk menerima data        |

Pada kode di atas bisa dilihat bahwa secara default channel akan memiliki kemampuan untuk mengirim dan menerima data. Untuk 
mengubah channel tersebut agar hanya bisa mengirim atau menerima saja, dengan memanfaatkan simbol `<-`.

Sebagai contoh fungsi `sendMessage(ch chan<- string)` yang parameter `ch` dideklarasikan dengan level akses untuk pengiriman 
data saja. Channel tersebut hanya bisa digunakan untuk mengirim, contohnya: `ch <- fmt.Sprintf("data %d", i)`. Dan sebaliknya 
pada fungsi `printMessage(ch <-chan string)`, channel `ch` hanya bisa digunakan untuk menerima data saja.

# Channel - Timeout

Teknik channel timeout digunakan untuk mengontrol penerimaan data dari channel mengacu ke kapan waktu diterimanya data, dengan 
durasi timeout bisa kita tentukan sendiri. Ketika tidak ada aktivitas penerimaan data dalam durasi yang sudah ditentukan, 
maka blok timeout dieksekusi.

## Penerapan Channel Timeout

Berikut adalah program sederhana contoh pengaplikasian timeout pada channel. Sebuah goroutine baru dijalankan dengan tugas 
mengirimkan data setiap interval tertentu, dengan durasi interval-nya sendiri adalah acak/random.

```go
package main

import "fmt"
import "math/rand"
import "runtime"
import "time"

func sendData(ch chan<- int) {
    randomizer := rand.New(rand.NewSource(time.Now().Unix()))

    for i := 0; true; i++ {
        ch <- i
        time.Sleep(time.Duration(randomizer.Int()%10+1) * time.Second)
    }
}
```

Selanjutnya, disiapkan perulangan tanpa henti, yang di setiap perulangan ada seleksi kondisi channel menggunakan `select`.

```go
func retreiveData(ch <-chan int) {
    loop:
    for {
        select {
        case data := <-ch:
            fmt.Print(`receive data "`, data, `"`, "\n")
        case <-time.After(time.Second * 5):
            fmt.Println("timeout. no activities under 5 seconds")
            break loop
        }
    }
}
```

Ada 2 blok kondisi pada `select` tersebut.

- Kondisi `case data := <-messages:`, akan terpenuhi ketika ada serah terima data pada channel `messages`. 
- Kondisi `case <-time.After(time.Second * 5):`, akan terpenuhi ketika tidak ada aktivitas penerimaan data dari channel dalam durasi 5 detik. Blok inilah yang kita sebut sebagai blok timeout.

Terakhir, kedua fungsi tersebut dipanggil di `main()`.

```go
func main() {
    runtime.GOMAXPROCS(2)

    var messages = make(chan int)

    go sendData(messages)
    retreiveData(messages)
}
```

Muncul output setiap kali ada penerimaan data dengan delay waktu acak. Ketika tidak ada aktivitas penerimaan dari channel 
dalam durasi 5 detik, perulangan pengecekkan channel diberhentikan.