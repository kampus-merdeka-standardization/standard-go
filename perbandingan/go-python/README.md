# Go vs Python

Bahasa Go bersifat prosedural, fungsional, dan concurrent, sedangkan Python adalah bahasa berorientasi objek, imperatif, 
fungsional, dan prosedural. Demikian pula, beberapa perbedaan lain membuat satu berbeda dari yang lain. Jadi, mari kita 
bahas dengan presentasi tabel tentang perbedaan antara keduanya:

| Parameter            | Golang                                             | Python                                                               |
|----------------------|----------------------------------------------------|----------------------------------------------------------------------|
| Tipe                 | Statis                                             | Dinamis                                                              |
| Kecepatan            | Cepat                                              | Relatif Lambat                                                       |
| Keterbacaan          | Lebih Mudah Dibaca                                 | Kurang Dapat Dibaca                                                  |
| Tujuan               | _Systems Programming_ dan konkurensi               | _General Purpose Programming_                                        |
| Ekspresi             | Lebih Ekspresif                                    | Kurang Ekspresif                                                     |
| Dukungan _Library_   | Baik                                               | Lebih Baik                                                           |
| Sintaks              | Mirip dengan bahasa C dengan tipe eksplisit        | Pengetikan Dinamis                                                   |
| Performa             | Lebih Cepat dan Efisien                            | Relatif Lebih Lambat dan Kurang Efisien                              |
| Konkurensi           | Dukungan Konkurensi Bawaan                         | Mendukung Konkurensi melalui _Library_                               |
| Kompilasi            | Dikompilasi ke Kode Mesin                          | Ditafsirkan atau Dikompilasi ke Bytecode                             |
| Manajemen Memori     | Manual                                             | Otomatis                                                             |
| _Error Handling_     | Eksplisit                                          | _Exception-based_                                                    |
| _Pacakge Management_ | Sistem Modul Bawaan (_Go Modules_)                 | _Package Manager (pip) and Virtual Environments (like virtualenv)_   |
| Pengembangan Web     | Ekosistem Bertumbuh                                | Ekosistem yang Luas                                                  |
| Dukungan Komunitas   | Lebih Kecil tapi Berkembang                        | Besar dan Aktif                                                      |
| Kurva Pembelajaran   | Kurva Pembelajaran yang Curam                      | Sederhana dan Mudah Dipahami                                         |
| Kasus Penggunaan     | _Backend Systems, Distributed Systems, Networking_ | _Web Development, Data Analysis, Scripting, Artificial Intelligence_ |
| _Framework_ Populer  | Gin, Echo, Gorilla                                 | Django, Flask, Pyramid                                               |

## Kepopuleran

Sekarang, mengingat Golang vs Python, keduanya populer di kalangan pengembang, menurut Survei Stack Overflow 2022, Python 
memegang posisi ke-4 sebagai bahasa pemrograman paling populer di kalangan pengembang dengan 48,07% suara, dan bahasa Go 
memegang posisi ke-13 dengan 11,15% suara di segmen preferensi dan popularitas. Python lebih populer daripada Golang. 
Namun, Golang berkembang pesat namun tertinggal dari Python.

## Performa

Dalam hal performa Go vs Python, Go dan Python menunjukkan hasil yang signifikan. Namun, kedua bahasa tersebut dapat diwujudkan 
berdasarkan beberapa faktor, seperti manajemen memori, fungsionalitas, dan kecepatan. Demikian pula, berdasarkan perbandingan 
Performance Benchmarks oleh [Benchmarks Game](https://benchmarksgame-team.pages.debian.net/benchmarksgame/fastest/go-python3.html), 
kami dapat menyimpulkan bahwa kinerja Golang hampir 40x lebih cepat daripada Python.

### Binary Search

Di bawah ini, kami membuat daftar `int` (mulai dari 1 hingga 1,00,0000) dan kemudian menggunakan pencarian biner untuk menemukan 
nomor yang sama. Hasil yang kami capai adalah:

| Bahasa | Kecepatan        |
|--------|------------------|
| Golang | 20.8 ns/op       |
| Python | 2442.13377 ns/op |

### Bubble Sort

Kami membuat daftar `int` acak, sepanjang 10.000 elemen, dan kemudian mengurutkannya menggunakan Bubble Sort.

| Bahasa | Kecepatan                 |
|--------|---------------------------|
| Golang | 90805247 ns/op (0.09s)    |
| Python | 6708160950.6 ns/op (6.7s) |

### Read from File

kami melakukan tes standar membaca file teks mentah 'lorem ipsum'.

| Bahasa | Kecepatan   |
|--------|-------------|
| Golang | 5305 ns/op  |
| Python | 58359 ns/op |

### HTTP Request Handling

Kami membuat server analog dengan Python dan Golang mengamati waktu yang diperlukan untuk merespons pesan sederhana 'Halo Dunia'.

| Bahasa | Kecepatan   |
|--------|-------------|
| Golang | 0.070 ms/RQ |
| Python | 1.261 ms/RQ |

Di sini, kita dapat melihat bahwa Golang lebih cepat daripada Python hampir secara keseluruhan; oleh karena itu, kita dapat 
menyimpulkan bahwa Kinerja Golang lebih baik daripada Python. Namun, kedua bahasa pemrograman tersebut sama-sama efektif 
dalam kancah pengembangannya.

## Skalabilitas

Bagi perusahaan pengembang Golang mana pun, dukungan dan gagasan proses _concurrent_ terbukti signifikan. Namun, jika berbicara 
tentang Python, bahasa tersebut memang menunjukkan beberapa masalah dalam hal konkurensi tetapi memberikan hasil yang fantastis dalam hal paralelisme. 
Python memberikan hasil yang konsisten ketika membagi tugas untuk menawarkan skalabilitas yang lebih baik untuk bahasa pemrograman.

## _Frameworks_

Python memiliki keunggulan paling besar dibandingkan Golang karena banyaknya koleksi _library_ dan _frameworks_, dengan Django 
dan Flask sebagai dua _framework_ web paling kuat yang memungkinkan pembuatan aplikasi web atau API dalam waktu singkat. 
Namun, Golang, di sisi lain, tidak memiliki _framework_ dominan yang signifikan seperti Django untuk Python atau Laravel untuk PHP. 
Selain itu, komunitas Golang agak menentang _framework_ tersebut.

## _Concurrency and Multithreading_

Konkurensi dan multithreading adalah teknik yang digunakan untuk meningkatkan kinerja dan skalabilitas dalam pemrograman. 
Di Go, konkurensi adalah fitur inti. Ia memiliki `goroutine` yang memungkinkan fungsi berjalan secara independen dan asinkron. 
Ini berarti fungsi dapat dijalankan secara terpisah tanpa menyebabkan penundaan. Python juga mendukung multithreading tetapi 
tidak terintegrasi atau seefisien `goroutine` Go.

Dengan Python, kita perlu mengimpor _library_ “threading” dan mengikuti beberapa langkah untuk membuat dan memulai thread 
untuk suatu fungsi:

```python
import threading

def myFunc():
    print("Hello World!")

t1 = threading.Thread(target=myFunc)
t1.start()
```

Di Go, kita dapat menjalankan fungsi apa pun secara bersamaan menggunakan kata kunci “go”. Berikut kode Go:

```go
func myFunc() {
    fmt.Println("Hello World!")
}

go myFunc()
```

Menggunakan “go” di Go memungkinkan kita menjalankan fungsi secara mandiri dengan mudah tanpa mengkhawatirkan manajemen thread. 
Hal ini membuat pemrograman bersamaan di Go lebih sederhana dibandingkan dengan Python.

## Aplikasi Web

Golang adalah bahasa yang paling cocok untuk _systems programming_. Karena memiliki konkurensi, tidak ada keraguan Anda akan 
dapat diterima dan digunakan dalam komputasi cluster dan komputasi awan. Selain itu Golang juga digunakan dalam pengembangan 
web karena kemudahan penggunaannya di perpustakaan. Dengan bantuan Golang, Anda dapat menyiapkan server web yang tepat dengan 
mudah, dan hanya membutuhkan waktu beberapa detik.

## Eksekusi Kode

Eksekusi kode adalah salah satu faktor utama yang mendasari popularitas tumpukan teknologi. Python adalah bahasa yang diketik 
secara dinamis dan menggunakan _interpreter_ atau VM, sedangkan Golang diketik secara statis dan menggunakan kompiler alih-alih 
_interpreter_ atau VM, sehingga memberikan performa waktu proses yang lebih baik.

## Libraries

Python adalah bahasa yang menonjol dalam kasus seperti ini karena banyaknya _library_. Dengan _packages_ fantastis seperti 
Numpy, dapat membantu menangani fungsi matriks dan penanganan array. Scikit dan Tensorflow membantu dalam _Deep Learning_, 
Pandas membantu dalam Analisis Data, dan _package_ lainnya dapat banyak membantu dalam fungsi penting lainnya. _Library_ 
Python adalah salah satu alasan utama mengapa pengembang cenderung memilihnya.

Namun, bukan berarti Golang bisa ketinggalan dalam kasus ini. Selama proses pengembangan Golang, Google memutuskan untuk 
menggunakan _libraries_ yang paling menakjubkan.Mengenai perbandingannya, Golang mungkin tidak bisa mendekati Python karena 
banyaknya _library_. Namun jika dibandingkan bidang penggunaan, kedua bahasa ini sebagian besar sama. Ada penanganan basis 
data yang luar biasa, pengembangan web, enkripsi, dan _library_ pemrograman _concurrent_.

## Referensi

- [Go vs Python For Web Development and ML](https://www.bacancytechnology.com/blog/go-vs-python)