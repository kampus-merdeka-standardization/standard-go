# Database

Library database menyediakan antarmuka untuk berinteraksi dengan basis data. Pengembang dapat menggunakan library ini untuk
melakukan operasi seperti mengambil, menyimpan, atau mengubah data dalam basis data.

Berikut adalah library database di Golang:

## Relational Database Management System (RDBMS)

### [pgx](https://github.com/jackc/pgx)

pgx adalah driver dan toolkit murni dalam bahasa pemrograman Go untuk PostgreSQL. Driver pgx adalah antarmuka tingkat rendah 
yang memiliki kinerja tinggi dan mengekspos fitur-fitur khusus PostgreSQL seperti LISTEN / NOTIFY dan COPY. Ini juga mencakup 
sebuah adapter untuk antarmuka database/sql standar. Komponen toolkit adalah seperangkat paket terkait yang mengimplementasikan 
fungsi-fungsi PostgreSQL seperti pemrosesan protokol wire dan pemetaan tipe antara PostgreSQL dan Go. Paket-paket dasar ini 
dapat digunakan untuk mengimplementasikan driver alternatif, proxy, load balancer, klien replikasi logis, dan sebagainya.

### [GORM](https://github.com/go-gorm/gorm)

GORM adalah library ORM (Object-Relational Mapping) yang sangat populer dalam bahasa pemrograman Go (Golang). GORM memungkinkan 
pengembang untuk berinteraksi dengan basis data relasional seperti MySQL, PostgreSQL, dan SQLite dengan cara yang lebih mudah 
dan lebih abstrak. Dengan GORM, Anda dapat mendefinisikan model data dalam kode Go dan menggunakan operasi berorientasi objek 
untuk melakukan pembuatan, pembacaan, pembaruan, dan penghapusan data dalam basis data. Ini memungkinkan pengembang untuk 
fokus pada logika bisnis mereka daripada detail teknis dari SQL. GORM juga menyediakan fitur-fitur canggih seperti pengelolaan 
hubungan antar tabel, migrasi basis data, dan dukungan untuk transaksi.

### [SQLx](https://github.com/jmoiron/sqlx)

SQLx adalah sebuah library yang menyediakan serangkaian ekstensi pada library database/sql standar Go. Versi SQLx dari sql.DB, 
sql.TX, sql.Stmt, dan lain-lain, semuanya menjaga antarmuka dasarnya tidak berubah, sehingga antarmuka mereka adalah himpunan 
data yang lebih lengkap dari versi standar. Hal ini membuat integrasi kode-kode yang sudah ada yang menggunakan database/sql 
dengan SQLx menjadi relatif tidak menyakitkan.

## Key-Value

### [Go Redis](https://github.com/redis/go-redis)

Library Go Redis adalah sebuah library yang digunakan untuk berinteraksi dengan Redis, yang merupakan sistem penyimpanan 
data berkinerja tinggi berbasis key-value. Go Redis menyediakan API yang kuat untuk mengakses, memanipulasi, dan memanage 
data di Redis melalui aplikasi Go Anda. Ini memungkinkan Anda untuk melakukan operasi seperti menyimpan dan mengambil data, 
mengatur nilai-nilai dalam hash, melakukan operasi set, mengelola daftar, dan banyak lagi. Go Redis sangat berguna untuk 
membangun aplikasi berkinerja tinggi yang membutuhkan penyimpanan data cepat dan efisien, serta berfungsi sebagai cache dalam 
arsitektur mikro dan aplikasi terdistribusi.

## Document

### [MongoDB Go Driver](https://github.com/mongodb/mongo-go-driver)

MongoDB adalah salah satu basis data dokumen terkemuka, dan MongoDB Go Driver adalah library resmi yang memungkinkan Anda 
berinteraksi dengan MongoDB menggunakan Go. Anda dapat menggunakan driver ini untuk melakukan operasi seperti menyimpan, 
mengambil, mengubah, dan menghapus dokumen dalam MongoDB.

## Graph

### [Neo4j Go Driver](https://github.com/neo4j/neo4j-go-driver)

Neo4j Go Driver adalah library resmi yang memungkinkan pengembang Go (Golang) untuk berinteraksi dengan basis data grafik 
Neo4j. Driver ini menyediakan API yang kuat untuk melakukan operasi seperti menyimpan, mengambil, dan mengubah data dalam 
Neo4j menggunakan Go. Salah satu fitur utama dari driver ini adalah dukungan penuh untuk bahasa query Cypher yang digunakan 
secara umum dalam Neo4j.