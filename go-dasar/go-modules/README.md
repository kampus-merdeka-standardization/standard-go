# Go Modules

Go modules meruapakan manajemen dependensi resmi untuk Go. Modules ini diperkenalkan pertama kali di `go1.11`, sebemum itu
pengembangan project Go dilakukan dalam `GOPATH`. Modules digunakan untuk menginisialisasi sebuah project, sekaligus melakukan
manajemen terhadap 3rd party atau library lain yang dipergunakan. Modules penggunaannya adalah lewat CLI. Dan jika teman-teman
sudah sukses meng-install Go, maka otomatis bisa mempergunakan Go Modules.

## Inisialisasi Project Menggunakan Go Modules

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