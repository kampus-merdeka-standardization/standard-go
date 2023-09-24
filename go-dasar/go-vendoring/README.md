# Go Vendoring

## Penjelasan

Vendoring di Go merupakan kapabilitas untuk mengunduh semua dependency atau *3rd party*, untuk disimpan di lokal dalam folder 
project, dalam folder bernama `vendor`. Dengan adanya folder tersebut, maka Go tidak akan *lookup* 3rd party ke cache folder, 
melainkan langsung mempergunakan yang ada dalam folder `vendor`. Jadi tidak perlu download lagi dari internet.

## Praktek Vendoring

Kita akan coba praktekan untuk vendoring sebuah 3rd party bernama [gin](https://github.com/gin-gonic/gin).
Buat folder project baru dengan nama `belajar-vendor` dengan isi satu file `main.go`. Lalu go get gin.

```bash
mkdir belajar-vendor
cd belajar-vendor
go mod init belajar-vendor
go get -u github.com/gin-gonic/gin
```

Isi `main.go` dengan blok kode berikut, untuk menampilkan angka random dengan range 10-20.

```go
package main

import (
	"net/http"

	"github.com/gin-gonic/gin"
)

func main() {
	r := gin.Default()
	r.GET("/ping", func(c *gin.Context) {
		c.JSON(http.StatusOK, gin.H{
			"message": "pong",
		})
	})
	r.Run() // listen and serve on 0.0.0.0:8080 (for windows "localhost:8080")
}
```

Setelah itu jalankan command `go mod vendor` untuk vendoring *3rd party library* yang dipergunakan, dalam contoh ini adlah gin.
Bisa dilihat, sekarang library gin *source code*-nya disimpan dalam folder `vendor`. Nah ini juga akan berlaku untuk semua 
*library* lainnya yg digunakan jika ada.

## Build dan Run Project yang Menerapkan Vendoring

Untuk membuat proses build lookup ke folder vendor, kita tidak perlu melakukan apa-apa, setidaknya jika versi Go yang diinstall 
adalah 1.14 ke atas. Maka command build maupun run masih sama.

```
go run main.go
go build -o executable
```

Untuk yg menggunakan versi Go di bawah 1.14, penulis sarankan untuk upgrade. Atau bisa gunakan flag `-mod=vendor` untuk 
memaksa Go lookup ke folder `vendor`.

```
go run -mod=vendor main.go
go build -mod=vendor -o executable
```

## Manfaat Vendoring

Manfaat vendoring adalah pada sisi kompatibilitas dan kestabilan 3rd party. Jadi dengan vendor, misal 3rd party yang kita 
gunakan di itu ada update yg sifatnya tidak *backward compatible*, maka aplikasi kita tetap aman karena menggunakan yang 
ada dalam folder `vendor`. Jika tidak menggunakan vendoring, maka bisa saja saat `go mod tidy` sukses, namun sewaktu build 
error, karena ada fungsi yg tidak kompatibel lagi misalnya.