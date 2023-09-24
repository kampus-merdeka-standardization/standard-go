# [Gin](https://github.com/gin-gonic/gin)

Gin adalah _framework_ web yang ditulis dalam [Go](https://go.dev/). Ini menampilkan API seperti martini dengan kinerja
hingga 40 kali lebih cepat berkat [httprouter](https://github.com/julienschmidt/httprouter). Jika membutuhkan performa dan
produktivitas yang baik, Gin sangatlah cocok.

Fitur utama Gin:
1. Zero allocation router
2. Fast
3. Middleware support
4. Crash-free
5. JSON validation
6. Routes grouping
7. Error management
8. Rendering built-in
9. Extendable

## Getting Started

### Prasyarat

- Go: salah satu dari tiga [rilis](https://go.dev/doc/devel/release) _major_ terbaru (diujinya dengan ini).

### Getting Gin

Jalankan perintah Go berikut untuk menginstal _pacakage_ gin:
```shell
$ go get -u github.com/gin-gonic/gin
```

### Running Gin

Pertama, impor paket Gin untuk menggunakan Gin, salah satu contoh paling sederhana seperti berikut `example.go`:
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

Dan gunakan perintah Go untuk menjalankan demo:
```shell
# run example.go and visit 0.0.0.0:8080/ping on browser
$ go run example.go
```