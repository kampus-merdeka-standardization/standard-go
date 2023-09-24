# Project Layout Structure

## Ringkasan

Berikut ini merupakan tata letak dasar untuk proyek aplikasi Go. ini `bukan standar resmi yang ditetapkan oleh tim pengembang inti Go`;
namun, ini merupakan sejumlah pola tata letak proyek historis dan terkini yang umumnya digunakan dalam ekosistem Go.
Beberapa pola ini lebih populer daripada yang lain.

## Pembagian Direktori

Ada cukup banyak folder dan subfolder dalam project layout, berikut ringkasan beberapa file dan direktori yang umumnya dipakai.

```bash
.
├── go.mod
|   # file go.mod dipergunakan oleh go module (jika go mod diaktifkan).
|
├── Makefile
|   # file Makefile dipergunakan oleh command `make`.
|
├── assets/
|   # folder assets berisi static assets, seperti gambar, logo, dll.
|
├── build/
|   # folder build isinya adalah files untuk keperluan build dan
|   # juga CI (continous integration). Contoh file yang dimaksud adalah
|   # seperti Dockerfile, file CI tool (.travis-ci.yml, .gitlab-ci.yml)
|   # dan file untuk keperluan build ke bentuk lain seperti file deb, rpm, pkg.
|   |
│   ├── ci/
|   |   # tempatkan file untuk CI dalam folder ini
|   |
│   └── package/
|       # tempatkan file untuk keperluan build dalam folder ini
|
├── cmd/
|   # folder cmd isinya adalah source code utama aplikasi.
|   #
|   # jika aplikasi merupakan sebuah app monolith, maka folder ini isinya
|   # adalah langsung source code utama.
|   # salah satu contoh, folder ini isinya adalah file-file bisnis logic utama,
|   # seperti services dan repositories.
|   #
|   # jika arsitektur microservices diadopsi, dengan layout monorepo,
|   # maka isi dari cmd adalah source code yang dibagi per service.
|   |
│   ├── your_app_1/
│   ├── your_app_2/
│   ├── your_app_3/
│   └── ...
|
├── configs/
|   # folder configs isinya adalah file konfigurasi.
|
├── deployments/
|   # folder deployments isinya adalah file yang berhubungan dengan orchestration,
|   # deployments, dan juga CD. Seperti docker-compose.yml, k8s file, dll.
|
├── docs/
|   # folder docs isinya adalah file design dan dokumentasi.
|
├── examples/
|   # folder examples isinya adalah file example.
|
├── init/
|   # folder init isinya adalah file-file system init (systemd, upstart, sysv)
|   # dan file konfigurasi process manager atau supervisor (runit, supervisord).
|
├── internal/
|   # folder internal isinya adalah file private aplikasi dan library.
|   # sebetulnya folder ini kegunaannya sama seperti `pkg`, perbedaannya adalah package
|   # dalam folder internal ini hanya bisa di-import dalam project ini, tidak bisa di-import
|   # ke project lain.
|
├── pkg/
|   # folder pkg isinya adalah file utility yg di-reuse dalam project yang sama,
|   # atau bisa juga di re-use oleh project lain.
|   |
│   ├── your_public_lib_1/
│   ├── your_public_lib_2/
│   ├── your_public_lib_3/
│   └── ...
|
├── test/
|   # folder test isinya adalah file testing. untuk struktur file-nya sendiri bebas,
|   # mau disusun seperti apa.
|   #
|   # khusus untuk unit test, baiknya tidak ditempatkan di sini,
|   # tapi ditempatkan di dalam package yang sama dengan file yang akan di-unit-test. 
|
├── vendor/
|   # berisi clone dari 3rd party dependencies. Folder ini digunakan jika konfigurasi vendor diaktifkan
|
├── web/
|   # berisi aplikasi web. untuk microservices saya sarankan untuk menempatkan aplikasi web dalam folder `cmd/app`
|
└── ...
```

## Direktori Go

### `/cmd`

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

### `/internal`

Kode aplikasi dan library privat. Ini adalah kode anda yang tidak ingin diimpor oleh aplikasi atau library lain.
Perlu dicatat bahwa pola tata letak ini dipaksakan atau dijaga oleh kompiler Go itu sendiri. Pehatikan bahwa anda tidak
dibatasi pada direktori top level `internal` saja. Anda dapat memiliki banyak lebih dari satu direktori `internal` di setiap
tingkatan proyek ada.

Secara opsional anda dapat menambahkan struktur tambahan ke paket internal anda, untuk memisahkan kode internal yang
bersifat shared dan non-shared. Hal ini tidak diwajibkan (terutama untuk proyek-proyek kecil), tetapi bagus untuk memiliki
petunjuk visual yang menunjukkan penggunaan paket yang dimaksudkan.

Sebenernya kode aplikasi dapat ditempatkan di direktori `/internal/app` (misalnya, `/internal/app/myapp`) dan kode yang
dibagikan oleh aplikasi tersebut dapat ditempatkan di direktori `/internal/pkg` (mislanya, `/internal/pkg/myprivlib`).

### `/pkg`

Kode library yang boleh digunakan oleh aplikasi eksternal (misalnya, `/pkg/mypubliclib`). Proyek lain akan mengimpor library 
ini dengan harapan dapat berfungsi, jadi berpikirlah dua kali sebelum anda meletakkan sesuatu di sini :-) Perlu dicatat 
bahwa direktori `internal` adalah cara yang lebih baik untuk memastikan paket pribadi anda tidak dapat diimpor karena dijaga 
oleh Go. Namun, direktori `/pkg` tetap cara yang baik untuk mengkomunikasikan secara eksplisit  bahwa kode di dalam direktori 
tersebut aman digunakan oleh orang lain. Postingan [`I'll take pkg over internal`](https://travisjeffery.com/b/2019/11/i-ll-take-pkg-over-internal/) 
oleh Travis Jeffery memberikan gambaran yang baik tentang direktori `pkg` dan `internal` serta kapan waktu yang tepat untuk 
menggunakannya.

Hal ini merupakan cara untuk mengelompokkan kode Go di satu tempat ketika direktori root anda berisi banyak komponen dan 
direktori non-Go, sehingga memudahkan dalam menjalankan berbagai tools Go (seperti yang disebutkan dalam presentasi-presentasi 
ini: [`Best Practices for Industrial Programming`](https://www.youtube.com/watch?v=PTE4VJIdHPg) dari GopherCon EU 2018, 
[GopherCon 2018: Kat Zien - How Do You Structure Your Go Apps](https://www.youtube.com/watch?v=oL6JBUk6tj0), dan 
[GoLab 2018 - Massimiliano Pippi - Project layout patterns in Go](https://www.youtube.com/watch?v=3gQa1LWwuzk)).

Tidak masalah jika anda tidak menggunakannya, apabila proyek aplikasi anda benar-benar kecil dan tingkatan level tambahan 
tidak begitu penting (kecuali jika anda benar-benar menginginkannya. Pikirkanlah hal tersebut ketika proyek anda cukup besar 
dan direktori root anda sudah cukup sibuk (terutama jika anda memiliki banyak komponen aplikasi non-Go).

Asal-usul direktori `pkg`: Source code Go yang lama menggunakan `pkg` untuk paket-paketnya, dan kemudian berbagai proyek 
Go dalam komunitas mulai meniru pola tersebut (Lihat [`tweet Brad Fitzpatrick ini`](https://twitter.com/bradfitz/status/1039512487538970624) 
untuk konteks lebih lanjut).

Untuk contoh-contoh lebih lanjut bisa lihat berikut:

- https://github.com/kubernetes/kubernetes/tree/master/pkg
- https://github.com/grafana/grafana/tree/master/pkg
- https://github.com/influxdata/influxdb/tree/master/pkg

### `/vendor`

Dependensi aplikasi (dikelola secara manual atau dengan dependency management tool favorit anda seperti fitur baru bawaan 
[`Go Modules`](https://github.com/golang/go/wiki/Modules). Perintah `go mod vendor` akan membuat direktori `/vendor `untuk anda. 
Perlu dicatat bahwa anda mungkin perlu menambahkan flag `-mod=vendor` ke perintah `go build` jika anda tidak menggunakan 
Go 1.14 di mana fitur tersebut sudah diaktifkan secara default.

Jangan meng-commit dependency aplikasi anda jika anda sedang membangun sebuah library. Perlu dicatat bahwa sejak versi 
[`1.13`](https://golang.org/doc/go1.13#modules), Go telah mengaktifkan fitur module proxy (menggunakan 
[`https://proxy.golang.org`](https://proxy.golang.org) sebagai server proxy modul default). Baca lebih lanjut tentang fitur ini 
[`di sini`](https://blog.golang.org/module-mirror-launch) untuk melihat apakah sesuai dengan semua persyaratan dan batasan anda. 
Jika sesuai, maka anda sama sekali tidak perlu menggunakan direktori `vendor`.

## Direktori Servis Aplikasi

### `/api`

Spesifikasi OpenAPI/Swagger, file skema JSON, file definisi protokol.

Untuk contoh-contoh lebih lanjut bisa lihat berikut:

- https://github.com/kubernetes/kubernetes/tree/master/api
- https://github.com/moby/moby/tree/master/api

### `/web`

Komponen-komponen spesifik aplikasi web: aset web statis, template di sisi server, dan SPAs.

## Direktori Umum Aplikasi

### `/configs`

Template file konfigurasi atau konfigurasi default. Letakkan file template anda di `confd` atau `consul-template`..

### `/init`

Konfigurasi sistem init (systemd, upstart, sysv) dan manajer proses/supervisor (runit, supervisord).

### `/scripts`

Skrip-skrip untuk melakukan berbagai operasi seperti build, instalasi, analisis, dll. Skrip-skrip ini menjaga Makefile tingkat 
root agar tetap kecil dan sederhana (misalnya, [`https://github.com/hashicorp/terraform/blob/master/Makefile`](https://github.com/hashicorp/terraform/blob/master/Makefile)).

Untuk contoh-contoh lebih lanjut bisa lihat berikut:

- https://github.com/kubernetes/helm/tree/master/scripts
- https://github.com/cockroachdb/cockroach/tree/master/scripts
- https://github.com/hashicorp/terraform/tree/master/scripts

### `/build`

Pemaketan (Packaging) dan Integrasi Berkelanjutan (Continuous Integration).

Letakkan skrip paket dan konfigurasi untuk cloud (AMI), container (Docker), sistem operasi (deb, rpm, pkg) anda di direktori `/build/package`.
Letakkan skrip dan konfigurasi CI (travis, circle, drone) anda di direktori `/build/ci`. Perhatikan bahwa beberapa tools CI 
(misalnya, Travis CI) sangat ketat mengenai lokasi file konfigurasi mereka. Coba letakkan file konfigurasi di direktori `/build/ci` 
dan buat tautan ke lokasi yang diharapkan oleh tools CI (jika memungkinkan).

### `/deployments`

Konfigurasi dan template untuk IaaS, PaaS, orkestrasi sistem, dan container (docker-compose, kubernetes/helm, mesos, terraform, 
bosh). Perhatikan bahwa dalam beberapa repositori (terutama aplikasi yang diimplementasikan dengan kubernetes), direktori 
ini disebut `/deploy`.

### `/test`

Tambahan eksternal untuk menguji aplikasi dan data. Aturlah struktur direktori `/test` sesuai keinginan anda. Untuk proyek 
yang lebih besar, disarankan memiliki subdirektori data. Misalnya, anda dapat memiliki `/test/data` atau `/test/testdata` 
jika anda ingin Go mengabaikan apa yang ada dalam direktori tersebut. Perhatikan bahwa Go juga akan mengabaikan direktori 
atau file yang dimulai dengan "." atau "_", sehingga anda memiliki fleksibilitas lebih dalam penamaan direktori data pengujian.

Untuk contoh-contoh lebih lanjut bisa lihat berikut:

- https://github.com/openshift/origin/tree/master/test (test data berada di dalam /testdata subdirectory)

## Direktori Lainnya

### `/docs`

Dokumentasi desain dan pengguna (selain dokumentasi yang dihasilkan oleh godoc).

Untuk contoh-contoh lebih lanjut bisa lihat berikut:

- https://github.com/gohugoio/hugo/tree/master/docs
- https://github.com/openshift/origin/tree/master/docs
- https://github.com/dapr/dapr/tree/master/docs

### `/tools`

Tools pendukung untuk proyek ini. Perhatikan bahwa tools ini dapat mengimpor kode dari direktori `/pkg` dan `/internal`.

Untuk contoh-contoh lebih lanjut bisa lihat berikut:

- https://github.com/istio/istio/tree/master/tools
- https://github.com/openshift/origin/tree/master/tools
- https://github.com/dapr/dapr/tree/master/tools

### `/examples`

Contoh-contoh aplikasi atau library publik anda.

Untuk contoh-contoh lebih lanjut bisa lihat berikut:

- https://github.com/nats-io/nats.go/tree/master/examples
- https://github.com/docker-slim/docker-slim/tree/master/examples
- https://github.com/hashicorp/packer/tree/master/examples

### `/third_party`

Tools eksternal, kode yang di-fork, dan utilitas pihak ketiga (third party) lainnya (misalnya, Swagger UI).

### `/githooks`

Git hooks.

### `/assets`

Aset lainnya yang ada di repositori anda (gambar, logo, dll).

### `/website`

Tempat untuk meletakkan data situs web proyek anda jika anda tidak menggunakan halaman GitHub.

Untuk contoh-contoh lebih lanjut bisa lihat berikut:

- https://github.com/hashicorp/vault/tree/master/website
- https://github.com/perkeep/perkeep/tree/master/website

## Direktori yang Sebaiknya Tidak Dimiliki

### `/src`

Beberapa proyek Go memiliki folder `src`, akan tetapi ini biasanya terjadi ketika pengembang berasal dari dunia Java di mana 
itu adalah pola umum. Jika memungkinkan, hindari mengadopsi pola Java ini. Anda benar-benar tidak ingin kode Go atau proyek 
Go anda terlihat seperti Java.

Jangan bingung antara direktori proyek `/src` dengan direktori `/src` yang digunakan Go untuk workspace-nya seperti yang 
dijelaskan dalam [`How to Write Go Code`](https://golang.org/doc/code.html). Variabel environtment `$GOPATH` menunjuk ke 
workspace anda saat ini (secara default menunjuk ke `$HOME/go` pada sistem non-Windows). Workspace ini mencakup direktori 
top level `/pkg`, `/bin`, dan `/src`. Proyek aktual anda berada di bawah direktori `/src`, jadi jika anda memiliki direktori 
`/src` di proyek anda, path proyek akan terlihat seperti ini: `/some/path/to/workspace/src/your_project/src/your_code.go`. 
Perlu diingat bahwa dengan Go 1.11, memungkinkan untuk memiliki proyek di luar `GOPATH`, tetapi bukan berarti itu adalah 
ide yang baik untuk menggunakan pola tata letak ini.

## Referensi 

- [Standard Go Project Layout](https://github.com/golang-standards/project-layout/tree/master)

Untuk penjelasan lengkap setiap direktori dapat lihat di [Go Project Layout](https://github.com/golang-standards/project-layout)
