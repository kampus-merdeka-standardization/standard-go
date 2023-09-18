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

## Gin vs Fiber vs Gorilla Mux

| Aspek      | Gin                      | Fiber                              | Gorilla Mux                      |
|------------|--------------------------|------------------------------------|----------------------------------|
| Kelebihan  | - Kinerja tinggi         | - Kinerja tinggi                   | - Routing yang kuat              |
|            | - Routing yang sederhana | - Sintaks mudah dipahami           | - Fleksibilitas                  |
|            | - Middleware yang kuat   | - Middleware yang kuat             |                                  |
|            | - Banyak plugin tersedia | - Sintaks mirip Express.js         |                                  |
| Kekurangan | - Kurangnya fitur penuh  | - Kurangnya ekosistem yang matang  | - Tidak secanggih framework lain |
|            |                          | - Beberapa fitur mungkin belum ada | - Belajar curva tinggi           |

| Komponen        | Gin | Fiber | Gorilla Mux |
|-----------------|-----|-------|-------------|
| Maintenance     | 4   | 4     | 4           |
| Reputable       | 4   | 4     | 4           |
| Compatibility   |     |       |             |
| Community       | 4   | 4     | 3           |
| Documentation   | 4   | 4     | 3           |
| Licensing       | 4   | 4     | 4           |
| Extensible      |     |       |             |
| Size            | 4   | 2     | 4           |
| **Total Score** |     |       |             |


## Kesimpulan

Pilihan antara Gin, Fiber, atau Gorilla Mux akan tergantung pada kebutuhan dan preferensi pengembang. Gin dan Fiber lebih 
cocok untuk pengembangan aplikasi web berkinerja tinggi, sedangkan Gorilla Mux lebih fleksibel dan cocok digunakan bersama 
dengan berbagai pustaka lain. Semua framework ini memiliki komunitas yang aktif, sehingga Anda dapat dengan mudah menemukan 
dukungan dan sumber daya tambahan untuk membangun aplikasi web Go yang kuat.