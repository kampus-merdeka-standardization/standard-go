# Routing

Library routing adalah kumpulan alat atau modul yang dirancang khusus untuk mengelola routing dan penanganan permintaan dalam
aplikasi web atau jaringan. Library routing membantu pengembang mengatur bagaimana permintaan dari pengguna atau klien akan
dipetakan ke fungsi-fungsi pengendali yang sesuai berdasarkan pola-pola rute yang telah ditentukan. Dengan memanfaatkan library
routing, pengembang dapat dengan efisien menangani permintaan HTTP, mengelola parameter URL, dan menerapkan logika bisnis
dalam aplikasi web.

Berikut adalah library routing di Golang:

## [Fast HTTP](https://github.com/valyala/fasthttp)

FastHTTP adalah library yang dikhususkan untuk bahasa pemrograman Go (Golang) yang menonjol karena kinerja tinggi dan efisiensi 
dalam penanganan permintaan HTTP. Dirancang untuk menghemat penggunaan memori dan CPU, FastHTTP sangat cocok untuk aplikasi 
web dengan beban kerja tinggi yang membutuhkan waktu respons cepat, meskipun dengan routing yang lebih sederhana dibandingkan 
dengan net/http bawaan Go.

## [Chi](https://github.com/go-chi/chi)

Chi adalah library routing dan middleware yang sangat ringan dan fleksibel untuk bahasa pemrograman Go (Golang). Chi memungkinkan 
pengembang untuk dengan mudah membuat routing yang kuat dan kompleks serta menggabungkan middleware dengan cara yang modular. 
Dengan pendekatan yang minimalis dan fokus pada kecepatan eksekusi, Chi sangat cocok untuk pengembangan aplikasi web yang 
memerlukan kontrol tinggi atas proses routing dan penanganan middleware.

## [Heimdall](https://github.com/gojek/heimdall)

Heimdall adalah klien HTTP yang membantu aplikasi Anda dalam menangani sejumlah besar permintaan dengan skala yang besar. 
Dengan menggunakan Heimdall, Anda dapat mengontrol permintaan yang gagal menggunakan mekanisme yang mirip dengan circuit 
breaker ala Hystrix. Selain itu, Anda dapat menambahkan pengulangan sinkron dalam memori untuk setiap permintaan, dan bahkan 
memiliki opsi untuk menentukan strategi pengulangan kustom sesuai kebutuhan Anda. Heimdall juga memungkinkan Anda untuk membuat 
klien dengan timeout yang berbeda untuk setiap permintaan. Semua metode HTTP diekspos dalam antarmuka yang mudah digunakan, 
memudahkan penggunaannya dalam pengembangan aplikasi Anda.

## Perbandingan

| Komponen        | Fast HTTP | Chi | Heimdall |
|-----------------|-----------|-----|----------|
| Maintenance     | 4         | 3   | 1        |
| Reputable       | 4         | 2   | 4        |
| Compatibility   | 4         | 4   | 3        |
| Community       | 4         | 4   | 2        |
| Documentation   | 3         | 4   | 3        |
| Licensing       | 4         | 4   | 4        |
| Extensible      | 4         | 4   | 4        |
| Size            | 4         | 4   | 4        |
| **Total Score** | 31        | 29  | 25       |