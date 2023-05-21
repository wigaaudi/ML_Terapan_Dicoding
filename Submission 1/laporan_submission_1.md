# Laporan Proyek Machine Learning 1 (Credit Risk) - Wiga Audi Prasetyo

## Domain Proyek

Industri keuangan, khususnya dalam sektor pemberian pinjaman, memiliki risiko kredit yang signifikan. Risiko kredit merujuk pada kemungkinan tidak dapatnya pihak yang meminjam untuk memenuhi kewajiban pembayaran pinjaman mereka. Dalam hal ini, pendekatan yang menggunakan machine learning dan analisis data dapat menjadi solusi yang efektif untuk mengidentifikasi dan mengelola risiko kredit.

Dalam industri keuangan, salah satu tantangan utama adalah memprediksi risiko kredit dengan akurasi tinggi. Melakukan evaluasi risiko kredit secara manual dapat memakan waktu dan terkadang tidak efisien. Oleh karena itu, menggunakan pendekatan machine learning untuk mengklasifikasikan pelanggan berdasarkan risiko kredit dapat membantu lembaga keuangan dalam pengambilan keputusan yang lebih cepat dan lebih tepat.

Proyek credit risk bertujuan untuk mengembangkan model prediksi risiko kredit yang dapat memberikan informasi yang berharga bagi lembaga keuangan. Dengan menggunakan teknik-teknik machine learning, model ini akan didesain untuk menganalisis data pelanggan, mempelajari pola-pola yang relevan, dan membuat prediksi terhadap peluang terjadinya risiko kredit pada setiap pelanggan. Model ini akan menjadi alat yang sangat berguna bagi lembaga keuangan dalam mengidentifikasi dan mengelola risiko kredit, serta membantu meningkatkan keputusan kredit yang lebih akurat dan berbasis data.

## Business Understanding

### Problem Statements

Berdasarkan latar belakang yang sudah dibahas sebelumnya, maka problem statement untuk proyek ini adalah:
- Lembaga keuangan menghadapi risiko kredit yang tinggi dan sulit untuk mengidentifikasi secara efisien pelanggan yang memiliki potensi risiko kredit.
- Proses evaluasi risiko kredit secara manual membutuhkan waktu yang lama dan tidak memberikan tingkat akurasi yang optimal.

### Goals

Berdasarkan problem statement sebelumnya, maka adapun goals yang ingin dicapai dalam proyek ini adalah:
- Mengembangkan model prediksi risiko kredit yang dapat mengidentifikasi pelanggan dengan potensi risiko kredit secara efisien.
- Meningkatkan tingkat akurasi dalam evaluasi risiko kredit dengan menggunakan pendekatan machine learning.


### Solution statements
- Menggunakan beberapa algoritma machine learning seperti Random Forest, dan K-Nearest Neighbord untuk membangun model prediksi risiko kredit. Hal ini akan memberikan pembandingan dan pilihan terbaik dalam mengidentifikasi pelanggan dengan potensi risiko kredit.
-Menggunakan teknik feature engineering untuk meningkatkan pemahaman dan representasi data. Dengan mengidentifikasi dan mengekstraksi fitur-fitur yang relevan dari data kredit, seperti hutang, pendapatan, dan usia dapat menghasilkan informasi yang lebih kuat untuk mendukung model prediksi risiko kredit.
- Metrik evaluasi yang akan digunakan:
Tingkat akurasi: Mengukur sejauh mana model dapat mengklasifikasikan pelanggan dengan benar menjadi kategori risiko kredit yang sesuai.

## Data Understanding
Dalam proyek ini, penulis menggunakan dataset Credit Risk yang terdiri dari 5 kolom dan 2000 baris dan dapat diunduh dari Kaggle melalui tautan berikut: https://www.kaggle.com/datasets/upadorprofzs/credit-risk.

Dataset ini mencakup informasi tentang pelanggan kredit dan target yang merupakan variabel default yang menunjukkan apakah seorang pelanggan memiliki risiko kredit yang tinggi atau rendah.


### Variabel-variabel pada Dataset Credit Risk adalah sebagai berikut:
Berikut adalah penjelasan singkat tentang masing-masing kolom dalam dataset:

-ClientID: Kolom ini berisi ID unik untuk setiap pelanggan. ID ini digunakan untuk mengidentifikasi pelanggan secara individu.

-Income: Kolom ini menyimpan informasi tentang pendapatan pelanggan. Pendapatan diukur dalam satuan tertentu (dalam mata uang tertentu).

-Age: Kolom ini mencatat usia pelanggan dalam tahun. Usia adalah faktor yang dapat mempengaruhi risiko kredit seseorang.

-Loan: Kolom ini berisi jumlah pinjaman yang dimiliki oleh pelanggan. Jumlah pinjaman dapat mencerminkan tingkat ketergantungan pelanggan pada pinjaman atau hutang.

-Default: Kolom ini adalah target variabel yang menunjukkan apakah seorang pelanggan memiliki risiko kredit yang tinggi (1) atau rendah (0). Ini adalah kolom yang ingin diprediksi menggunakan model machine learning.

### Beberapa teknik visualisasi data telah diterapkan dalam EDA. Berikut adalah beberapa langkah yang dilakukan:

- Histogram:
Dilakukan visualisasi histogram untuk melihat distribusi variabel-variabel numerik dalam dataset. Histogram memberikan gambaran tentang sebaran nilai pada setiap variabel.

- Heatmap Korelasi:
Dibuat heatmap korelasi untuk melihat hubungan antara variabel-variabel numerik. Heatmap memberikan informasi tentang sejauh mana variabel-variabel saling berkorelasi.

- Pairplot:
Dibuat pairplot untuk melihat hubungan antara variabel-variabel numerik secara keseluruhan. Pairplot memungkinkan untuk melihat pola korelasi dan distribusi variabel dalam satu visualisasi.

Melalui visualisasi data tersebut, dapat diperoleh pemahaman tentang distribusi variabel, pola korelasi antara variabel, serta adanya outlier atau anomali data. EDA membantu dalam memahami karakteristik data, mengidentifikasi pola, dan mengeksplorasi hubungan antar variabel. Hal ini memberikan wawasan yang berharga dalam membangun model prediksi risiko kredit.

Dengan melakukan tahap EDA ini, kita dapat memahami data dengan lebih baik, mengidentifikasi pola dan hubungan yang relevan, serta mengambil keputusan yang tepat dalam proses pemodelan.

## Data Preparation
Pada tahap Data Preparation, beberapa teknik telah diterapkan untuk mempersiapkan data sebelum dilakukan pemodelan. Berikut adalah langkah-langkah yang dilakukan dalam proses data preparation:

Penghapusan Kolom "clientid":
Kolom "clientid" tidak memberikan kontribusi yang signifikan terhadap prediksi risiko kredit. Oleh karena itu, kolom ini dihapus dari dataset menggunakan fungsi drop().

Handling Missing Values:
Terdapat 3 nilai yang hilang pada kolom "age". Karena jumlah data yang hilang relatif kecil, baris yang mengandung nilai yang hilang dihapus menggunakan metode dropna() dengan menyebutkan subset kolom "age".

Handling Negative Values:
Terdapat beberapa nilai negatif pada kolom "age", yang tidak konsisten dengan usia yang sebenarnya. Oleh karena itu, baris yang mengandung nilai negatif dihapus dengan menggunakan filter (df[['age']] >= 0).all(axis=1).

Standarisasi:
Variabel numerik ("income", "age", dan "loan") dalam dataset di-standarisasi menggunakan StandardScaler dari library sklearn.preprocessing. Hal ini dilakukan untuk mengubah skala variabel numerik agar memiliki mean 0 dan standar deviasi 1, sehingga mempermudah proses pemodelan.

Setiap tahap data preparation di atas dilakukan dengan tujuan untuk membersihkan dan menyesuaikan data agar siap untuk proses pemodelan. Penghapusan kolom dan penanganan nilai yang hilang serta nilai negatif penting untuk menjaga integritas data dan memastikan bahwa data yang digunakan dalam proses pemodelan adalah valid dan relevan. Standarisasi dilakukan untuk menghilangkan perbedaan skala antar variabel numerik, sehingga meminimalkan pengaruh skala pada algoritma pemodelan.

Tahap data preparation sangat penting dalam menghasilkan model yang akurat dan dapat diandalkan untuk memprediksi risiko kredit. Dengan melakukan langkah-langkah ini, dataset telah siap untuk proses pemodelan selanjutnya.

## Modeling
Pada tahap Modeling, dilakukan pemilihan dan penggunaan algoritma machine learning untuk membangun model prediksi risiko kredit. Dalam proyek ini, dua algoritma yang digunakan adalah K-Nearest Neighbors (KNN) dan Random Forest.

1. K-Nearest Neighbors (KNN):
Algoritma KNN adalah metode non-parametrik yang digunakan untuk klasifikasi dan regresi. Dalam kasus ini, KNN digunakan sebagai algoritma klasifikasi untuk memprediksi status "default" klien. KNN bekerja dengan mencari k-neighbors terdekat dari data uji dan melakukan voting mayoritas untuk mengklasifikasikan data tersebut.

Kelebihan KNN:

- Sederhana dan mudah diimplementasikan.
- Tidak memerlukan asumsi tertentu tentang data.
- Dapat digunakan untuk masalah klasifikasi dan regresi.

Kekurangan KNN:

- Sensitif terhadap skala data.
- Perlu menentukan jumlah tetangga (k) yang optimal.
- Komputasi yang mahal jika jumlah data besar.

2. Random Forest:
Random Forest adalah algoritma ensemble yang menggabungkan beberapa pohon keputusan untuk melakukan klasifikasi. Setiap pohon dalam Random Forest diberikan sebagian data yang diambil secara acak dan atribut yang dipilih secara acak. Prediksi akhir didapatkan dengan melakukan voting mayoritas dari prediksi semua pohon dalam hutan.

Kelebihan Random Forest:

- Efektif dalam mengatasi overfitting.
- Mampu menangani data dengan fitur yang banyak dan beragam.
- Tidak memerlukan pre-processing data yang kompleks.

Kekurangan Random Forest:

- Cenderung kompleks dan membutuhkan waktu untuk proses pelatihan.
- Interpretasi model yang sulit dibandingkan dengan model pohon keputusan tunggal.

Berdasarkan hasil evaluasi, terlihat bahwa kedua model memiliki performa yang baik dengan tingkat akurasi yang tinggi. Namun, model Random Forest menunjukkan akurasi yang lebih tinggi pada data train (100%) dibandingkan dengan model KNN (97.99%). Pada data test, model Random Forest juga memiliki akurasi yang sedikit lebih tinggi dibandingkan dengan model KNN (98.37% vs. 98.12%).

Sebagai solusi terbaik, penulis dapat memilih model Random Forest karena memiliki akurasi yang lebih tinggi pada data train dan test. Model ini memiliki kemampuan untuk menangani kompleksitas data dan efektif dalam mengatasi overfitting. Selain itu, Random Forest tidak memerlukan pre-processing data yang kompleks.

## Evaluation
Dalam proyek ini, metrik evaluasi yang digunakan adalah akurasi (accuracy). Akurasi adalah metrik yang mengukur sejauh mana model mampu mengklasifikasikan dengan benar data yang ada.

Akurasi dihitung dengan membagi jumlah prediksi yang benar dengan jumlah total data yang diprediksi. Metrik ini memberikan gambaran tentang seberapa baik model dapat memprediksi dengan benar. Namun, akurasi bisa menjadi bias jika jumlah kelas dalam data tidak seimbang.

Berdasarkan hasil proyek, model Random Forest memiliki akurasi train sebesar 100% dan akurasi test sebesar 98.37%. Sementara itu, model KNN memiliki akurasi train sebesar 97.99% dan akurasi test sebesar 98.12%.

Dengan akurasi yang tinggi pada data test, kedua model mampu memberikan prediksi yang akurat dalam memprediksi risiko kredit. Model Random Forest memperoleh akurasi yang sedikit lebih tinggi dibandingkan dengan model KNN, menunjukkan kemampuannya dalam mengklasifikasikan data dengan lebih baik.

