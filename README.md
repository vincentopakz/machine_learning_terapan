# Laporan Proyek Machine Learning - Vincent
## Domain Proyek

Latar belakang dari proyek ini adalah tantangan untuk memprediksi harga penutupan ETF Emas yang disesuaikan di masa depan selama periode waktu tertentu di masa depan. Masalah ini merupakan masalah regresi, karena nilai output yang merupakan harga penutupan yang disesuaikan dalam proyek ini adalah nilai kontinu.

### Latar Belakang
  
Secara historis, emas telah digunakan sebagai bentuk mata uang di berbagai belahan dunia termasuk Amerika Serikat. Saat ini, logam mulia seperti emas dipegang oleh bank sentral semua negara untuk menjamin pembayaran kembali utang luar negeri, dan juga untuk mengendalikan inflasi yang mencerminkan kekuatan keuangan negara. Baru-baru ini, ekonomi dunia yang sedang berkembang, seperti Cina, Rusia, dan India telah menjadi pembeli emas yang besar, sedangkan AS, SoUSA, Afrika Selatan, dan Australia termasuk di antara penjual emas yang besar.

Peramalan kenaikan dan penurunan harga emas harian dapat membantu investor untuk memutuskan kapan harus membeli (atau menjual) komoditas. Tetapi harga Emas bergantung pada banyak faktor seperti harga logam mulia lainnya, harga minyak mentah, kinerja bursa saham, harga Obligasi, nilai tukar mata uang, dll.

## Business Understanding

### Problem Statements
Berdasarkan pada latar belakang di atas, permasalahan yang dapat diselesaikan pada proyek ini adalah sebagai berikut:

-   Bagaimana melakukan pengolahan dataset agar dapat memperoleh data yang baik untuk model machine Learning?
-   Bagaimana membangun model machine learning untuk memprediksi harga satu bulan selanjutnya?

### Goals
Tujuan dibuatnya proyek ini adalah sebagai berikut:

-   Melakukan pengolahan dataset harga emas agar dapat digunakan dalam membangun model.
-   Membangun model machine learning untuk memprediksi harga satu bulan selanjutnya

### Solution statements
Solusi yang dapat dilakukan untuk memenuhi tujuan dari proyek ini di antaranya:

- Pengolahan data dapat dilakukan beberapa tahapan, antara lain:
  
    -   Melakukan perhitungan rerata berdasarkan data High dan Low.
    -   Melakukan pembagian dataset.
    -   Standardisasi data fitur numerik pada dataset.
  
- Perancangan model dapat dilakukan dengan beberapa algoritma, antara lain:
  - _K-Nearest Neighbors_
  - _Random Forest_
  - _XGBoost Algorithm_
    
## Data Understanding
- **Informasi Dataset**
   Data untuk penelitian ini dikumpulkan dari 18 November 2011 hingga 1 Januari 2019 dari _yahoo finance_. Informasi lebih lanjut mengenai dataset tersebut dapat lihat pada tabel berikut:

  | Jenis                   | Keterangan                                                                              |
  | ----------------------- | --------------------------------------------------------------------------------------- |
  | Sumber                  | Dataset: [Kaggle](https://www.kaggle.com/datasets/sid321axn/gold-price-prediction-dataset) |
  | Dataset Owner           | Manu Siddhartha                                                                          |
  | Lisensi                 | CC0: Public Domain                                                                        |
  | Kategori                | Finance, Economics                                                                |
  | Usability               | 9.41                                                                                      |
  | Jenis dan Ukuran Berkas | CSV (1.04 MB)                                                                           |

  Setelah melakukan observasi pada dataset yang diunduh melalui _link_ Kaggle yaitu `FINAL_USO.csv`, didapatkan informasi sebagai berikut :
  
  - Data memiliki total 1718 baris yang berisi informasi mengenai data riwayat harga Emas setiap harinya.
  - Terdapat 81 kolom yaitu `Date, Open, High, Low, Close, Adj Close, Volume, SP_open, SP_high, SP_low, SP_close, SP_Ajclose, SP_volume, DJ_open, DJ_high, DJ_low, DJ_close, DJ_Ajclose, DJ_volume, EG_open, EG_high, EG_low, EG_close, EG_Ajclose, EG_volume, EU_Price, EU_open, EU_high, EU_low, EU_Trend, OF_Price, OF_Open, OF_High, OF_Low, OF_Volume, OF_Trend, OS_Price, OS_Open, OS_High, OS_Low, OS_Trend, SF_Price, SF_Open, SF_High, SF_Low, SF_Volume, SF_Trend, USB_Price, USB_Open, USB_High, USB_Low, USB_Trend, PLT_Price, PLT_Open, PLT_High, PLT_Low, PLT_Trend, PLD_Price, PLD_Open, PLD_High, PLD_Low, PLD_Trend, RHO_PRICE, USDI_Price, USDI_Open, USDI_High, USDI_Low, USDI_Volume, USDI_Trend, GDX_Open, GDX_High, GDX_Low, GDX_Close, GDX_Adj Close, GDX_Volume, USO_Open, USO_High, USO_Low, USO_Close, USO_Adj Close, USO_Volume
` yang merupakan variabel - variabel pada data
  - Dari kolom-kolom tersebut terdapat 58 kolom numerik dengan tipe data float64 dan terdapat 22 kolom numerik dengan tipe data int64.
  - Tidak terdapat _missing value_ pada dataset. 
  
  Untuk penjelasan mengenai variabel-variabel pada dataset dapat dilihat pada poin-poin berikut ini:

    *   Date: Tanggal pengamatan
    *   Open: Harga awal pada saat pembukaan perdagangan pada hari tersebut
    *   High: Harga tertinggi yang dicapai pada hari itu
    *   Low: Harga terendah yang dicapai pada hari itu
    *   Close: Harga terakhir pada saat penutupan perdagangan pada hari tersebut
    *   Adj Close: Harga penutupan yang disesuaikan untuk memperhitungkan perubahan pada dividen, saham terbagi, dan sebagainya.
    *   Volume: Jumlah saham atau kontrak yang diperdagangkan pada hari itu
    *   SP_open: Harga pembukaan indeks saham S&P 500 pada hari itu
    *   SP_high: Harga tertinggi indeks saham S&P 500 pada hari itu
    *   SP_low: Harga terendah indeks saham S&P 500 pada hari itu
    *   SP_close: Harga penutupan indeks saham S&P 500 pada hari itu
    *   SP_Ajclose: Harga penutupan indeks saham S&P 500 yang disesuaikan
    *   SP_volume: Jumlah saham atau kontrak yang diperdagangkan pada indeks saham S&P 500 pada hari itu
    *   DJ_open: Harga pembukaan indeks saham Dow Jones pada hari itu
    *   DJ_high: Harga tertinggi indeks saham Dow Jones pada hari itu
    *   DJ_low: Harga terendah indeks saham Dow Jones pada hari itu
    *   DJ_close: Harga penutupan indeks saham Dow Jones pada hari itu
    *   DJ_Ajclose: Harga penutupan indeks saham Dow Jones yang disesuaikan
    *   DJ_volume: Jumlah saham atau kontrak yang diperdagangkan pada indeks saham Dow Jones pada hari itu
    *   EG_open: Harga pembukaan saham perusahaan EG pada hari itu
    *   EG_high: Harga tertinggi saham perusahaan EG pada hari itu
    *   EG_low: Harga terendah saham perusahaan EG pada hari itu
    *   EG_close: Harga penutupan saham perusahaan EG pada hari itu
    *   EG_Ajclose: Harga penutupan saham perusahaan EG yang disesuaikan
    *   EG_volume: Jumlah saham atau kontrak yang diperdagangkan pada saham perusahaan EG pada hari itu
    *   EU_Price: Harga euro terhadap dolar AS pada hari itu
    *   EU_open: Harga pembukaan euro terhadap dolar AS pada hari itu
    *   EU_high: Harga tertinggi euro terhadap dolar AS pada hari itu
    *   EU_low: Harga terendah euro terhadap dolar AS pada hari itu
    *   EU_Trend: Trend harga euro terhadap dolar AS pada hari itu
    *   OF_Price: Harga minyak mentah WTI pada hari itu
    *   OF_Open: Harga pembukaan minyak mentah WTI pada hari itu
    *   OF_High: Harga tertinggi minyak mentah WTI pada hari itu


- **Sebaran atau Distribusi Data pada Setiap Fitur**
  sebelum masuk ke tahap distribusi data, kita hapus dulu beberapa variabel yang tidak digunakan dan hanya menyisakan variabel `High` dan `Low`, kemudian menambahkan dua buah variabel baru yaitu variabel `Price_Average` untuk harga rata-rata dan `Price_NextMonth` untuk harga bulan berikutnya. 

    Berikut merupakan visualisasi data yang menunjukkan sebaran/distribusi data pada setiap fitur-fitur numerik (`High, Low, Price_Average, Price_NextMonth`) :
  
  - Mengidentifikasi Missing Value dan Outlier
    <br>
    
    <img src="https://user-images.githubusercontent.com/94229589/232325680-88db42d6-a81a-4985-b000-3e162a98ba1e.png" width="500">
    <br> Terlihat jika di atas banyak terdapat outlier pada setiap variabel, lalu untuk mengatasinya nantinya penulis akan menerapkan batas bawah dan batas atas menggunakan metode IQR
    
  - Univariate Analysis
    <br>
    
    <img src="https://user-images.githubusercontent.com/94229589/232325627-178acd6c-1720-4d89-927b-c4e09a8c681f.png" width="500">
    <br> Terlihat pada grafik bahwa semua data cenderung distribusi nilainya miring ke kanan (right-skewed). Hal ini akan berimplikasi pada model nantinya.
    
  - Multivariate Analysis
    <br>
    
    <img src="https://user-images.githubusercontent.com/94229589/232325604-efb38490-bc51-4030-bf82-7fa1cf136059.png" width="500">
    <br> Terlihat bahwa pada grafik kebanyakan bernilai positif karena kebanyakan grafik pada sumbu y dan x mengalami peningkatan yang cukup signifikan membentuk sebuah garis lurus.
    <br>
    
    <img src="https://user-images.githubusercontent.com/94229589/232325512-97829a34-15f0-4197-a7c5-59fb61010356.png" width="500">
    <br> Terlihat pada matriks korelasi di atas dapat disimpulkan bahwa semua variabel memiliki keterikatan dan korelasi yang kuat antar variabel lainnya, dimana nilai korelasi antar variabel bernilai lebih dari 0.9 atau mendekati 1.
  
## Data Preparation
Berikut ini merupakan tahapan-tahapan dalam melakukan pra-pemrosesan data:
  - **Melakukan Penanganan Missing Value dan Outlier**
    <br> Penanganan yang penulis lakukan pada Missing Value yaitu dengan melakukan drop data, tetapi karena dataset yang digunakan cukup bersih, missing value hanya terdapat pada variabel yang penulis buat pada model untuk membandingkan harga setelah perbulan (Price_NextMonth) sebanyak 30 missing value. Namun penulis tidak akan menghapus semua outliers pada data dikarenakan jika kita menghapus outliers dengan contoh menggunakan metode InterQuartile Range (IQR), maka akan berdampak pada menurunnya tingkat akurasi pada model yang akan kita kerjakan nantinya

  - **Melakukan pembagian dataset**
    <br> Untuk mengetahui kinerja model ketika dihadapkan pada data yang belum pernah dilihat sebelumnya, maka perlu dilakukan pembagian dataset. Pada proyek ini dataset dibagi menjadi data latih dan data uji dengan rasio 80% untuk data latih dan 20% untuk data uji. Data latih merupakan data yang akan kita latih untuk membangun model _machine learning_, sedangkan data uji merupakan data yang belum pernah dilihat oleh model dan digunakan untuk melihat kinerja atau performa dari model yang dilatih.  Pembagian dataset dilakukan dengan modul [train_test_split](https://scikit-learn.org/0.24/modules/generated/sklearn.model_selection.train_test_split.html#sklearn.model_selection.train_test_split) dari scikit-learn. Setelah melakukan pembagian dataset, didapatkan jumlah sample pada data latih yaitu 1350 sampel dan jumlah sample pada data uji yaitu 338 sampel dari total jumlah sample pada dataset yaitu 1688 sampel.
    
  - **Standardisasi data pada semua fitur numerik pada dataset**
  <br> Standardisasi merupakan teknik transformasi yang paling umum digunakan dalam tahap data _preparation_. Standardisasi membantu untuk membuat semua fitur numerik berada dalam skala data yang sama dan membuat fitur data menjadi bentuk yang lebih mudah diolah oleh algoritma. Pada proyek ini, standardisasi data dilakukan dengan menerapkan teknik [StandarScaler](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.StandardScaler.html) dari library Scikitlearn. StandardScaler melakukan proses standardisasi fitur dengan mengurangkan mean (nilai rata-rata) kemudian membaginya dengan standard deviasi untuk menggeser distribusi. StandardScaler menghasilkan distribusi dengan standard deviasi sama dengan 1 dan mean sama dengan 0.
  
## Modeling
Pada proyek ini, Proses modeling dalam proyek ini menggunakan 3 algoritma _machine learning_ yaitu `K-Nearest Neighbor`, `Random Forest` dan `XGBoost Algorithm` kemudian membandingkan performanya.

- **K-Nearest Neighbor**
  <br> KNN bekerja dengan membandingkan jarak satu sampel ke sampel pelatihan lain dengan memilih sejumlah k tetangga terdekat (dengan k adalah sebuah angka positif). Pada tahap ini pembuatan model dilakukan dengan menggunakan modul [KNeighborsClassifier](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsClassifier.html) dari library Scikitlearn dengan nilai k = 10 dan metric Euclidean yang artinya, pada model ini akan membandingkan jarak satu sampel data ke 10 sampel data tetangganya yang terdekat, agar hasil persamaan regresi yang dihasilkannya nantinya akan lebih halus, tahapan itu akan dilakukan berulang-ulang hingga mendapatkan hasil persamaan regresi dengan nilai yang maksimal. Kemudian proses selanjutnya melakukan prediksi menggunakan data uji dan melakukan pengujian.
  -   Kelebihan:
      -   Algoritma KNN merupakan algoritma yang sederhana dan mudah untuk diimplementasikan.
      -   Dapat di implementasikan pada beberapa kasus seperti klasifikasi, regresi dan pencarian.
  -   Kekurangan:
      -   Algoritma KNN menjadi lebih lambat secara signifikan seiring meningkatnya jumlah sampel dan/atau variabel independen.

- **Random Forest**
  <br> Algoritma ini disusun dari banyak algoritma pohon (decision tree) yang pembagian data dan fiturnya dipilih secara acak. Pembuatan model dilakukan dengan menggunakan modul [RandomForestClassifier](https://scikitlearn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html) dari library Scikitlearn. terdapat parameter yang harus digunakan agar hasil dari pembuatan model dapat maksimal. Parameter pertama ialah parameter `n_estimator` yang merupakan jumlah _trees_ (pohon) di _forest_. Di proyek ini penulis melakukan _set_ nilai `n_estimator` sebesar 100 _trees_. Selanjutnya ialah parameter `max_depth` yang merupakan kedalaman atau panjang pohon. Itu merupakan ukuran seberapa banyak pohon dapat membelah (_splitting_) untuk membagi setiap _node_ ke dalam jumlah pengamatan yang di inginkan, di proyek ini penulis melakukan set nilai `max_depth` sebesar 32 _split_. Parameter `random_state` digunakan untuk mengontrol _random number generator_ yang digunakan. Di proyek ini penulis melakukan _set_ nilai pada parameter `random_state` sebesar 55. Lalu yang terakhir ialah parameter `n_jobs` yaitu jumlah _job_ (pekerjaan) yang digunakan secara paralel. Itu merupakan komponen untuk mengontrol _thread_ atau proses yang berjalan secara paralel. `n_jobs = -1` artinya semua proses berjalan secara paralel. Kemudian proses selanjutnya melakukan prediksi menggunakan data uji dan melakukan pengujian.
  -   Kelebihan :
      -   Algoritma Random Forest merupakan algoritma dengan pembelajaran paling akurat yang tersedia. Untuk banyak kumpulan data, algoritma ini menghasilkan pengklasifikasi yang sangat akurat.
      -   Berjalan secara efisien pada data besar.
      -   Dapat menangani ribuan variabel input tanpa penghapusan variabel.
      -   Memberikan perkiraan variabel apa yang penting dalam klasifikasi.
      -   Memiliki metode yang efektif untuk memperkirakan data yang hilang dan menjaga akurasi ketika sebagian besar data hilang.
  -   Kekurangan :
      -   Algoritma Random Forest overfiting untuk beberapa kumpulan data dengan tugas klasifikasi/regresi yang _bising/noise_.
      -   Untuk data yang menyertakan variabel kategorik dengan jumlah level yang berbeda, Random Forest menjadi bias dalam mendukung atribut dengan level yang lebih banyak. Oleh karena itu, skor kepentingan variabel dari Random Forest tidak dapat diandalkan untuk jenis data ini.

- **XGBoost Algorithm**
  <br> XGBoost merupakan salah satu metode boosting yaitu kumpulan DT yang pembangunan pohon berikutnya akan bergantung pada pohon sebelumnya. Pohon pertama dalam XGBoost akan lemah dalam melakukan klasifikasi dengan inisialisasi probability yang ditentukan oleh peneliti dan kemudian akan dilakukan update bobot pada setiap pohon yang dibangun sehingga menghasilkan kumpulan pohon klasifikasi yang kuat. Pada tahap ini pembuatan model dilakukan dengan menggunakan modul [XGBoost Alghoritm](https://xgboost.readthedocs.io/en/stable/python/python_api.html). Penulis menggunakan metode boosting yaitu XGBoost. Algoritma XGBoost adalah algoritma ensemble yang memanfaatkan bagging dan boosting untuk mengembangkan peningkatan akurasi prediktor. Proses XGBoost adalah pemangkasan, newton boosting, dan parameter pengacakan ekstra. Proses pemangkasan atau penyusutan proporsional simpul daun digunakan untuk meningkatkan generalisasi model. proses newton boosting adalah proses untuk menyediakan rute langsung sehingga tidak memerlukan penurunan gradient. Proses pengacakan parameter bertujuan untuk mengurangi korelasi antar tree sehingga dapat meningkatkan kekuatan algoritma ensemble.

Kemudian proses selanjutnya melakukan prediksi menggunakan data uji dan melakukan pengujian.
  -   Kelebihan :
      -   Akurasi yang tinggi
      -   Mendukung berbagai tipe data
      -   Kemampuan feature selection
      -   Mudah digunakan
  -   Kekurangan :
      -   Sangat sensitif terhadap tuning parameter
      -   Memerlukan sumber daya yang cukup
      -   Interpretasi model yang sulit

  Dapat disimpulkan model terbaik yang digunakan untuk dataset ini ialah model KNN di mana KNN memiliki nilai error terkecil dan nilai akurasi yang tinggi ketimbang kedua model lainnya(cek pada bagian Evaluasi)
 
## Evaluation
Metrik yang akan penulis gunakan pada proyek ini adalah MSE atau Mean Squared Error yang menghitung jumlah selisih kuadrat rata-rata nilai sebenarnya dengan nilai prediksi. Karena penulis baru melakukan scaling pada data latih untuk menghindari kebocoran data, maka sebelum menghitung nilai mse, penulis perlu melakukan scaling fitur terlebih dahulu pada data uji. Setelah melakukan scaling data uji barulah MSE dihitung. Secara matematis dihitung dengan persamaan berikut:

<img src="https://user-images.githubusercontent.com/94229589/232325470-cfeea4fe-65f4-4b5c-aa91-fe087a177f87.png" width="200">

keterangan:
N = jumlah dataset,
yi = nilai sebenarnya,
yi^ = nilai prediksi,

Penulis juga melakukan evaluasi dengan menggunakan metrik akurasi, yaitu tingkat keakuran data prediksi yang didasarkan dari data latih pada model. Metrik Akurasi mungkin metrik paling awam/paling diketahui pada pemodelan klasifikasi. Metrik ini adalah persentase jumlah data yang diprediksi secara benar terhadap jumlah keseluruhan data. Jika ditinjau dengan confusion matrix, akurasi adalah rasio dari jumlah elemen diagonal terhadap jumlah seluruh elemen matriks, atau:
   
<img src="https://user-images.githubusercontent.com/94229589/232325361-0ca77056-71b1-4460-8075-5887120a5952.png" width="400">

Berdasarkan metrik akurasi penulis mendapati bahwa model dengan akurasi tertinggi adalah _XGBR Boosting_, yaitu 98.2%%. Sama halnya dengan metrik akurasi, MSE juga menunjukkan bahwa model _XGBR Boosting_ memberikan error yang paling kecil. Sedangkan _KNN_ memiliki error paling besar. Jadi model yang akan penulis gunakan dalam memprediksi harga satu bulan selanjutnya adalah model _XGBR Boosting_.

Berikut ini bisa kita lihat perbandingan grafik MSE dan akurasi ketiga model

<img src="https://user-images.githubusercontent.com/94229589/232324894-395da9d6-149a-4a84-b765-5eff93803434.png" width="400">
     


Berdasarkan tingkat eror pada grafik di atas, semakin kecil tingkat eror maka semakin baik model tersebut memprediksi data. Jika dibandingkan dengan dua model lainnya, model dengan error terkecil adalah Model XGBR Boosting.

