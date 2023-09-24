# Gorilla-mux

Gorilla Mux adalah framework yang sangat berguna dalam ekosistem bahasa pemrograman Go (Golang) untuk membangun aplikasi web 
berbasis HTTP. Salah satu fitur utamanya adalah kemampuan untuk mengelola routing dengan fleksibilitas tinggi, memungkinkan 
Anda untuk mendefinisikan pola rute yang kompleks dan menghubungkannya dengan fungsi pengendali yang sesuai. Anda dapat dengan 
mudah mengekstrak parameter dari URL, memungkinkan Anda untuk mengambil data dari URL dan menggunakannya dalam pemrosesan permintaan.

Nama "mux" dalam Gorilla Mux merupakan singkatan dari "HTTP request multiplexer" atau pemusat penggandaan permintaan HTTP. 
Mirip dengan http.ServeMux standar, mux.Router pada dasarnya adalah sebuah alat yang digunakan untuk mencocokkan permintaan 
HTTP yang masuk dengan daftar rute yang telah didaftarkan, dan kemudian memanggil sebuah pengendali (handler) yang sesuai 
dengan rute yang cocok dengan URL atau kondisi lainnya. 

## Install

```go
go get -u github.com/gorilla/mux
```

## Contoh

Mari kita mulai dengan mendaftarkan beberapa path URL dan _handler_:

```go
func main() {
    r := mux.NewRouter()
    r.HandleFunc("/", HomeHandler)
    r.HandleFunc("/products", ProductsHandler)
    r.HandleFunc("/articles", ArticlesHandler)
    http.Handle("/", r)
}
```

Di sini kita mendaftarkan tiga rute yang mengaitkan path URL dengan pengendali. Ini setara dengan cara kerja `http.HandleFunc()`.
Jika URL permintaan yang masuk cocok dengan salah satu path, maka pengendali yang sesuai akan dipanggil dengan parameter 
(`http.ResponseWriter`, `*http.Request`)

Path-path tersebut dapat memiliki variabel. Variabel ini didefinisikan menggunakan format `{name}` atau `{name:pattern}`. Jika pola 
ekspresi reguler tidak ditentukan, variabel yang cocok akan berisi segala sesuatu hingga tanda garis miring ("/") berikutnya. 
Sebagai contoh:

```go
r := mux.NewRouter()
r.HandleFunc("/products/{key}", ProductHandler)
r.HandleFunc("/articles/{category}/", ArticlesCategoryHandler)
r.HandleFunc("/articles/{category}/{id:[0-9]+}", ArticleHandler)
```

Nama-nama ini digunakan untuk membuat _map_ dari variabel _route_ yang dapat diambil dengan memanggil `mux.Vars()`:

```go
func ArticlesCategoryHandler(w http.ResponseWriter, r *http.Request) {
    vars := mux.Vars(r)
    w.WriteHeader(http.StatusOK)
    fmt.Fprintf(w, "Category: %v\n", vars["category"])
}
```

Dan ini adalah semua yang perlu Anda ketahui tentang penggunaan dasarnya.

## Referensi

- [gorilla-mux](https://github.com/gorilla/mux/blob/main/README.md)