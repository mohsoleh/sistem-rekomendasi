# Laporan Proyek Machine Learning - Moh. Saleh
![](https://www.vanas.ca/images/blog/vfx-visual-effects-vanas.jpg)

## Project Overview
Dalam era digital saat ini, informasi sangat mudah diakses dan ketersediaannya hampir tidak terbatas. Informasi menjadi kebutuhan utama dalam bisnis yang berkembang pesat saat ini, di mana terdapat ketergantungan yang meningkat pada penggalian data untuk mendukung solusi bisnis. Berbagai perusahaan memanfaatkan informasi ini guna memahami preferensi pelanggan dan meningkatkan pengalaman pengguna. Hal ini mendorong munculnya sistem rekomendasi, yang memainkan peranan penting di berbagai bidang.

Sistem rekomendasi telah menjadi komponen esensial dalam platform digital [(Hasibuan, 2021)](https://ejournal.unesa.ac.id/index.php/JDKV/article/view/41064), terutama di industri hiburan seperti streaming film, musik, dan layanan konten lainnya. Sistem ini bekerja dengan memprediksi preferensi pengguna terhadap item tertentu berdasarkan perilaku pengguna di masa lalu atau perilaku pengguna lainnya, lalu memberikan saran berdasarkan preferensi tersebut [(Angga,  2022)](https://ejurnal.ars.ac.id/index.php/jdcode/article/view/864). Contoh penerapan sistem ini dapat ditemukan pada platform seperti Netflix, YouTube, dan Spotify.

Dengan banyaknya konten dan pilihan genre film yang tersedia, platform penyedia layanan perlu memberikan item-item yang relevan sesuai dengan minat pelanggannya guna mempertahankan pelanggan. Sistem rekomendasi merupakan alternatif yang solutif untuk memberikan rekomendasi film yang sesuai dengan minat pengguna. Oleh karena itu, proyek machine learning ini bertujuan untuk mengembangkan model machine learning yang digunakan untuk sistem rekomendasi film dengan mempertimbangkan rating film di masa lalu yang diberikan oleh berbagai pengguna untuk memberikan rekomendasi kepada pengguna.

Proyek ini akan menggunakan metode Content-Based Filtering dan Collaborative Filtering. Pada pendekatan Content-Based Filtering, atribut-atribut film seperti judul dan genre digunakan untuk menemukan pola kesamaan antarfilm [(H. D. Putri & Faisal, 2023)](https://doi.org/10.31603/komtika.v7i2.9219). Ketika pengguna menunjukkan minat pada film tertentu, sistem akan menyarankan film lain dengan atribut yang serupa. Sementara itu, pendekatan Collaborative Filtering memanfaatkan data interaksi pengguna seperti rating film untuk mengidentifikasi preferensi berdasarkan pola perilaku pengguna lain yang serupa [(Guo, J., Deng, J., Ran, X., Wang, Y., & Jin, H. (2021))](https://doi.org/10.1016/j.eswa.2020.113756).

Hasil yang diharapkan dari proyek ini adalah terciptanya sistem rekomendasi yang efektif dalam memberikan saran film yang relevan, meningkatkan kepuasan pengguna, serta mendorong eksplorasi terhadap film-film dari berbagai genre, termasuk yang mungkin belum dikenal secara luas. Sistem ini juga diharapkan mampu memberikan rekomendasi yang akurat bahkan untuk pengguna baru yang memiliki riwayat interaksi yang terbatas.
## Business Understanding
Pada bagian ini, Anda perlu menjelaskan proses klarifikasi masalah. yang meliputi :

### Problem Statements
Berdasarkan latar belakang yang telah dipaparkan, Problem Statements dalam proyek ini dapat dirumuskan sebagai berikut:
1. Bagaimana merancang dan mengembangkan sistem rekomendasi film yang mampu menyesuaikan dengan preferensi, minat, atau perilaku pengguna?
2. Bagaimana mengukur kinerja dan mengevaluasi model yang digunakan dalam sistem rekomendasi untuk memastikan akurasi dalam memenuhi preferensi, minat, atau perilaku pengguna?

### Goals
Berdasarkan rumusan masalah yang telah dipaparkan, proyek ini bertujuan untuk:
1. Mengembangkan sistem rekomendasi film yang dapat menyesuaikan dengan preferensi, minat, atau perilaku pengguna.
2. Mengevaluasi hasil dan kinerja model yang digunakan dalam sistem rekomendasi untuk memastikan kemampuan model dalam memberikan rekomendasi yang relevan dan akurat sesuai dengan kebutuhan pengguna.

### Solution statements
Berdasarkan tujuan yang telah dipaparkan, proyek penelitian ini dirancang dengan tahapan solusi sebagai berikut:
1. Melakukan data preprocessing dan exploratory data analysis (EDA) pada dataset untuk menganalisis keterkaitan antar fitur, mendapatkan insight, serta memahami karakteristik data secara menyeluruh.
2. Mengembangkan model machine learning yang sesuai untuk membangun sistem rekomendasi, sekaligus mengevaluasi performa model menggunakan metrik evaluasi yang relevan. Teknik yang akan diterapkan meliputi:
   - Content-Based Filtering: Memberikan rekomendasi item berdasarkan kemiripan antara item yang direkomendasikan dengan item yang sudah dipilih oleh pengguna.
   - Collaborative Filtering: Menghasilkan rekomendasi berdasarkan preferensi dan pola kesamaan dari komunitas atau pengguna lain.
3. Melakukan evaluasi sistem rekomendasi berdasarkan metrik evaluasi yang telah ditentukan untuk menilai relevansi, akurasi, dan efektivitas model yang dikembangkan.

## Data Understanding
Proyek ini memanfaatkan dataset MovieLens, yang merupakan dataset yang banyak digunakan di bidang sistem rekomendasi, berisi penilaian dan metadata film. Dataset ini yang saya gunakan adalah dataset dari kaggle yang memiliki 2 file movies.csv dan ratings.csv, sedangkan data aslinya dari MovieLens berformat zip yang memiliki 7 file terpisah diantaranya movies.csv, ratings.csv, genome-scores.csv, links.csv, tags.csv, genome-tags.csv, dan README.txt. Berdasarkan README.txt yang telah disediakan, dataset ini dibuat pada 21 November 2019 oleh 162.541 pengguna yang dikumpulkan dalam kurun waktu film rilis pada 09 Januari 1995 hingga 21 November 2019.

### Variabel-variabel pada dataset:
Pada file `movies.csv` berisi daftar film yang memiliki 62.423 records data dan 3 feature:
- `movieId` : memuat nomor ID film  
- `title` : memuat judul film
- `genres` : memuat genre film

Pada file `ratings.csv` berisi daftar ratings atau penilaian terhadap satu film yang memiliki 25.000.095 records data dan 4 feature:
- `userId` : memuat nomor ID users
- `movieId` : memuat nomor ID film  
- `rating` : memuat rating atau penilaian films dalam skala bintang, dengan peningkatan setengah bintang dalam rentang 0,5 - 5 bintang
- `timestamp` : memuat kode timestamp

## Exploratory Data Analysis (EDA)
Proses Exploratory Data Analysis (EDA) dilakukan dengan menganalisis dataset secara menyeluruh untuk memperoleh pemahaman mendalam mengenai struktur data, pola, dan hubungan antar fitur. Tujuan utama dari proses ini adalah mengidentifikasi wawasan (insight) dan pengetahuan (knowledge) yang dapat mendukung pengembangan sistem rekomendasi.

### Univariate Analysis
Berdasarkan informasi sebelumnya, mari kita lihat lebih detail informasi terkait movies dan rating, menggunakan function `info` :

![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/eda-movies-info.png?raw=true)
Dataset ini terdiri dari 62.423 baris dengan 3 kolom utama, yaitu movieId, title, dan genres. Selanjutnya mari kita lihat informasi genre menggunakan perintah berikut :
![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/eda-genre-len.png?raw=true)
Dataset mencakup 1.639 kombinasi genre unik, dengan beberapa tipe genre seperti Adventure|Animation|Children|Comedy|Fantasy, Comedy|Romance, dan kombinasi lainnya yang mencakup horor, misteri, hingga fiksi ilmiah, menunjukkan keragaman genre dalam dataset. selanjutnya kita lihat informasi dataset ratings.
![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/eda-ratings-info.png?raw=true)
Dataset ini memiliki ukuran data yang sangat besar yakni 762.9 MB, dan memiliki 4 kolom diantaranya adalah userId, movieId, rating dan timestamp. Selanjutnya mari kita lihat informasi dari rating lebih detail lagi, menggunakan perintah berikut:
![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/eda-ratings-describe.png?raw=true)
Dari data di ratings memiliki rata-rata rating sebesar 3.53. Sebagian besar rating berkisar antara 3.0 sampai 4.0, yang mencerminkan bahwa mayoritas film mendapatkan penilaian yang cukup baik. Rating terendah adalah 0.5, sementara yang tertinggi mencapai 5.0.

## Data Preprocessing
Dari sudut pandang proses data preparation, langkah pertama yang saya lakukan adalah data cleaning pada dataset movies.csv dan ratings.csv. Setelah memastikan kedua dataset tersebut telah bersih dan siap digunakan, saya melakukan merging kedua dataframe tersebut untuk membentuk satu dataframe yang utuh. Dataframe hasil penggabungan ini kemudian digunakan sebagai dasar untuk mengembangkan sistem rekomendasi. Berikut adalah tahapan yang dilakukan:

### Data Cleaning `movies.csv`
Pada data `movies.csv`, terdapat tahun rilis dari film yang disertakan secara bersamaan pada feature judul film. Hal ini diperlukan penanganan khusus untuk memisahkan antara judul film dengan tahun rilis agar tidak terjadi permasalahan yang tidak diinginkan pada proses training model. dimana, tahun rilis dari setiap film akan dipisahkan ke dalam kolom tersendiri. dapat dilihat pada gambar berikut ini:
![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/preprocessing-separate-titles-and-year.png?raw=true)
Kode pada gambar di atas, memisah tahun rilis dan title dengan menambahkan satu kolom year_of_release. sekarang kita hapus tahun rilis pada title menggunakan kode berikut :
![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/preprocessing-remove-year-from-title.png?raw=true)
Dari gambar di atas, data telah tertata dengan baik setelah memisahkan informasi tahun rilis dari title dan menambahkan kolom baru bernama year_of_release.

### Data Cleaning `ratings.csv`
Pada data `ratings.csv`, skala rating pada feature rating memiliki sebaran yang tidak normal. dimana terdapat data dalam bentuk kode timestamp. Akan susah untuk dipahami, kapan data tersebut diambil secara spesifik. maka, proses konversi dilakukan untuk mengubah timestamps menjadi data datetime.
![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/preprocessing-convert-datetime.png?raw=true)
Gambar di atas, hasil dari konversi timestamps menjadi data datetime, sehingga mempermudah dipahami.

### Data Merging `movies` dengan `ratings`
Penggabungan dilakukan dengan melakukan merge pada kedua dataframe antara `movies` dengan `ratings` menjadi satu dataframe yang utuh dan mengassignnya kedalam variabel `films`.
![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/preprocessing-marge-dataframe.png?raw=true)
Gambar di atas menunjukkan hasil penggabungan data yang menghasilkan total sebanyak 25.003.471 entri. Jumlah ini berasal dari penggabungan data sebelumnya, yaitu 62.423 entri pada dataset movies dan 25.000.095 entri pada dataset ratings. Dataset hasil penggabungan ini terdiri dari 7 kolom.

## Data Preparation
Ada beberapa handling yang dilakukan pada dataframe `films`, diantaranya sebagai berikut.

### Handling Missing Values
Data yang hilang, null, NaN atau tidak terbaca merupakan hal umum yang seringkali ditemui. Agar data yang missing tidak memengaruhi kinerja model yang akan dikembangkan, maka saya akan menghapusnya.
![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/preparation-films-isnull.png?raw=true)
Gambar di atas terdapat banyak missing value pada sebagian besar fitur. Hanya fitur movieId, title, ganres saja yang memiliki 0 missing value. sehingga perlu kita drop data tersebut menggunakan perintah `films = films.dropna()`.

### Handling `No Genres Listed`
Pada proyek ini, saya menemukan missing values pada beberapa feature, salah satunya adalah genre dimana terdapat data '(no genres listed)'. sehingga kita perlu menghapus data yang tidak memiliki genre, menggunakan kode berikut :
![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/preparation-clean-no-genre.png?raw=true)
Dari data 24.988.552 sebelumnya, sekarang data menjadi 24.964.826 yang tandanya semua movie yang tidak memiliki genre sudah berhasil dihapus.

### Handling Scala Ratings
Skala rating pada feature rating memiliki sebaran yang tidak normal. dimana data rating memiliki skala 0.5 sampai 5 dengan perbedaan 0.5 setiap skalanya. handling yang dilakukan untuk pada case ini adalah dengan membulatkan nilai skala pada feature rating agar distribusi skala memiliki rentang 1-5.
![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/preparation-round-ratings.png?raw=true)
Kode di atas digunakan untuk membulatkan nilai pada kolom rating dalam dataframe bernama films menggunakan fungsi np.ceil dari library NumPy. 

### Handling Duplicate Data
Dataset yang berantakan dan terduplikasi dapat mempengaruhi hasil modeling dan analisis akhir. Pada proyek ini, terdapat banyak duplikasi data didalamnya berdasarkan id film dan judul film. Menghapusnya merupakan langkah yang tepat untuk merapikan data. pada proyek ini menggunakan kode berikut ini:
![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/preparation-drop-duplicate-data.png?raw=true)

### Fixed data in genre features
Pada features genre, saya mendapati genre ***Sci-Fi***. setelah saya pahami, ternyata ***Sci-Fi*** merupakan akronim dari kata ***Science Fiction*** yang menggambarkan film fiksi ilmiah. kata ***Sci-Fi*** memiliki separator dash atau tanda pisah. Hal ini, perlu dihilangkan. apabila tidak dihilangkan maka pada tahap vektorisasi TF-IDF nantinya kata ***Sci-Fi*** akan diperlakukan sebagai 2 kata yang berbeda ***Sci*** dan ***Fi***. karena, pada tahap TF-IDF selain melakukan vektorisasi juga dilakukan tokenisasi. proses mengganti kata ***Sci-Fi*** dapat dilihat di kode berikut:
![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/preparation-replace-sci-fi-to-scifi.png?raw=true)

### Membuat Variable preparation
Sebelum diproses oleh Model, ayo kita buat variabel preparation yang berisi dataframe films kemudian mengurutkan berdasarkan movieId 
![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/preparation-order-by-movie_id.png?raw=true)
Gambar di atas menunjukkan hasil preparation, data yang akan proses pada model sebanyak 50.607 entri dan terdiri dari 7 kolom. Selanjutnya, kita perlu melakukan konversi data series menjadi list. Dalam hal ini, kita menggunakan fungsi tolist() dari library numpy. Implementasikan kode berikut.
![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/preparation-convert-to-list.png?raw=true)
Kode ini mengonversi kolom movieId, title, dan genres dari dataset preparation ke dalam bentuk daftar Python menggunakan metode .tolist(). Variabel film_id, film_name, dan film_genre masing-masing menyimpan data ID film, judul film, dan genre film dalam format list. Ketiga kolom di atas memiliki jumlah data yang sama yakni 50.607. Tahap berikutnya, kita akan membuat dictionary untuk menentukan pasangan key-value pada data film_id, film_name, dan genre yang telah kita siapkan sebelumnya.

Tahap berikutnya, kita akan membuat dictionary untuk menentukan pasangan key-value pada data film_id, film_name, dan genre yang telah kita siapkan sebelumnya.
![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/preparation-create-dataframe.png?raw=true)

Sampai tahap ini, data telah siap untuk dimasukkan ke dalam pemodelan.

## Modeling
Pada proyek ini, pendekatan yang dipakai untuk mengembangkan model dalam sistem rekomendasi adalah `Content-Based Filtering` dan `Collaborative Filtering`.

### Content-Based Filtering
Konsep dasar dari content-based filtering adalah memberikan rekomendasi item dengan memperhatikan kemiripan dari item yang disukai oleh pengguna berdasarkan aktivitas pengguna tersebut di masa lalu. Ambil contoh, mawan menyukai film disney Coco. maka, sistem akan merekomendasikan film dengan genre animation yang mirip seperti Encanto. Pada akhirnya, semakin banyak informasi yang didapatkan dari aktivitas pengguna, semakin baik pula akurasi dari sistem rekomendasi yang dihasilkan.

![](https://dicoding-web-img.sgp1.cdn.digitaloceanspaces.com/original/academy/dos:46ce6a2a9d4d38560021dba74dcba60420210910164924.jpeg)
Sumber : dicoding.com

Pada proyek ini, saya akan menggunakan pendekatan content-based filtering untuk mengembangkan model sistem rekomendasi film sesuai dengan tujuan yang telah ditetapkan. Berikut adalah beberapa tahapan yang saya lakukan:

### TF-IDF Vectorizer
Proses term frequency-inverse document frequency (TF-IDF) diperlukan untuk menemukan representasi kata yang penting dalam kolom genre. Pada proyek ini, proses vectorizer dilakukan dengan memanfaatkan function [tfidfvectorizer()](https://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.TfidfVectorizer.html) yang telah tersedia pada library scikit-learn. berikut hasil tf-idf dalam bentuk matrix. yang mana pada matrix menunjukkan korelasi antara film dengan genre-nya.
![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/model-create-sparse.png?raw=true)

Kode ini membuat Sparse DataFrame dari matriks TF-IDF (tfidf_matrix) untuk menghubungkan film dengan genre secara efisien, menggunakan nama film sebagai indeks dan genre sebagai kolom. Selanjutnya, dilakukan sampling untuk memilih 10 baris (film) dan 20 kolom (genre) secara acak, menghasilkan subset kecil data yang siap untuk dianalisis lebih lanjut.

Output gambar tersebut merupakan hasil representasi data dalam bentuk matriks TF-IDF yang diubah menjadi Sparse DataFrame. Matriks ini merepresentasikan hubungan antara film dan genre berdasarkan skor TF-IDF (Term Frequency-Inverse Document Frequency), di mana skor menunjukkan relevansi sebuah genre terhadap suatu film. Baris pada matriks merepresentasikan nama film, seperti Murder, My Sweet, Andrei Rublev, dan The Suicide Theory, sementara kolom menunjukkan berbagai genre yang tersedia, seperti `action`, `drama`, `thriller`, dan sebagainya. Setiap nilai dalam matriks menunjukkan skor TF-IDF, misalnya film _Andrei Rublev_ memiliki skor 0.380178 untuk genre `drama` dan 0.924913 untuk genre `noir`, yang menunjukkan relevansi genre tersebut dengan film. Data yang ditampilkan merupakan hasil sampling, di mana 10 baris film dan 20 kolom genre dipilih secara acak. Sparse DataFrame digunakan untuk menghemat memori karena sebagian besar nilai dalam matriks adalah nol, menunjukkan bahwa genre tersebut tidak relevan untuk film terkait. Matriks ini menjadi dasar dalam pendekatan _content-based filtering_ untuk menghitung kemiripan antar film berdasarkan genre.

### Perhitungan Cosine Similarity
Cosine similarity digunakan untuk menghitung derajat kesamaan (similarity degree) antar film. Pada proyek ini, kalkulasi similarity dilakukan dengan mengimplementasikan function [cosine_similarity()](http://scikit-learn.org/stable/modules/generated/sklearn.metrics.pairwise.cosine_similarity.html) yang telah tersedia pada library sklearn. Perhitungan similarity merupakan tahapan paling penting dalam pendekatan content-based filtering, karena pada dasarnya pendekatan ini menerapkan prinsip kesamaan antar item untuk mendapatkan hasil rekomendasi yang sesuai. Output dari cosine similarity akan menghasilkan suatu matrix kesamaan yang bisa dilihat pada konversi ke bentuk dataframe berikut. 
![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/model-consin-sim-to-dense.png?raw=true)

Kode ini mengonversi matriks cosine similarity dari bentuk sparse ke bentuk dense menggunakan toarray(), sehingga dapat diproses lebih lanjut. Selanjutnya, matriks dense ini digunakan untuk membuat sebuah DataFrame bernama cosine_sim_df, di mana indeks dan kolomnya adalah nama-nama film dari data['film_name'].

Dengan cosine_sim_df.shape, ukuran matriks ditampilkan sebagai (50607, 50607), menunjukkan bahwa ada 50.607 film dengan nilai kesamaan antarfilm. sample(5, axis=1).sample(10, axis=0) menampilkan subset kecil dari matriks kesamaan untuk pengamatan.

Pada sampel data yang diambil, terlihat beberapa pasangan film dengan skor cosine similarity, misalnya:

- Film Populaire memiliki skor 0.404632 dengan film Volga - Volga, menunjukkan adanya kemiripan sedang di antara keduanya.
- Film Stricken memiliki skor 0.719576 dengan film Revance, menunjukkan tingkat kemiripan yang tinggi.
- Sebagian besar skor lainnya bernilai 0, yang berarti tidak ada kesamaan atau kesamaan sangat rendah antara film tersebut.

Data ini penting untuk sistem rekomendasi berbasis konten (content-based filtering), di mana matriks cosine similarity dapat digunakan untuk merekomendasikan film yang memiliki tingkat kesamaan tertinggi dengan film tertentu.

### Create Custom Functions
Tahapan terakhir adalah membangun custom function untuk mendapatkan rekomendasi terhadap data input yang diinginkan. functions ini bekerja dengan mengambil similarity dari data film yang ingin dicari, data yang similar akan dimasukkan ke dalam variabel closest. parameter K di define untuk menghasilkan top-K recommendation berdasarkan tingkat similarity tertinggi. film yang dicari akan dihapus agar tidak muncul dalam daftar rekomendasi. Step terakhir, return digunakan untuk mengembalikan values dalam bentuk dataframe, dimana values yang di return merupakan rekomendasi dari judul film berdasarkan tingkat similarity.
![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/model-function-recomendation.png?raw=true)

### Recommendations
Berikut ini merupakan Top 5 Recommendations berdasarkan genre dari film '***Toy Story***'. Sistem telah berhasil merekomendasikan film dengan sesuai, bisa dilihat pada hasil yang mendapatkan rekomendasi film yang mirip dengan genre Adventure dan Fantasy. 

![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/model-get-recomendation.png?raw=true)

**Kelebihan Content-Based Filtering**
- Mampu menjelaskan bagaimana hasil rekomendasi didapatkan
- Kemampuan untuk merekomendasikan item yang sifatnya baru bagi pengguna bahkan belum pernah di-rate oleh siapapun, karena prinsip kerjanya yaitu dengan melihat deskripsi item yang terdapat pada item yang pernah diberi nilai rating tinggi

**Kekurangan Content-Based Filtering**
- Terbatasnya rekomendasi hanya pada item-item yang mirip (similar) sehingga tidak ada kesempatan untuk mendapatkan item yang tidak terduga (serendipity)
- Sistem tidak dapat memberikan rekomendasi kepada pengguna baru yang belum pernah melakukan aktivitas apapun dan tidak memiliki profil user yang cukup (Cold Start Problem)

### Collaborative Filtering
Sebelumnya kita telah menerapkan teknik content based filtering pada data. Teknik ini merekomendasikan item yang mirip dengan preferensi pengguna di masa lalu. Berikutnya, kita akan menerapkan teknik collaborative filtering untuk membuat sistem rekomendasi. Teknik ini membutuhkan data rating dari user. berikut merupakan tahapan dalam Collaborative Filtering

### Data Understanding
Pada tahap awal, diperlukan beberapa library salah satunya adalah tensorflow dan dataframe yang dipakai adalah dataframe 'preparation' yang sebelumnya telah digunakan.

### Data Preparation
Proses encoding dilakukan pada tahap ini, dengan melakukan encode pada feature 'userId' dan 'movieId'. proses encode akan memetakan setiap nilai pada kedua feature tersebut ke dalam bentuk index.
![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/model-encode-user-id.png?raw=true)

Kode ini melakukan encoding pada kolom userId dalam dataset. Pertama, nilai unik dari userId diubah menjadi daftar menggunakan .unique().tolist(). Kemudian, setiap userId di-encode menjadi indeks numerik menggunakan dictionary user_to_user_encoded. Sebaliknya, dictionary user_encoded_to_user memetakan indeks numerik kembali ke userId asli. Ini memungkinkan representasi userId dalam bentuk numerik yang lebih mudah digunakan dalam model dan analisis.

![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/model-encode-movie-id.png?raw=true)

Kode di atas melakukan encoding pada kolom movieId dalam dataset. Pertama, nilai unik dari movieId diubah menjadi daftar menggunakan .unique().tolist(). Kemudian, setiap movieId dipetakan ke indeks numerik melalui dictionary films_to_films_encoded. Sebaliknya, dictionary films_encoded_to_films memungkinkan pemetaan indeks numerik kembali ke movieId asli. Proses ini memungkinkan representasi movieId dalam bentuk numerik yang lebih mudah untuk digunakan dalam analisis atau model pembelajaran mesin. Berikutnya, petakan userID dan movieID ke dataframe yang berkaitan. Terakhir, cek beberapa hal dalam data seperti jumlah user, jumlah film, dan mengubah nilai rating menjadi float.

![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/model-get-informations-dataset.png?raw=true)

Tahap persiapan ini penting dilakukan agar data siap digunakan untuk pemodelan. Namun sebelumnya, kita perlu membagi data untuk training dan validasi terlebih dahulu.

### Split Data for Training and Validation
Data dibagi untuk data train dan validasi dengan komposisi 80/20. Pembagian ini bertujuan agar data yang digunakan dapat digunakan untuk mengembangkan model dan mengevaluasi performance dari model yang telah dikembangkan.
![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/model-split-data-train.png?raw=true)

### Training
Proses training dilakukan dengan mengimplementasikan teknik embedding untuk menghitung skor kecocokan antara film dengan users. kemudian, pada  proses compile dilakukan menggunakan BinaryCrossentropy untuk menghitung loss function, Adam (Adaptive Moment Estimation) sebagai optimizer, dan root mean squared error (RMSE) sebagai metrics evaluation. Proses training model berjalan sebanyak 25 epochs sebagai berikut.
![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/model-output-training.png?raw=true)

### Metrics Visualization
Berdasarkan hasil log pelatihan, terlihat bahwa nilai root_mean_squared_error (RMSE) untuk data pelatihan terus menurun secara konsisten dari 0.2790 (epoch 1) menjadi 0.1353 (epoch 25). Hal ini menunjukkan bahwa model berhasil mempelajari pola pada data pelatihan dengan baik. Untuk data validasi, nilai RMSE juga mengalami penurunan, meskipun cenderung melambat setelah beberapa epoch awal dan stabil di sekitar nilai 0.2371 pada epoch terakhir.

![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/model-plot-training.png?raw=true)

### Recommendations
Kemudian menggunakan model.predict(), sistem akan memberikan rekomendasi sebagai berikut.

![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/model-ouput-get-recomendation-by-user.png?raw=true)

Horee, sudah berhasil memberikan rekomendasi kepada user. Hasil di atas adalah rekomendasi untuk user dengan id 3. Dari output tersebut, kita dapat membandingkan antara `films with high ratings from user` dan `Top 10 films recommendation untuk user.`

## Evaluation
Evaluasi dilakukan untuk mengukur sejauh mana performance atau kinerja dari model sistem rekomendasi. Pada proyek ini, evaluasi diukur menggunakan metriks evaluasi sesuai dengan pendekatan yang dipakai dalam pengembangan sistem rekomendasi.

### Content-Based Filtering
Pada pendekatan Content-Based Filtering, performance model diukur menggunakan nilai metriks precisions dengan similarity. Cosinus Similarity merupakan ukuran yang mengkuantifikasi kesamaan antara dua atau lebih vektor. 

![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/cosine-sim-formula.png?raw=true)

Nilai cosinus similarity memiliki rentang yang terbatas antara 0 dan 1. ukuran kemiripan ditentukan oleh ukuran cosinus sudut antara dua vektor tak nol. Semakin besar nilai cosinus similarity semakin mendekati 1, maka sudut antara kedua vektor juga semakin kecil.

Precision merupakan tingkat ketepatan antara informasi yang diminta oleh pengguna dengan hasil yang diberikan oleh sistem. Precision sangat cocok diterapkan sebagai metriks evaluasi pada sistem rekomendasi yang mana pengukuran kualitas akan ditentukan melalui seberapa bergunakah sistem dapat melakukan prediksi. 

![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/precision-table.png?raw=true)
Keterangan:
- **True Postive (TP):** prediksinya **Positif** dan hasil yang sebenarnya memang **Positif.**
- **False Positive (FP)**: prediksinya **Positif**, namun hasil yang sebenarnya adalah **Negatif.**
- **True Negative (TN):** prediksinya **Negatif** dan hasil yang sebenarnya memang **Negatif.**
- **False Negative (FN)**: prediksinya **Negatif**, namun hasil yang sebenarnya adalah **Positif.**

Formula diatas merupakan rumus precision. Namun, dalam sistem rekomendasi lebih sederhana menggunakan rumus seperti gambar dibawah ini. pada dasarnya sama saja, precisions membantu pengguna memilih item yang mirip di antara set item yang tersedia.

![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/precision-recommendations-formula.png?raw=true)

### Collaborative Filtering
Performance dari pendekatan Collaborative Filtering diukur menggunakan metriks evaluasi Root Mean Squared Error (RMSE). RMSE merupakan cara standar untuk mengukur rata-rata kesalahan suatu model dalam memprediksi. RMSE bekerja dengan cara mengurangi nilai prediksi dengan nilai observasi yang kemudian dikuadratkan. Hasilnya akan dijumlahkan (sigma jumlah) dengan keseluruhan hasil lainnya yang selanjutnya dibagi dengan banyaknya data (n). Hasil perhitungan yang didapatkan akan diakar kuadrat sehingga mendapatkan nilai RMSE sesuai dengan formula sebagai berikut.

![](https://raw.githubusercontent.com/mohsoleh/sistem-rekomendasi/refs/heads/main/img/rmse-formula.png)

Saat melakukan training model, RMSE sangat membantu untuk mengevaluasi dari model dengan melihat penurunan kesalahan pada setiap iterasi (epochs). Kemudian, hasil dari proses training model dapat divisualiasasikan ke dalam plot metrics sebagai berikut.

![](https://github.com/mohsoleh/sistem-rekomendasi/blob/main/img/model-plot-training.png?raw=true)

Berdasarkan plot metriks di atas, nilai RMSE didapatkan sebesar 0.13 dan pada data validasi sebesar 0.23 yang mana sistem yang telah dikembangkan sudah cukup baik.

## Conclusion
Disini, saya telah berhasil mengembangkan model sistem rekomendasi untuk film menggunakan dua teknik yang berbeda, yaitu Content-Based Filtering dan Collaborative Filtering. Hasil rekomendasi yang didapatkan cukup bagus. Metode collaborative filtering dapat memberikan hasil rekomendasi yang cukup sesuai. sedangkan metode content-based filtering juga dapat memberikan rekomendasi film yang similar dengan film yang memiliki kemiripan genre. Namun, ada yang perlu diperhatikan bahwa dataset yang digunakan memiliki data film dengan jumlah yang terbatas, bisa jadi pada dunia nyata model tidak memberikan rekomendasi sesuai yang diinginkan pengguna, dimana ada beberapa pengguna yang menyukai rekomendasi film-film terbaru. sedangkan model bisa saja merekomendasikan film-film keluaran lama.

## Referensi
1. Hasibiuan, R. Y. (2021). Desain Web Rekomendasi Musik Berdasarkan Pengelompokan. Barik, 2(2), 57–71. https://ejournal.unesa.ac.id/index.php/JDKV/article/view/41064
2. Angga, D. M. P. (2022). Analisis Isi Film “The Platform.” Journal  of  Digital  Communication  and  Design (JDCODE), 1(2), 127–136 https://ejurnal.ars.ac.id/index.php/jdcode/article/view/864
3. Putri, H. D., & Faisal, M. (2023). Analyzing the Effectiveness of Collaborative Filtering and Content-Based Filtering Methods in Anime Recommendation Systems. Jurnal Komtika (Komputasi Dan Informatika), 7(2), 124–133. https://doi.org/10.31603/komtika.v7i2.9219
4. Guo, J., Deng, J., Ran, X., Wang, Y., & Jin, H. (2021). An efficient and accurate recommendation strategy using degree classification criteria for item-based collaborative filtering. Expert Syst. Appl., 164, 113756. https://doi.org/10.1016/j.eswa.2020.113756
