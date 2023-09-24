# Go vs Node.js

Saat ini, Go adalah salah satu bahasa terpopuler yang banyak digunakan untuk pemrograman. Hal ini memungkinkan produktivitas 
terbaik dan penggunaan daya multi-core. Sebaliknya, Node hadir dengan lingkungan runtime lengkap yang dilengkapi dengan semua 
alat pengembangan yang diperlukan.

## Pro dan Kontra Golang

| Pro                                                  | Kontra                                                                                                                                                                        |
|------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Kode yang mudah dibaca dan dipelihara                | Memerlukan lebih banyak _coding_ untuk fitur sederhana karena kurangnya _complex abstractions_                                                                                |
| Sintaks yang rapi dan bersih                         | Penggunaan kembali kode lebih sulit karena Go tidak mendukung generics (saat ini Golang sudah _support generics)_                                                             |
| Didukung secara aktif oleh Google                    | Tidak ada _library_ GUI bawaan untuk membangun aplikasi GUI                                                                                                                   |
| Mencegah kesalahan variabel dengan pengetikan statis | Komunitasnya kurang _mature_ dibandingkan beberapa bahasa pemrograman populer lainnya                                                                                         |
| Peningkatan kinerja sebagai bahasa yang dikompilasi  | Mungkin mengonsumsi lebih banyak sumber daya komputasi untuk program yang kompleks, sehingga menghasilkan ukuran file yang lebih besar karena tidak adanya mesin virtual (VM) |
| Mendukung konkurensi untuk pemrosesan paralel        |                                                                                                                                                                               |

## Pro dan Kontra Node.js

| Pro                                                                                               | Kontra                                                                                                                                       |
|---------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| _Useful_ untuk membangun aplikasi web yang skalabel                                               | Proses debug mungkin sulit dilakukan karena pengetikan JavaScript yang dinamis dan potensi kesalahan kode terkait variabel                   |
| Terintegrasi dengan baik dengan database NoSQL MongoDB                                            | Pemrograman asinkron memerlukan keahlian tingkat tinggi untuk menguasai dan membuat aplikasi yang skalabel                                   |
| Mudah dipelajari karena penggunaan JavaScript                                                     | API dan _packages_ mungkin sering mengalami perubahan dan pembaruan, yang menyebabkan masalah kompatibilitas dan kebingungan bagi pengembang |
| Memberikan kinerja cepat dengan fitur Event loop bawaan                                           |                                                                                                                                              |
| Komunitas yang aktif dan berkembang dengan pembaruan dan rilis yang sering                        |                                                                                                                                              |
| Sangat cocok untuk membangun aplikasi streaming                                                   |                                                                                                                                              |
| Memungkinkan caching modul individual dengan mudah dan mendorong pengembangan aplikasi yang cepat |                                                                                                                                              |

## Kesederhanaan dan Kurva Pembelajaran

Tidak diragukan lagi, JavaScript adalah salah satu bahasa pemrograman yang paling banyak digunakan di seluruh dunia. Pada 
dasarnya, ini adalah bahasa pemrograman asinkron dan berisi _callback function_ juga. Dan jika seorang pengembang tidak terbiasa 
dengan JavaScript, menjadi ahli dalam pengembangan Node js sangatlah mudah. Faktanya, ada ribuan kursus Node js yang tersedia 
di Internet yang berisi proses pembelajaran terstruktur dan banyak di antaranya didukung oleh komunitas pengembang JavaScript 
yang besar. Hal ini membuat mempelajari Node js jauh lebih mudah dan sederhana dibandingkan bahasa Go.

Dalam bahasa Go, pengembang full-stack diharuskan mempelajari segala sesuatu tentang kerangka full-stack seperti proses 
spesifiknya, konsep, _rules_, pointer, _strict typing_, _interfaces_, coroutine, koneksi database, dan banyak hal lainnya.
Artinya, jika Anda menyewa pengembang aplikasi Golang untuk proyek aplikasi web Anda, Anda atau seseorang dari tim Anda juga 
pasti sudah familiar dengan Golang. Selain itu, Golang hanya untuk pengembangan backend, jadi Anda mungkin perlu _hire_ 
pengembang frontend secara terpisah.

## Skalabilitas

Bahasa Go diciptakan dengan mempertimbangkan skalabilitas. Faktanya, karena fungsi goroutine, yang dapat dieksekusi satu 
sama lain secara _concurrent_, bahasa Go sangat cocok untuk skalabilitas. Dalam istilah yang lebih sederhana, Goroutine 
pada dasarnya memungkinkan eksekusi thread yang andal dan mudah yang dapat dilakukan secara paralel dengan lancar.

Di sisi lain, pengembangan aplikasi web menggunakan Node JS bekerja sedikit berbeda. Sejujurnya, ini kurang elegan karena 
pemrograman _concurrent_ dalam JavaScript biasanya dilakukan menggunakan event callback, yang membuat konkurensi menjadi 
tidak efisien. Akibatnya, sistem menjadi berantakan dengan sangat cepat. Selain itu, Node Js bersifat single threaded, sehingga 
eksekusi instruksi dilakukan secara berurutan. Artinya, dukungan konkurensi di Node JS tidak secepat yang seharusnya.

## Benchmarks

Untuk menentukan _tool_ atau bahasa yang paling cocok untuk suatu _task_, akan sangat membantu jika membandingkan kinerja 
berbagai bahasa saat menjalankan berbagai algoritma dan _task_. Dalam contoh ini, kami akan membandingkan kinerja _task_ 
benchmark Node.js dan Go untuk metode dan algoritma bahasa komputer yang berbeda.

![benchmark](https://www.peerbits.com/static/0bd230ac77592b11a9e3c3b15e03199f/c5b3e/nodejs-vs-golang-image-04.png)
![benchmark](https://www.peerbits.com/static/f7d1c1ec07b0844dce1c4c2cb1512224/c5b3e/nodejs-vs-golang-image-05.png)

Berdasarkan data yang disajikan, terlihat bahwa Go memerlukan lebih sedikit waktu, memori, dan beban CPU untuk melakukan 
operasi dibandingkan dengan Node.js.

## Error Handling

_Error handling_ dalam bahasa Go memiliki pendekatan unik yang berbeda. Golang menuntut pengecekan kesalahan secara eksplisit 
dengan baris kode yang ditulis. Namun, sisi positifnya, hal ini juga menjamin konsistensi yang lebih baik dan hasil yang sempurna.

Di Node JS, _error handling_ terkadang tidak konsisten. Namun, ia menawarkan _error handling_ yang lebih baik dan lebih jelas 
dibandingkan Golang dengan teknik penanganan lempar-tangkap yang umum. Dan bagian terbaiknya adalah banyak pengembang web 
yang sudah familiar dengan teknik ini.

## _Availability of Developers_

Go relatif merupakan bahasa baru dan berkembang. Selain itu, Go juga disebut-sebut sebagai salah satu framework aplikasi 
tersulit. Namun, Go memiliki cakupan yang lebih cerah di masa depan karena pertumbuhannya yang pesat.

Karena NodeJS adalah bahasa pemrograman yang banyak digunakan, lebih mudah untuk menemukan pengembang yang memiliki keahlian 
Node.js. Oleh karena itu, membangun tim profesional untuk berbagai tugas pengembangan menjadi mudah.

## _Development Tools_

Node.Js menawarkan banyak _tools_, yang merupakan alasan utama untuk memilihnya. Bersamaan dengan ini, ini adalah _frameworks_ 
berbasis peristiwa yang berisi _microservice architecture_. Selain itu, Node Package Manager atau NPM adalah _standard library_ 
yang berisi sekitar 800.000 blok penyusun yang dapat diinstal dengan mudah dan pengoperasiannya tidak merepotkan.

Sebaliknya, Golang berisi _tools_ yang lebih sedikit dibandingkan dengan Node.Js. Sebenarnya, Go memiliki _library_ lengkap 
terstandarisasi dengan fitur-fitur yang dapat dioperasikan dengan mudah tanpa dukungan pihak ketiga.

## _Raw Performance_

Go lebih unggul dalam hal _raw performance_. Go dapat bekerja tanpa _interpreter_ dan dikompilasi langsung ke dalam kode 
mesin. Ini memberi Go tingkat kinerja yang sama dengan _low-level languages_.

Baik Go maupun Node.js memiliki fitur _garbage collector_, yang mencegah _memory leak_ dan memastikan stabilitas _memory footprint_. 
Dengan cara ini, Node.js sangat membantu dalam manajemen memori karena berfungsi sebagai _garbage collector_ yang efisien.

## _Real-life Performance_

Node.js sedikit tertinggal dari Go dalam performa di kehidupan nyata. Mesin Javascript V8 memastikan bahwa aplikasi akan 
memberikan kinerja real-time tanpa _interpreter_ apa pun. Namun, jika interaksi server database atau aplikasi jaringan terlibat,
kinerja Golang Vs Node.Js seringkali sama.

## Ekosistem

Node.js memiliki sejarah panjang dan komunitas yang mapan, yang berarti terdapat banyak _tools_, _library_, dan tutorial 
yang tersedia untuk pengembangan Node.js. Golang, meskipun lebih baru dan kurang populer, memiliki keuntungan dalam mendukung 
lingkungan runtime lintas platform, sehingga lebih mudah untuk mengembangkan aplikasi lintas platform.

Selain itu, Golang telah mendapatkan popularitas dalam beberapa tahun terakhir dan memiliki komunitas pengembang yang terus 
berkembang. Baik Node.js maupun Golang memiliki kekuatan dan keunggulannya masing-masing, dan pilihan di antara keduanya 
akan bergantung pada kebutuhan spesifik proyek Anda.

Meskipun Golang pasti memiliki _package_ dan _library_ yang bagus untuk digunakan, namun sejujurnya Golang akan membutuhkan 
waktu untuk mengejar Node JS. Di sisi lain, menemukan perusahaan pengembang Node JS lebih mudah ditemukan dibandingkan dengan 
pengembang Go.

## Komunitas

Seperti disebutkan di awal, baik Golang dan Node JS adalah _open-source_ dan mereka memiliki komunitas sendiri yang sepenuhnya 
terlibat dalam penyempurnaan bahasa pemrograman ini. Terkait Node JS, komunitasnya besar dan dinamis. Komunitas Golang, 
sebaliknya, masih muda dan lebih kecil. Namun pertumbuhannya semakin meningkat setiap tahunnya. Menurut [Survei Golang](https://go.dev/blog/survey2020-results), 
76% responden menggunakan Go di tempat kerja dan 66% mengatakan Go sangat penting bagi kesuksesan perusahaan mereka.

## Kesimpulan

Tampaknya Node JS dan Golang sedang berkembang. Namun, menurut [statista](https://www.statista.com/statistics/793628/worldwide-developer-survey-most-used-languages/),
JavaScript dan HTML/CSS adalah bahasa pemrograman yang paling umum digunakan di kalangan pengembang perangkat lunak. Namun, 
Golang berada di peringkat 5 besar bahasa pemrograman yang paling disukai, meninggalkan JavaScript. Semua ini dengan jelas 
menyimpulkan bahwa tidak ada bahasa yang sempurna dalam pengembangan web. Itu semua tergantung pada jenis aplikasi web yang 
ingin Anda bangun.

## Referensi

- [peerbits - Nodejs vs Go](https://www.peerbits.com/blog/nodejs-vs-golang.html#:~:text=In%20summary%2C%20Node.,that%20require%20efficient%20memory%20management.)