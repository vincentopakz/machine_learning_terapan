# Laporan Proyek Machine Learning - Vincent

## Project Overview
Dalam era digital saat ini, platform streaming film seperti Netflix, Hulu, Amazon Prime, dan lainnya menawarkan ribuan film dan acara televisi dalam berbagai genre. Namun, pengguna seringkali bingung dalam memilih film yang ingin mereka tonton.

Dalam hal ini, sistem rekomendasi film yang menggunakan machine learning dapat membantu pengguna dalam menemukan film yang sesuai dengan preferensi mereka. Sistem ini akan mengumpulkan data tentang preferensi dan aktivitas tontonan pengguna, seperti film yang sudah ditonton dan peringkat yang diberikan, serta informasi tentang genre dan aktor favorit. Kemudian, sistem akan menggunakan algoritma machine learning untuk menganalisis data dan memberikan rekomendasi film yang cocok dengan minat pengguna.

Selain itu, sistem rekomendasi film juga dapat memberikan manfaat bagi industri hiburan. Dengan menggunakan data yang dikumpulkan dari sistem, platform streaming dapat mengidentifikasi tren dan preferensi pengguna, sehingga mereka dapat memproduksi konten yang sesuai dengan permintaan pasar. Hal ini dapat membantu industri hiburan dalam meningkatkan popularitas dan keuntungan mereka.

Secara keseluruhan, proyek machine learning untuk membuat sistem rekomendasi film berdasarkan genre dapat memberikan manfaat bagi pengguna dan industri hiburan secara keseluruhan.

## Business Understanding

### Problem Statement

Bagaimana cara merekomendasikan film yang sesuai dengan preferensi pengguna di platform streaming film yang menawarkan ribuan film dalam berbagai genre?

### Goal

Membangun sebuah sistem rekomendasi film berdasarkan genre dengan machine learning untuk membantu pengguna memilih film di platform streaming.

### Solution

Menggunakan algoritma machine learning untuk menganalisis preferensi pengguna dan memberikan rekomendasi film yang sesuai dengan minat mereka di platform streaming film.

## Data Understanding

  | Jenis                   | Keterangan                                                                              |
  | ----------------------- | --------------------------------------------------------------------------------------- |
  | Sumber                  | Dataset: [Top 100 Rotten Tomatoes movies by genres](https://www.kaggle.com/datasets/prasertk/top-100-rotten-tomatoes-movies-by-genres) |
  | Dataset Owner           | Prasert Kanawattanachai                                                                          |
  | Lisensi                 | CC0: Public Domain                                                                        |
  | Kategori                | Movies & TV Shows                                                                |
  | Usability               | 10.00                                                                                      |
  | Jenis dan Ukuran Berkas | CSV (87.16 kB)                                                                           |
  

1. *top_100_movies_by_genres.csv.csv*
 <br>Keterangan :
 * `Genre` = Genre dari film (object)
   <br>memiliki 17 data unik.
 * `Rank` = Ranking dari film (float64)
   <br>memiliki 100 data unik.
 * `RatingTomatometer` = Rating dari Tomatometer (object)
   <br>memiliki 70 data unik.
 * `Title` = Judul dari film dan tahun perilisan (object)
   <br>memiliki 1007 data unik.
 * `No. of Reviews` = Jumlah peminat film yang memberikan reviews (int64)
   <br>memiliki 304 data unik.
    
 *Jumlah Data 1612, dan memiliki 5 kolom*

## Data Preparation

### Missing Value

Kita cek apakah ada missing values

Fitur | Jumlah Value
----- | ------------
Genre                 | 0
Rank                  | 0
RatingTomatometer     | 0
Title                 | 0
No. of Reviews        | 0

Aman

### Duplicate Value

Kita cek apakah ada row yang duplikasi

Total Movies | Total Row Data
----------- | --------------------
1007 | 1612

Disini terlihat bahwa ada judul film yang memiliki beberapa genre, maka itu kita akan menghapus data duplikasi tersebut.

dan dataframe kita pun menjadi 
<br>  *1005 rows × 5 columns*

Kita juga hanya akan menggunakan kolum Title dan Genre saja

## Modeling

Proses modeling dilakukan dengan membuat algoritma machine learning, yaitu content based filtering

1. Inisialisasi TfidfVectorizer
2. Melakukan perhitungan idf pada data genre
3. Mapping array dari fitur index integer ke fitur name
4. Melakukan fit lalu ditransformasikan ke bentuk matrix
5. Menghitung cosine similarity
6. Membuat dataframe baru menggunakan cosine similarity
7. Membuat fungsi untuk merekomendasikan 10 movies dengan cosine similarity

## Evaluation 

### Mengecek Genre dari sebuah film

No | Title	 | Genre
-- | -------- | ----
477 | 1917 (2020) | Drama

### Rekomendasi dengan Cosine Similarity
No | Title	 | Genre
-- | -------- | ----
0	|	12 Years a Slave (2013)	|	Drama
1	|	Pain and Glory (Dolor y gloria) (2019)	|	Drama
2	|	Nomadland (2021)	|	Drama
3	|	Sound of Metal (2020)	|	Drama
4	|	Schindler's List (1993)	|	Drama
5	|	Never Rarely Sometimes Always (2020)	|	Drama
6	|	Call Me by Your Name (2018)	|	Drama
7	|	The Florida Project (2017)	|	Drama
8	|	The Godfather, Part II (1974)	|	Drama
9	|	Widows (2018)	|	Drama

Sistem merekomendasikan 10 judul film yang relevan dengan judul 1917 (2020) yang memiliki genre Drama
