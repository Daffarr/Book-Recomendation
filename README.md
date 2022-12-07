# *Book Recommendation* - Daffa Rayhan Riadi
 
## *Project Overview*

Perpustakaan adalah tempat koleksi besar dari buku dan bahan bacaan lainnya yang umumnya dikelola oleh institusi untuk dimanfaatkan oleh masyarakat luas sebagai sarana informasi dan pengetahuan. Dalam perkembangannya sejalan dengan perkembangan teknologi informasi, sehingga perpustakaan pun ikut berkembang dengan penyediaan koleksi bahan bacaan dalam bentuk digital yang umumnya diistilahkan sebagai sistem informasi perpustakaan. Sekarang sudah ada beberapa perpustakaan yang menerapkan teknologi informasi di dalam layanan nya seperti layanan sistem informasi yang disebut dengan *Online Public Acces Catalog* (*OPAC*). *OPAC* adalah sistem katalog terpasang yang dapat diakses secara umum dan dapat dipakai pengguna untuk menelusuri katalog buku, kemudian setelah katalog buku ditemukan, maka sistem akan menampilkan seluruh informasi dari buku nya.

Namun selama ini tidak sedikit pula pengunjung perpustakaan yang mengalami kesulitan dalam mencari buku yang memiliki kesamaan atau berkaitan dengan buku yang dibaca atau dipilih sebelumnya. Pengunjung pastinya memerlukan waktu yang relatif lama sebab koleksi buku perpustakaan yang sangat banyak. Oleh karena itu diperlukan sebuah sistem yang dapat membantu merekomendasikan kepada para pengunjung perpustakaan tersebut, agar lebih mudah mendapatkan informasi mengenai buku-buku yang memiliki kesamaan dengan buku yang dibaca atau dipilih sebelumnya.

Sistem rekomendasi adalah salah satu fitur pada sebuah perangkat lunak yang sangat bermanfaat untuk memudahkan pengguna dalam mendapatkan saran untuk barang (*item*) yang kemungkinan besar sedang dicari dan menarik bagi pengguna. Sistem rekomendasi sendiri sangat diperlukan dikarenakan terlalu banyaknya jenis dan jumlah data yang ada. Dengan adanya sistem rekomendasi, pengguna akan dimanjakan dengan rekomendasi–rekomendasi buku yang sesuai dengan preferensi masing–masing pengguna, sehingga pengguna tidak perlu repot lagi dalam melakukan pencarian buku yang diinginkan. Sistem rekomendasi sendiri harus dapat menganalisis sekian banyak data tentang pengguna dan buku yang tersedia, dapat juga didukung dengan data *rating* agar hasil yang diberikan lebih akurat.

Berdasarkan latar belakang yang telah dijelaskan di atas, topik proyek ini diambil dengan tujuan sebagai domain proyek *machine learning* yang akan dibuat. Selain itu, proyek ini dibuat untuk dapat menambah pengalaman yang menyenangkan kepada pengunjung perpustakaan. Diharapkan sistem rekomendasi ini dapat digunakan pada sebuah layanan di sebuah perpustakaan dan memberikan rekomendasi yang relevan sesuai dengan preferensi pengguna dan dapat meningkatkan kenyamanan pengguna saat menggunakan layanan ini.

## *Business Understanding*
### *Problem Statements*
Berdasarkan pada latar belakang diatas, permasalahan yang dapat diselesaikan pada proyek ini adalah sebagai berikut: 
Menjelaskan pernyataan masalah:
- Bagaimana cara memproses data sehingga dapat di latih dengan baik oleh model?
- Bagaimana cara membangun model *machine learning* yang dapat memberikan hasil rekomendasi yang baik dan relevan dan sesuai dengan preferensi pengguna?

### *Goals*
Tujuan dibuatnya proyek ini adalah sebagai berikut:
- Dapat memproses data dengan baik sehingga dapat dipahami oleh model serta mendapatkan hasil rekomendasi yang baik.
- Membangun model *machine learning* yang baik sehingga dapat memberikan hasil rekomendasi yang relevan dan sesuai dengan preferensi pengguna.

### *Solution Statements*
Solusi yang dapat diterapkan agar goals diatas terpenuhi adalah sebagai berikut:
- Melakukan analisa pada data untuk dapat memahami data yang ada. Analisa yang dapat dilakukan yaitu, antara lain:
  - Menangani *missing value* pada *dataset*.
  - Menangani data yang duplikat pada *dataset*
- Melakukan pemrosesan pada data seperti:
  - Menggabungkan data buku dan *rating* sehingga dapat lebih mudah dipahami oleh model *machine learning*
  - Normalisasi *rating* pada *dataset* sehingga dapat di proses lebih mudah oleh model *machine learning*.
- Membangun model *machine learning* dengan menggunakan salah satu teknik algoritma *machine learning* yang umum digunakan yaitu ***Collaborative Filtering* (*CF*)**

## *Data Understanding*
Sesuai dengan Domain Proyek diatas, *dataset* yang digunakan disini adalah *dataset* mengenai **Buku**. *Dataset* ini diambil dari platform [Kaggle](https://www.kaggle.com/). *Dataset* ini berformat ***CSV*** didalamnya terdapat 3 *file* **(*Books.csv, Ratings.csv, Users.csv*)**. Pada proyek kali ini hanya akan menggunakan file ***Books.csv*** dan ***Ratings.csv*** saja. *Dataset* tersebut dapat di unduh pada website kaggle berikut: [*Book Recommendation Dataset*](https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset).

Penjelasan mengenai data ***Books.csv*** dan ***Ratings.csv*** sebagai berikut:
- ***Books.csv***
  
  Variabel-variabel pada *Books.csv* adalah sebagai berikut:
  - ***ISBN***: Kode pengidentifikasian buku yang bersifat unik.
  - ***Book-Title***: Judul Buku.
  - ***Book-Author***: Nama pengarang buku.
  - ***Year-Of-Publication***: Tahun penerbitan buku.
  - ***Publisher***: Pihak penerbit buku.
  - ***Image-URL-S***: URL yang menautkan ke gambar sampul berukuran kecil.
  - ***Image-URL-M***: URL yang menautkan ke gambar sampul berukuran normal.
  - ***Image-URL-L***: URL yang menautkan ke gambar sampul berukuran besar. 

  *File* ini memiliki **271360 baris** dan **8 kolom** sampel data dan semua tipe data variabel dari *file Books.csv* adalah *object*, dapat dilihat sebagai berikut:
  
  Tabel 1 *Books.csv*
  
  | # | ***Column*** | ***Non-Null Count*** | ***Dtype*** |
  |---|---|---|---|
  | 0 | *ISBN* | 271360 *non-null* | *object* |
  | 1 | *Book-Title* | 271360 *non-null* | *object* |
  | 2 | *Book-Author* | 271359 *non-null* | *object* |
  | 3 | *Year-Of-Publication* | 271360 *non-null* | *object* |
  | 4 | *Publisher* | 271358 *non-null* | *object* |
  | 5 | *Image-URL-S* | 271360 *non-null* | *object* |
  | 6 | *Image-URL-M* | 271360 *non-null* | *object* |
  | 7 | *Image-URL-L* | 271357 *non-null* | *object* |
  
- ***Ratings.csv***

  Variabel-variabel pada *Ratings.csv* adalah sebagai berikut:
  - ***User-ID***: Nomer unik user yang memberikan *rating*.
  - ***ISBN***: Kode pengidentifikasian buku yang bersifat unik.
  - ***Book-Rating***: Skor dari *rating* yang diberikan.

  *File* ini memiliki **102023 baris** dan **3 kolom** sampel data dan tipe data variabel yang dimiliki oleh *file Rating.csv* adalah *integer* dan *object*, dapat dilihat sebagai berikut:
  
  Tabel 2 *Ratings.csv*
  
  | # | ***Column*** | ***Non-Null Count*** | ***Dtype*** |
  |---|---|---|---|
  | 0 | *User-ID* | 1149780 *non-null* | *int64* |
  | 1 | *ISBN* | 1149780 *non-null* | *object* |
  | 2 | *Book-Rating* | 1149780 *non-null* | *int64* |

### Exploratory Data Analysis
Sebelum melakukan pemrosesan data untuk pelatihan, perlu dilakukan analisa pada data untuk mengetahui keadaan pada data seperti eksplorasi pada data, eksplorasi yang di lakukan antara lain:

- Menghitung Shape Buku dan *Rating*
  Disini dapat diketahui bahwa shape data yang ada pada kedua *dataset* ini sebagai berikut:
 
  |***Dataset***| ***Row*** | ***Column*** |
  |:---:|:---:|:---:|
  | *Books* | 271360 | 8 |
  | *Ratings* | 1149780 | 3 |

- Memeriksa *Missing Value*
  Jika dilihat dari data buku dan data *rating* tabel di bawah. Terdapat sedikit *missing value* pada data buku, sedangkan pada data *rating* tidak memiliki *missing value* sama sekali.
  
  **Tabel 1** *Missing Value* Data *Books*: 
  |**Fitur**| **Jumlah Duplikasi** |
  |---|:---:|
  | *ISBN* | 0 |
  | *Book-Title* | 0 |
  | *Book-Author* | 1 |
  | *Year-Of-Publication* | 0 |
  | *Publisher* | 2 |
  | *Image-URL-S* | 0 |
  | *Image-URL-M* | 0 |
  | *Image-URL-L* | 3 |

  **Tabel 2** *Missing Value* Data *Rating*: 
  |**Fitur**| **Jumlah Duplikasi** |
  |---|:---:|
  | *User-ID* | 0 |
  | *ISBN* | 0 |
  | *Book-Rating* | 0 |

- Memeriksa Data Yang Duplikasi
  Dapat dilihat pada tampilan *output* yang ada pada tabel di bawah. Tidak terdapat duplikasi pada data *books* di fitur *ISBN* tetapi terdapat banyak duplikasi pada fitur lainnya. Begitu juga pada data *rating*, terdapat banyak duplikasi pada fitur. Tetapi ini hal yang wajar sebab tiap *user* dapat memberikan *rating* pada tiap buku yang berbeda dan buku yang berbeda dapat menerima *rating* dari *user* yang berbeda pula. Tabel dari output tersebut dapat dilihat sebagai berikut:
  
  **Tabel 1** Data Duplikasi *Books*: 
  |**Fitur**| **Jumlah Duplikasi** |
  |---|:---:|
  | *ISBN* | 0 |
  | *Book-Title* | 29225 |
  | *Book-Author* | 169336 |
  | *Year-Of-Publication* | 271158 |
  | *Publisher* | 254552 |
  | *Image-URL-S* | 316 |
  | *Image-URL-M* | 316 |
  | *Image-URL-L* | 318 |
  
  
  **Tabel 2** Data Duplikasi *Rating*: 
  |**Fitur**| **Jumlah Duplikasi** |
  |---|:---:|
  | *User-ID* | 1044497 |
  | *ISBN* | 809224 |
  | *Book-Rating* | 1149769 |

## *Data Preparation*
Berikut merupakan tahapan dalam mempersiapkan data untuk keperluan pelatihan model:

- **Menghapus Data Yang Tidak Digunakan**

  Sistem rekomendasi ini hanya memerlukan data *author* dan *rating* sebagai fitur untuk model. Beberapa kolom data seperti ***'Year-Of-Publication', 'Publisher', 'Image-URL-M', 'Image-URL-L'*** tidak akan digunakan untuk sistem rekomendasi ini. Sehingga data tersebut dapat dihapus.
  
- **Melakukan Penggabungan Data**

  Menggabungkan data buku dan *rating* menjadi satu bagian sehingga data akan lebih mudah digunakan untuk pelatihan oleh model *machine learning* nantinya.

- **Menghapus Data Duplikasi**

  Penghapusan duplikasi data yang dilakukan pada proyek ini yaitu penghapusan data berdasarkan judul buku yang sama namun memiliki ISBN yang berbeda. Sehingga 1 judul buku hanya akan memiliki 1 ISBN. Dengan begitu model dapat lebih baik dalam memberikan hasil rekomendasi.
  
- **Menangani *Missing Value* Pada Data**

  Salah satu cara menangani *missing value* yang umum dan sering digunakan adalah melakukan drop pada baris yang memiliki nilai kosong. Dengan begitu data baris yang memiliki nilai kosong akan terhapus, sehingga menjadikan performa dari model *machine learning* menjadi lebih baik lagi.
  
- **Melakukan Normalisasi**

  Melakukan transformasi pada data yang akan dipelajari oleh model dengan menggunakan library *MinMaxScaler* ataupun *StandardScaler*. Pada proyek kali ini data yang akan di normalisasi adalah data *rating* dengan menggunakan library *MinMaxScaler*. *MinMaxScaler* mentransformasikan fitur dengan menskalakan setiap fitur ke rentang tertentu. Library ini menskalakan dan mentransformasikan setiap fitur secara individual sehingga berada dalam rentang yang diberikan pada set pelatihan, pada library ini memiliki range default antara 0 dan 1. Dengan merenapkan teknik normalisasi data, model akan dengan lebih mudah mengenali pola-pola yang terdapat pada data sehingga akan menghasilkan prediksi yang lebih baik daripada tidak menggunakan teknik normalisasi.

- **Melakukan *Split Dataset***

  Membagi *dataset* menjadi data latih **(x_*train* & y_*train*)** dan data uji **(x_*test* & y_*test*)** sebelum membuat model. Data latih adalah sekumpulan data yang akan digunakan oleh model *machine learning* untuk melakukan pelatihan. Sedangkan data uji adalah sekumpulan data yang akan digunakan untuk memvalidasi kinerja pada model *machine learning* yang telah dilatih. Karena data uji berperan sebagai data baru yang belum pernah dilihat oleh model *machine learning*, maka cara ini efektif untuk memeriksa performa model *machine learning* setelah proses pelatihan dilakukan. Proporsi pembagian *dataset* pada proyek ini menggunakan proporsi pembagian **90:10** yang berarti sebanyak **90% merupakan data latih** dan **10% persen merupakan data uji**, kemudian ***random_state** bernilai **32**.

# *Modeling and Result*
Model atau Algoritma yang digunakan pada proyek ini adalah sebagai berikut: 

- ***Collaborative Filtering* (*CF*)**

  Pada teknik ini proses pembuatan rekomendasi menggunakan model *Deep Learning*. Langkah yang pertama yaitu dengan menggabungkan data buku dan *rating*. Setelah itu melakukan penyandian terhadap data *User-ID* dan *ISBN* dan memisahkan data latih dan data validasi dengan *ratio* 90:10. Kemudian membuat model untuk melakukan pelatihan pada data. Model ini menggunakan operasi perkalian *dot product* antara *embedding user* dan *book*. Skor kecocokan ditetapkan dalam skala [0,1] dengan fungsi aktivasi *sigmoid*. Untuk mendapatkan hasil rekomendasi, dipilih *User-ID* secara acak dan akan dilakukan penyaringan daftar buku yang belum pernah dibaca oleh user. Pastinya teknik ini memiliki kelebihan dan kekurangannya sendiri, yaitu sebagai berikut:

  Kelebihan:
  - Tidak memerlukan atribut untuk setiap itemnya.
  - Dapat membuat rekomendasi tanpa harus selalu menggunakan *dataset* yang lengkap.
  - Unggul dari segi kecepatan dan skalabilitas.
  - Rekomendasi tetap akan berkerja dalam keadaan dimana konten sulit dianalisi sekalipun.

  Kekurangan:
  - Membutuhkan parameter *rating*, sehingga jika ada item baru sistem tidak akan merekomendasikan item tersebut.

Setelah model dibuat dan dilatih, berikut adalah hasil rekomendasi dari model ***Collaborative Filtering* (*CF*)** :

**Tabel 1** Hasil Rekomendasi
<table>
    <thead>
        <tr>
            <th colspan=3>Menampilkan Rekomendasi Untuk Pengguna Dengan ID 230708</th>
        </tr>
    </thead>
  <thead>
        <tr>
            <th>Buku Dengan 5 Peringkat Tinggi Dari Pengguna</th>
            <th colspan=1>Rekomendasi 10 Buku Terbaik Kepada Pengguna</th>
        </tr>
    </thead>
    <tbody>
        <tr>
        	   <td>1. <a href="http://images.amazon.com/images/P/0440224721.01.THUMBZZZ.jpg"><i>Obstruction of Justice</i></a></td> 
            <td>1. <a href="http://images.amazon.com/images/P/0394800389.01.THUMBZZZ.jpg"><i>Fox in Socks</i></a></td>
        </tr>
        <tr>
        	   <td>2. <a href="http://images.amazon.com/images/P/0380818655.01.THUMBZZZ.jpg"><i>Another Summer</i></a></td>
            <td>2. <a href="http://images.amazon.com/images/P/096265342X.01.THUMBZZZ.jpg"><i>Principia Discordia</i></a></td>
        </tr>
        <tr>
            <td>3. <a href="http://images.amazon.com/images/P/0821771078.01.THUMBZZZ.jpg"><i>An Outlaw for Christmas (Zebra Historical Romance)</i></a></td>
            <td>3. <a href="http://images.amazon.com/images/P/0760707251.01.THUMBZZZ.jpg"><i>Charlottes Web Special Read Along Edition</i></a></td>
        </tr>
        <tr>
            <td>4. <a href="http://images.amazon.com/images/P/0553578138.01.THUMBZZZ.jpg"><i>A Place to Call Home</i></a></td>
            <td>4. <a href="http://images.amazon.com/images/P/1578591201.01.THUMBZZZ.jpg"><i>VideoHound's Golden Movie Retriever 2001</i></a></td>
        </tr>
        <tr>
            <td>5. <a href="http://images.amazon.com/images/P/044022361X.01.THUMBZZZ.jpg"><i>Wild Dream</i></a></td>
            <td>5. <a href="http://images.amazon.com/images/P/0689801505.01.THUMBZZZ.jpg"><i>Chimps Don't Wear Glasses</i></a></td>
        </tr>
        <tr>
            <td></td>
            <td>6. <a href="http://images.amazon.com/images/P/0316286850.01.THUMBZZZ.jpg"><i>Making Faces</i></a></td>
        </tr>
        <tr>
            <td></td>
            <td>7. <a href="http://images.amazon.com/images/P/0091842050.01.THUMBZZZ.jpg"><i>The Blue Day Book: A Lesson in Cheering Yourself Up</i></a></td>
        </tr>
        <tr>
            <td></td>
            <td>8. <a href="http://images.amazon.com/images/P/0060280034.01.THUMBZZZ.jpg"><i>Dinotopia: A Land Apart from Time (Dinotopia)</i></a></td>
        </tr>
        <tr>
            <td></td>
            <td>9. <a href="http://images.amazon.com/images/P/2020551470.01.THUMBZZZ.jpg"><i>Le baron perche</i></a></td>
        </tr>
        <tr>
            <td></td>
            <td>10. <a href="http://images.amazon.com/images/P/0393048470.01.THUMBZZZ.jpg"><i>The Annotated Alice: The Definitive Edition</i></a></td>
        </tr>
    </tbody>
</table>

Dapat dilihat bahwa rekomendasi buku yang dihasilkan relevan dan sesuai dengan preferensi dari pengguna berdasarkan *rating* yang diberikan

# *Evaluation*
Evaluasi untuk proyek *machine learning* pada model ***Collaborative Filtering* (*CF*)** ini akan menggunakan metrik ***Root Mean Squared Error* (*RMSE*)**, Cara Menghitung metrik ini adalah dengan mengurangi nilai aktual dengan nilai peramalan kemudian dikuadratkan dan dijumlahkan keseluruhan hasilnya kemudian dibagi dengan banyaknya data. Hasil perhitungan tersebut selanjutnya dihitung kembali untuk mencari nilai dari akar kuadrat. Semakin rendah nilai ***Root Mean Squared Error* (*RMSE*)** juga menandakan semakin baik model *machine learning* tersebut dalam melakukan prediksi sehingga kemudian dapat memberikan rekomendasi terbaik kepada pengguna.

  $$ RMSE = { \sqrt\frac{\displaystyle \sum_{t=1}^n (A_t-F_t)^2} {n} } $$
  
Dimana : 
* $A_t$ = Nilai Data Aktual
* $F_t$ = Nilai Hasil Peramalan
* $n$ = Banyaknya Data
* $\sum$ = Summation (Jumlah Keseluruhan Nilai)

Setelah melakukan evaluasi menggunakan metrik *mean squared error* pada model dengan menggunakan data uji didapatkan hasil nilai *RMSE* pada ***Collaborative Filtering* (*CF*)** sebagai berikut:

<img src="https://user-images.githubusercontent.com/77198942/205901043-211bb6cf-ad17-42a1-9617-d4e791a90c37.png" style="background-color:#FFFF" width="500"/>

Dari hasil pelatihan yang dilakukan. Dapat dilihat bahwa nilai metrik *RMSE* berada di sekitar 0.38 untuk *training* dan disekitar 0.36 untuk validasi.

# *Conclusion*
Kesimpulan dari beberapa pembahasan diatas berdasarkan proyek yang sudah dijalankan, dapat diketahui bahwa model ***Collaborative Filtering* (*CF*)** proyek ini menghasilkan rekomendasi buku yang relevan dan sesuai dengan preferensi dari pengguna berdasarkan *rating* yang diberikan.

# *References*
1. Irfan, M., C, A. D., & Fika Hastarita R. (2014). SISTEM REKOMENDASI : BUKU ONLINE DENGAN METODE COLLABORATIVE FILTERING. JURNAL TEKNOLOGI TECHNOSCIENTIA, 7(1).
2. Miraldi, R. N., Christanto, A. R., & Susanto, B. (2015). IMPLEMENTASI ALGORITMA FP-GROWTH UNTUK SISTEM REKOMENDASI BUKU DI PERPUSTAKAAN UKDW. Jurnal Informatika, 10(1). https://doi.org/10.21460/inf.2014.101.323
3. Fathurrahman, M. I., Nurjanah, D., & Rismala, R. (2017). Sistem Rekomendasi Pada Buku Dengan Menggunakan Metode Trust-Aware Recommendation. E-Proceeding of Engineering | ISSN : 2355-9365, 4(3).
4. Alkaff, M., Khatimi, H., & Eriadi, A. (2020). Sistem Rekomendasi Buku Menggunakan Weighted Tree Similarity dan Content Based Filtering. MATRIK : Jurnal Manajemen, Teknik Informatika Dan Rekayasa Komputer, 20(1).
