# [Fiber](https://github.com/gofiber/fiber)

Fiber adalah kerangka kerja web yang terinspirasi dari [Express](https://github.com/expressjs/express) yang berbasiskan
[Fasthttp](https://github.com/valyala/fasthttp), HTTP engine paling cepat untuk Go. Dirancang untuk mempermudah, mempercepat
pengembangan aplikasi dengan alokasi memori nol-nya serta kinerja yang selalu diperhatikan.

### Cara Memulai

```go
package main

import "github.com/gofiber/fiber/v2"

func main() {
    app := fiber.New()

    app.Get("/", func(c *fiber.Ctx) error {
        return c.SendString("Hello, World 👋!")
    })

    app.Listen(":3000")
}
```

### Instalasi

Pastikan kamu sudah menginstalasi Golang. Dengan versi `1.17` atau lebih tinggi [ Direkomendasikan ].

Inisialisasi proyek kamu dengan membuat folder lalu jalankan `go mod init github.com/nama-kamu/repo` ([_learn more_](https://go.dev/blog/using-go-modules))
di dalam folder. Kemudian instal Fiber dengan perintah `go get`:
```go
go get -u github.com/gofiber/fiber/v2
```

### Fitur

- Sistem [Routing](https://docs.gofiber.io/guide/routing) yang padu
- Menyajikan [file statis](https://docs.gofiber.io/api/app#static)
- [Kinerja](https://docs.gofiber.io/extra/benchmarks) ekstrim
- [Penggunaan memori](https://docs.gofiber.io/extra/benchmarks) yang kecil
- Cocok untuk [API](https://docs.gofiber.io/api/ctx)
- Mendukung Middleware & [Next](https://docs.gofiber.io/api/ctx#next) seperti Express
- Kembangkan aplikasi dengan [Cepat](https://dev.to/koddr/welcome-to-fiber-an-express-js-styled-fastest-web-framework-written-with-on-golang-497)
- [Template engines](https://github.com/gofiber/template)
- [Mendukung WebSocket](https://github.com/gofiber/websocket)
- [Server-Sent events](https://github.com/gofiber/recipes/tree/master/sse)
- [Rate Limiter](https://docs.gofiber.io/api/middleware/limiter)
- Tersedia dalam [19 bahasa](https://docs.gofiber.io/)
- Dan masih banyak lagi, [kunjungi Fiber](https://docs.gofiber.io/)

### Filosofi

Bagi yang baru yang beralih dari [Node.js](https://nodejs.org/en/about/) ke [Go](https://go.dev/doc/) terkadang perlu waktu
yang cukup lama sebelum mereka mampu membuat aplikasi web dengan Go. Fiber, sebagai **kerangka kerja web** dirancang secara
**minimalis** dan mengikuti filosofi dari **UNIX**, sehingga pengguna baru dapat dengan cepat memasuki dunia Go dengan sambutan
yang hangat dan dapat diandalkan. Fiber terinspirasi dari Express, salah satu kerangka kerja web yang paling terkenal di
Internet. Kami menggabungkan **kemudahan** dari Express dan **kinerja luar biasa** dari Go. Apabila anda pernah membuat
aplikasi dengan Node.js (_dengan Express atau yang lainnya_), maka banyak metode dan prinsip yang akan terasa **sangat umum**
bagi anda.