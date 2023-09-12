# Operator

Secara umum terdapat 3 kategori operator: aritmatika, perbandingan, dan logika.

## Operator Aritmatika

Operator aritmatika adalah operator yang digunakan untuk operasi yang sifatnya perhitungan. Go mendukung beberapa operator 
aritmatika standar, list-nya bisa dilihat di tabel berikut.

| Tanda | Penjelasan                      |
|-------|---------------------------------|
| `+`   | penjumlahan                     |
| `-`   | pengurangan                     |
| `*`   | perkalian                       |
| `/`   | pembagian                       |
| `%`   | 	modulus / sisa hasil pembagian |

Contoh penggunaan:

```go
var value = (((2 + 6) % 3) * 4 - 2) / 3
```

## Operator Perbandingan

Operator perbandingan digunakan untuk menentukan kebenaran suatu kondisi. Hasilnya berupa nilai boolean, `true` atau `false`.
Tabel di bawah ini berisikan operator perbandingan yang bisa digunakan di Go.

| Tanda | Penjelasan                                                     |
|-------|----------------------------------------------------------------|
| `==`  | apakah nilai kiri __sama dengan__ nilai kanan                  |
| `!=`  | apakah nilai kiri __tidak sama dengan__ nilai kanan            |
| `<`   | apakah nilai kiri __lebih kecil daripada__ nilai kanan         |
| `<=`  | apakah nilai kiri __lebih kecil atau sama dengan__ nilai kanan |
| `>`   | apakah nilai kiri __lebih besar dari__ nilai kanan             |
| `>=`  | apakah nilai kiri __lebih besar atau sama dengan__ nilai kanan |

Contoh penggunaan:

```go
var value = (((2 + 6) % 3) * 4 - 2) / 3
var isEqual = (value == 2)

fmt.Printf("nilai %d (%t) \n", value, isEqual)
```

Pada kode di atas, terdapat statement operasi aritmatika yang hasilnya ditampung oleh variabel `value`. Selanjutnya, variabel 
tersebut dibandingkan dengan angka __2__ untuk dicek apakah nilainya sama. Jika iya, maka hasilnya adalah `true`, jika tidak 
maka `false`. Nilai hasil operasi perbandingan tersebut kemudian disimpan dalam variabel `isEqual`. Untuk memunculkan nilai 
`bool` menggunakan `fmt.Printf()`, bisa gunakan layout format `%t`.

## Operator Logika

Operator ini digunakan untuk mencari benar tidaknya kombinasi data bertipe `bool` (bisa berupa variabel bertipe `bool`, atau 
hasil dari operator perbandingan). Beberapa operator logika standar yang bisa digunakan:

| Tanda  | Penjelasan               |
|--------|--------------------------|
| `&&`   | kiri dan kanan           |
| `\|\|` | kiri atau kanan          |
| `!`    | negasi / nilai kebalikan |

Contoh penggunaan:

```go
var left = false
var right = true

var leftAndRight = left && right
fmt.Printf("left && right \t(%t) \n", leftAndRight)

var leftOrRight = left || right
fmt.Printf("left || right \t(%t) \n", leftOrRight)

var leftReverse = !left
fmt.Printf("!left \t\t(%t) \n", leftReverse)
```

Hasil dari operator logika sama dengan hasil dari operator perbandingan, yaitu berupa boolean. Berikut penjelasan statemen 
operator logika pada kode di atas.

- `leftAndRight` bernilai `false`, karena hasil dari `false` __dan__ `true` adalah `false`. 
- `leftOrRight` bernilai `true`, karena hasil dari `false` **atau** `true` adalah `true`. 
- `leftReverse` bernilai `true`, karena __negasi__ (atau lawan dari)` false` adalah `true`.

Template `\t` digunakan untuk menambahkan indent tabulasi. Biasa dimanfaatkan untuk merapikan tampilan output pada console.