# Go Web Framework

Pada bagian Go Web Framework ini, hanya akan membahas 3 framework yang cukup populer di Golang. Dintaranya adalah [Gin](https://github.com/gin-gonic/gin), 
[Fiber](https://github.com/gofiber/fiber), dan [Gorilla Mux](https://github.com/gorilla/mux).

## [Gin](https://github.com/gemm123/standard-go/blob/master/go-lanjut/go-web-framework/gin/README.md)

Gin adalah _framework_ web yang ditulis dalam [Go](https://go.dev/). Ini menampilkan API seperti martini dengan kinerja
hingga 40 kali lebih cepat berkat [httprouter](https://github.com/julienschmidt/httprouter). Jika membutuhkan performa dan
produktivitas yang baik, Gin sangatlah cocok.

## [Fiber](https://github.com/gemm123/standard-go/blob/master/go-lanjut/go-web-framework/fiber/README.md)

Fiber adalah kerangka kerja web yang terinspirasi dari [Express](https://github.com/expressjs/express) yang berbasiskan 
[Fasthttp](https://github.com/valyala/fasthttp), HTTP engine paling cepat untuk Go. Dirancang untuk mempermudah, mempercepat 
pengembangan aplikasi dengan alokasi memori nol-nya serta kinerja yang selalu diperhatikan.

## [Gorilla-mux](https://github.com/gemm123/standard-go/blob/master/go-lanjut/go-web-framework/gorilla-mux/README.md)

_Package_ gorila/mux mengimplementasikan router dan operator permintaan untuk mencocokkan permintaan masuk ke penanganannya 
masing-masing. Nama mux adalah singkatan dari "HTTP request multiplexer". Seperti `http.ServeMux` standar, `mux.Router` mencocokkan 
permintaan masuk dengan _registered routes_  dan memanggil _handler_ untuk _route_ yang cocok dengan URL atau kondisi lainnya.