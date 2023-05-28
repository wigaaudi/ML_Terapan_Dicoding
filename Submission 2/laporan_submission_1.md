# Laporan Proyek Machine Learning 2 (Sistem Rekomendasi Film) - Wiga Audi Prasetyo

## Project Overview

Dalam era digital saat ini, industri hiburan seperti perfilman menghadapi tantangan untuk menyajikan konten yang relevan dan menarik bagi pengguna. Dalam hal menonton film, terdapat banyak pilihan yang tersedia, dan seringkali pengguna merasa kesulitan dalam menemukan film-film yang sesuai dengan minat mereka. Oleh karena itu, pengembangan sistem rekomendasi film menjadi penting untuk membantu pengguna menemukan film-film yang menarik dan sesuai dengan preferensi mereka.

Sistem rekomendasi film menggunakan metode cosine similarity sangat relevan dalam konteks ini. Metode ini menganalisis kesamaan genre antara film-film yang ada dalam dataset dan memberikan rekomendasi berdasarkan film-film dengan genre serupa. Dengan memanfaatkan informasi genre, sistem rekomendasi dapat memperluas pengetahuan pengguna tentang film-film baru yang mungkin tidak mereka temui secara acak.

Dengan adanya sistem rekomendasi film yang akurat, pengguna dapat menemukan film-film yang sesuai dengan minat dan preferensi mereka dengan lebih mudah. Hal ini akan meningkatkan kepuasan pengguna dalam menikmati pengalaman menonton film.

## Business Understanding

### Problem Statements
Berdasarkan latar belakang yang sudah dibahas sebelumnya, maka problem statement untuk proyek ini adalah:
- Bagaimana cara membantu pengguna menemukan film-film yang sesuai dengan minat dan preferensi mereka?
- Bagaimana cara menyederhanakan proses pemilihan film bagi pengguna yang dihadapkan pada banyak pilihan?

### Goals

Berdasarkan problem statement sebelumnya, maka adapun goals yang ingin dicapai dalam proyek ini adalah:
- Mengembangkan sistem rekomendasi film yang akurat dan efektif untuk membantu pengguna - menemukan film-film yang sesuai dengan minat dan preferensi mereka.
- Menyediakan rekomendasi film yang relevan dan personal kepada pengguna untuk memudahkan mereka dalam memilih film yang ingin ditonton.

## Data Understanding
Dataset yang digunakan adalah "TMDB Movie Metadata". Dataset ini berisi informasi mengenai film-film seperti anggaran produksi, genre, halaman utama, ID, kata kunci, bahasa asli, judul asli, sinopsis, popularitas, perusahaan produksi, negara produksi, tanggal rilis, pendapatan, durasi film, bahasa yang digunakan, status produksi, tagline, judul film, rata-rata voting, dan jumlah voting yang dapat diunduh pada tautan berikut. (https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata)

Variabel atau fitur pada dataset TMDB Movie Metadata adalah sebagai berikut:

-budget: Anggaran produksi film (dalam bentuk bilangan bulat).
-genres: Genre atau jenis film (dalam bentuk objek).
-homepage: URL halaman utama film (misalnya, situs web resmi film).
-id: ID unik yang mengidentifikasi setiap film (dalam bentuk bilangan bulat).
-keywords: Kata kunci yang terkait dengan film (dalam bentuk objek).
-original_language: Bahasa asli film (dalam bentuk objek).
-original_title: Judul asli film (dalam bentuk objek).
-overview: Ringkasan atau sinopsis film (dalam bentuk objek).
-popularity: Indikator popularitas film (dalam bentuk bilangan desimal).
-production_companies: Perusahaan produksi yang terlibat dalam pembuatan film (dalam bentuk -objek).
-production_countries: Negara-negara tempat film diproduksi (dalam bentuk objek).
-release_date: Tanggal rilis film (dalam bentuk objek).
-revenue: Pendapatan yang dihasilkan oleh film (dalam bentuk bilangan bulat).
-runtime: Durasi film dalam menit (dalam bentuk bilangan desimal).
-spoken_languages: Bahasa-bahasa yang digunakan dalam film (dalam bentuk objek).
-status: Status produksi film (dalam bentuk objek).
-tagline: Tagline atau slogan film (dalam bentuk objek).
-title: Judul film (dalam bentuk objek).
-vote_average: Nilai rata-rata voting film (dalam bentuk bilangan desimal).
-vote_count: Jumlah voting yang diberikan pada film (dalam bentuk bilangan bulat).

## Visualisasi Data
![image](https://github.com/wigaaudi/ML_Terapan_Dicoding/assets/116898134/8406d4e3-d101-40ef-952a-d8e1bb6e5944)
 Berdasarkan visualisasi di atas, dapat diketahui bahwa film dengan tingkat popularitas tertinggi adalah film "Minions" yang menduduki peringkat pertama, sementara film "Big Hero 6" berada di peringkat kesepuluh dalam daftar film dengan tingkat popularitas tertinggi.
 
## Data Preparation
Dalam tahap Data Preparation, beberapa teknik yang dilakukan pada dataset "tmdb_5000_movies.csv" adalah sebagai berikut:

1. Mengubah format kolom "genres" dari JSON menjadi list.
2. Mengubah tipe data pada kolom "genres" dari list menjadi string.
3. Membuat variabel "movies_new" yang berisi dataframe dengan kolom "title", "genres", dan "popularity".
4. Mencari data film yang memiliki nilai kosong pada kolom "genres".
5. Menghapus data film yang memiliki genre kosong.
Tahapan-tahapan tersebut dilakukan untuk mempersiapkan data agar siap digunakan dalam tahap model development. Dengan mengubah format kolom "genres" menjadi list dan menghapus data film yang memiliki genre kosong, kita dapat memastikan kebersihan dan konsistensi data sebelum melanjutkan ke tahap development.

## Modeling
Berikut adalah tahapan-tahapan yang dilakukan untuk membangun model sistem rekomendasi dalam menyelesaikan permasalahan:

1. Membangun Matrix TF-IDF:
 - Menggunakan TfidfVectorizer untuk menghitung nilai TF-IDF (Term Frequency-Inverse Document Frequency) dari data genres.
 - Matrix TF-IDF ini akan digunakan sebagai representasi fitur dari film-film dalam dataset.

2. Menghitung Similarity Matrix:
 - Menggunakan cosine_similarity untuk menghitung similarity antara setiap pasangan film dalam dataset berdasarkan matrix TF-IDF.
 - Similarity matrix ini akan digunakan sebagai dasar untuk menentukan tingkat kesamaan antara film-film.

3.Membangun Model Rekomendasi:
 - Menggunakan similarity matrix untuk menghasilkan rekomendasi film.
 - Membuat fungsi film_recommendations yang akan menerima input berupa nama film dan menghasilkan rekomendasi film berdasarkan tingkat kesamaan dengan film tersebut.

4. Menampilkan Top-N Recommendation:
 - Menggunakan fungsi film_recommendations untuk menghasilkan top-N rekomendasi film.
 - Output akan berupa daftar film rekomendasi yang disusun berdasarkan tingkat popularitas.

Dalam tahapan ini, telah disajikan satu solusi rekomendasi berdasarkan similarity matrix dan penggunaan metode cosine similarity. Solusi ini memungkinkan untuk mendapatkan rekomendasi film yang memiliki tingkat kesamaan yang tinggi dengan film yang diberikan.

Kelebihan:

Metode cosine similarity memberikan perhitungan kesamaan yang sederhana dan efektif untuk mengukur kesamaan antara film-film.
Dengan menggunakan metode ini, kita dapat dengan cepat menghasilkan rekomendasi film berdasarkan tingkat kesamaan dengan film yang diberikan.

Kekurangan:

Metode cosine similarity tidak mempertimbangkan konteks atau fitur lain dari film selain dari data genre.
Tidak ada personalisasi yang dilakukan dalam rekomendasi, sehingga rekomendasi film sama untuk setiap pengguna.

## Evaluation
Dalam proyek ini, penulis menggunakan metrik evaluasi sistem rekomendasi yang dikenal sebagai recommender system precision.

![image](https://github.com/wigaaudi/ML_Terapan_Dicoding/assets/116898134/db6ac071-456a-4831-9e2a-142020632c73)

Recommender system precision mengukur sejauh mana film-film yang direkomendasikan secara tepat kepada pengguna. Dalam konteks ini, kita ingin memastikan bahwa film-film yang direkomendasikan kepada pengguna benar-benar relevan dengan film "Cavite" yang menjadi acuan.

Dalam tabel rekomendasi film di bawah ini, kita menampilkan beberapa film yang memiliki kesamaan genre dengan "Cavite":

|   |              title |               genres | popularity |
|--:|-------------------:|---------------------:|-----------:|
| 0 |         The Circle |        Drama Foreign |   1.193779 |
| 1 |           Aberdeen | Drama Comedy Foreign |   1.068819 |
| 2 |      The Holy Girl |        Drama Foreign |   0.684881 |  
| 3 |       Pandaemonium |        Drama Foreign |   0.165367 |   
| 4 | The Other Conquest |        Drama Foreign |   0.015597 |   

Berdasarkan tabel ini, penulis dapat melakukan evaluasi dengan menghitung precision. Precision dihitung dengan membandingkan jumlah film yang relevan dengan "Cavite" dalam rekomendasi dengan jumlah total film yang direkomendasikan.

Jika mengasumsikan bahwa film-film di tabel di atas adalah film yang relevan dengan "Cavite", maka model memiliki 5 film yang relevan dalam 5 rekomendasi. Oleh karena itu, precisionnya adalah 1.0 atau 100%.

Dengan precision yang sempurna ini, dapat dikatakan bahwa sistem rekomendasi telah berhasil dalam memberikan rekomendasi film yang relevan dengan "Cavite".

- Kelebihan dari pendekatan ini adalah:

  - Rekomendasi film didasarkan pada kesamaan genre dengan film acuan, sehingga memastikan film-film yang direkomendasikan memiliki karakteristik yang serupa.
  - Precision yang tinggi menunjukkan bahwa rekomendasi yang diberikan sangat akurat dan relevan.

- Namun, ada beberapa kekurangan yang perlu diperhatikan:

  - Pendekatan ini hanya mempertimbangkan kesamaan genre dalam menentukan rekomendasi. Faktor-faktor lain seperti aktor, sutradara, atau tema film tidak dipertimbangkan.
  - Data yang digunakan dalam pembuatan sistem rekomendasi ini terbatas pada dataset yang tersedia.
  - 
Dapat diambil kesimpulan bahwa kualitas rekomendasi dapat ditingkatkan dengan dataset yang lebih luas dan representatif.
Dalam proyek ini, pendekatan sistem rekomendasi yang digunakan telah memberikan hasil yang baik dengan precision yang tinggi. Namun, masih ada ruang untuk pengembangan lebih lanjut guna meningkatkan akurasi dan kualitas rekomendasi.
