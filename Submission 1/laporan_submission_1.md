# Laporan Proyek Machine Learning 1 (Credit Risk) - Wiga Audi Prasetyo

## Domain Proyek

Industri keuangan, khususnya dalam sektor pemberian pinjaman, memiliki risiko kredit yang signifikan. Risiko kredit merujuk pada kemungkinan tidak dapatnya pihak yang meminjam untuk memenuhi kewajiban pembayaran pinjaman mereka. Dalam hal ini, pendekatan yang menggunakan machine learning dan analisis data dapat menjadi solusi yang efektif untuk mengidentifikasi dan mengelola risiko kredit.

Ketika pelanggan gagal membayar pinjaman, lembaga keuangan menghadapi risiko kerugian yang dapat memiliki konsekuensi serius. Kerugian ini dapat terjadi dalam beberapa bentuk, antara lain:

1. Hilangnya Pendapatan Bunga: Lembaga keuangan mengandalkan pendapatan bunga dari pinjaman yang diberikan. Jika pelanggan gagal membayar pinjaman, lembaga keuangan kehilangan sumber pendapatan ini. Hal ini dapat mengganggu aliran kas dan mengurangi profitabilitas lembaga keuangan.

2. Penurunan Kualitas Aset: Jika pinjaman bermasalah meningkat, kualitas aset lembaga keuangan akan menurun. Aset yang bermasalah akan mempengaruhi peringkat kredit lembaga keuangan, serta mengurangi nilai aset yang dapat digunakan sebagai jaminan atau likuidasi dalam situasi darurat.

3. Penurunan Kepercayaan Pelanggan: Ketika lembaga keuangan gagal mengelola risiko kredit dengan baik, ini dapat mengurangi kepercayaan pelanggan terhadap lembaga tersebut. Pelanggan yang sadar akan risiko kredit yang tinggi mungkin akan mencari alternatif pemberi pinjaman yang lebih dapat diandalkan. Penurunan kepercayaan pelanggan dapat mengakibatkan penurunan basis pelanggan dan pangsa pasar lembaga keuangan.

OOleh karena itu, penting bagi lembaga keuangan untuk mengidentifikasi dan mengelola risiko kredit dengan cara yang efektif

Proyek credit risk bertujuan untuk mengembangkan model prediksi risiko kredit yang dapat memberikan informasi yang berharga bagi lembaga keuangan. Dengan menggunakan teknik-teknik machine learning, model ini akan didesain untuk menganalisis data pelanggan, mempelajari pola-pola yang relevan, dan membuat prediksi terhadap peluang terjadinya risiko kredit pada setiap pelanggan. Model ini akan menjadi alat yang sangat berguna bagi lembaga keuangan dalam mengidentifikasi dan mengelola risiko kredit, serta membantu meningkatkan keputusan kredit yang lebih akurat dan berbasis data.

## Business Understanding

### Problem Statements

Berdasarkan latar belakang yang sudah dibahas sebelumnya, maka problem statement untuk proyek ini adalah:
- Bagaimana cara mengidentifikasi secara efisien pelanggan dengan potensi risiko kredit yang tinggi bagi lembaga keuangan?
-  Bagaimana meningkatkan tingkat akurasi evaluasi risiko kredit untuk mengurangi kerugian finansial yang mungkin terjadi?"

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
Dibuat heatmap korelasi untuk melihat hubungan antara variabel-variabel numerik. Heatmap memberikan informasi tentang sejauh mana variabel-variabel saling berkorelasi. Berdasarkan nilai-nilai korelasi pada heatmap, terdapat beberapa hubungan antara variabel-variabel yang dapat diamati:

1. Variabel "income" memiliki korelasi positif yang sedang dengan variabel "loan" (0.44). Hal ini menunjukkan adanya hubungan yang cukup kuat antara pendapatan dan jumlah pinjaman yang diberikan. Artinya, semakin tinggi pendapatan seseorang, kemungkinan besar jumlah pinjaman yang diajukan juga akan lebih tinggi.

2. Variabel "age" memiliki korelasi negatif yang cukup kuat dengan variabel "default" (-0.45). Hal ini menunjukkan adanya hubungan yang signifikan antara usia nasabah dengan status "default". Semakin tua usia nasabah, kemungkinan status "default" yang dia miliki akan lebih rendah.

3. Variabel "loan" juga memiliki korelasi positif yang sedang dengan variabel "default" (0.38). Ini menunjukkan adanya hubungan yang cukup kuat antara jumlah pinjaman dan status "default". Dengan kata lain, semakin tinggi jumlah pinjaman, kemungkinan status "default" yang dialami nasabah juga akan lebih tinggi.

Dengan menggunakan heatmap korelasi, dapat memahami hubungan antara variabel-variabel dalam dataset dan mengidentifikasi pola-pola yang berguna dalam memprediksi risiko kredit.

- Pairplot:
Dibuat pairplot untuk melihat hubungan antara variabel-variabel numerik secara keseluruhan. Pairplot memungkinkan untuk melihat pola korelasi dan distribusi variabel dalam satu visualisasi.


Selain teknik visualisasi data yang telah dijelaskan, analisis statistik deskriptif juga memberikan informasi penting tentang karakteristik variabel numerik dalam dataset. Berikut adalah rincian analisis statistik deskriptif untuk variabel numerik:

1. Variabel "income":

Mean (rata-rata): $45,331.60
Median (nilai tengah): $45,789.12
Distribusi pendapatan cenderung bervariasi, dengan standar deviasi sekitar $14,326.33. Ini menunjukkan variasi yang signifikan dalam pendapatan pelanggan.

2. Variabel "age":

    Mean (rata-rata): 40.81 tahun
    Median (nilai tengah): 41.32 tahun
    Standar deviasi: 13.62 tahun
    Distribusi usia memiliki variasi yang sedikit lebih rendah daripada pendapatan, tetapi juga tidak condong ke satu sisi.

3. Variabel "loan":

    Mean (rata-rata): $4,444.37
    Median (nilai tengah): $3,974.72
    Standar deviasi: $3,045.41
    Distribusi jumlah pinjaman memiliki variasi yang signifikan, dengan nilai rata-rata yang lebih tinggi daripada median. Hal ini menunjukkan adanya kemungkinan adanya nilai ekstrim yang lebih tinggi dalam sampel.

4. Variabel "default":

    Persentase pelanggan yang memiliki status default: 14.15%
    Persentase pelanggan yang tidak memiliki status default: 85.85%
    Variabel ini merupakan variabel kategorikal yang mengindikasikan status default pelanggan.

Analisis statistik deskriptif ini memberikan ringkasan tentang nilai rata-rata, median, dan distribusi variabel numerik dalam dataset. Informasi ini membantu memahami karakteristik data secara lebih terperinci dan memberikan gambaran tentang variasi, pola, dan kecenderungan dalam dataset.

Melalui visualisasi data tersebut, dapat diperoleh pemahaman tentang distribusi variabel, pola korelasi antara variabel, serta adanya outlier atau anomali data. EDA membantu dalam memahami karakteristik data, mengidentifikasi pola, dan mengeksplorasi hubungan antar variabel. Hal ini memberikan wawasan yang berharga dalam membangun model prediksi risiko kredit.

Dengan melakukan tahap EDA ini, kita dapat memahami data dengan lebih baik, mengidentifikasi pola dan hubungan yang relevan, serta mengambil keputusan yang tepat dalam proses pemodelan.

## Data Preparation
Pada tahap Data Preparation, beberapa teknik telah diterapkan untuk mempersiapkan data sebelum dilakukan pemodelan. Berikut adalah langkah-langkah yang dilakukan dalam proses data preparation:

Penghapusan Kolom "clientid":
Kolom "clientid" dihapus dari dataset karena kolom ini tidak memberikan kontribusi yang signifikan terhadap prediksi risiko kredit. Artinya, informasi yang terkandung dalam kolom "clientid" tidak relevan atau tidak berpengaruh dalam memprediksi risiko kredit. Oleh karena itu, kolom ini dihapus menggunakan fungsi drop() agar tidak mempengaruhi analisis dan pemodelan yang dilakukan.

Handling Missing Values:
Terdapat 3 nilai yang hilang pada kolom "age". Jumlah data yang hilang tersebut relatif kecil dibandingkan dengan jumlah total data, sehingga baris yang mengandung nilai yang hilang dihapus menggunakan metode dropna() dengan menyebutkan subset kolom "age". Dengan menghapus baris yang mengandung nilai yang hilang, maka dapat memastikan kebersihan dan kekonsistenan data yang digunakan dalam analisis lebih lanjut.

Handling Negative Values:
Terdapat beberapa nilai negatif pada kolom "age", yang tidak konsisten dengan usia yang sebenarnya. Nilai negatif pada kolom "age" dapat dianggap sebagai kesalahan input atau kesalahan dalam proses pengumpulan data. Oleh karena itu, baris yang mengandung nilai negatif dihapus menggunakan filter (df[['age']] >= 0).all(axis=1). Dengan menghapus baris yang mengandung nilai negatif, dapat memastikan bahwa data yang digunakan dalam analisis memiliki kualitas yang baik dan konsisten.

Pembagian dataset:
Proses pembagian dataset menjadi data pelatihan (train dataset) dan data uji (test dataset) dilakukan menggunakan fungsi train_test_split dari library sklearn.model_selection.

Pada kode yang diberikan, dataset awal (df) dibagi menjadi dua bagian, yaitu X dan y. Variabel X merupakan dataset yang berisi semua fitur kecuali kolom "default" yang digunakan sebagai target atau label yang disimpan dalam variabel y.

Parameter test_size pada fungsi train_test_split diatur sebesar 0.4, yang berarti data uji akan memiliki proporsi 40% dari keseluruhan dataset, sementara data pelatihan akan memiliki proporsi 60%. Proporsi ini dapat diubah sesuai kebutuhan.

Parameter random_state pada fungsi train_test_split diatur sebagai 123. Pengaturan ini digunakan untuk menjaga konsistensi pembagian dataset yang dilakukan. Jika menggunakan nilai random_state yang sama, pembagian dataset akan tetap sama setiap kali kode dijalankan.

Hasil dari proses pembagian dataset dicetak menggunakan perintah print. Dalam contoh ini, dicetak jumlah sampel dalam keseluruhan dataset, jumlah sampel dalam data pelatihan, dan jumlah sampel dalam data uji.

Output yang dihasilkan adalah:

Total # of sample in whole dataset: 1994
Total # of sample in train dataset: 1196
Total # of sample in test dataset: 798

Artinya, dataset awal memiliki 1994 sampel. Setelah pembagian dataset, data pelatihan memiliki 1196 sampel, sedangkan data uji memiliki 798 sampel.

Standarisasi:
Variabel numerik ("income", "age", dan "loan") dalam dataset di-standarisasi menggunakan StandardScaler dari library sklearn.preprocessing. Hal ini dilakukan untuk mengubah skala variabel numerik agar memiliki mean 0 dan standar deviasi 1, sehingga mempermudah proses pemodelan.

Setiap tahap data preparation di atas dilakukan dengan tujuan untuk membersihkan dan menyesuaikan data agar siap untuk proses pemodelan. Penghapusan kolom dan penanganan nilai yang hilang serta nilai negatif penting untuk menjaga integritas data dan memastikan bahwa data yang digunakan dalam proses pemodelan adalah valid dan relevan. Standarisasi dilakukan untuk menghilangkan perbedaan skala antar variabel numerik, sehingga meminimalkan pengaruh skala pada algoritma pemodelan.

Tahap data preparation sangat penting dalam menghasilkan model yang akurat dan dapat diandalkan untuk memprediksi risiko kredit. Dengan melakukan langkah-langkah ini, dataset telah siap untuk proses pemodelan selanjutnya.

## Modeling
Pada tahap Modeling, dilakukan pemilihan dan penggunaan algoritma machine learning untuk membangun model prediksi risiko kredit. Dalam proyek ini, dua algoritma yang digunakan adalah K-Nearest Neighbors (KNN) dan Random Forest.

1. K-Nearest Neighbors (KNN):
Algoritma KNN adalah metode non-parametrik yang digunakan untuk klasifikasi dan regresi. Dalam kasus ini, KNN digunakan sebagai algoritma klasifikasi untuk memprediksi status "default" klien. KNN bekerja dengan mencari k-neighbors terdekat dari data uji dan melakukan voting mayoritas untuk mengklasifikasikan data tersebut. Pada algoritma KNN, terdapat beberapa parameter yang perlu ditentukan, salah satunya adalah jumlah tetangga (k). Jumlah tetangga yang dipilih akan mempengaruhi hasil prediksi. Contoh penggunaan parameter k pada KNN adalah k = 10, di mana model akan mencari 10 tetangga terdekat dari data uji untuk melakukan voting mayoritas dalam proses klasifikasi.
Kelebihan KNN:

- Sederhana dan mudah diimplementasikan.
- Tidak memerlukan asumsi tertentu tentang data.
- Dapat digunakan untuk masalah klasifikasi dan regresi.

Kekurangan KNN:

- Sensitif terhadap skala data.
- Perlu menentukan jumlah tetangga (k) yang optimal.
- Komputasi yang mahal jika jumlah data besar.

2. Random Forest:
Random Forest adalah algoritma ensemble yang menggabungkan beberapa pohon keputusan untuk melakukan klasifikasi. Setiap pohon dalam Random Forest diberikan sebagian data yang diambil secara acak dan atribut yang dipilih secara acak. Prediksi akhir didapatkan dengan melakukan voting mayoritas dari prediksi semua pohon dalam hutan. Pada algoritma Random Forest, terdapat beberapa parameter yang perlu ditentukan, misalnya jumlah pohon (n_estimators). Contoh penggunaan parameter n_estimators pada Random Forest adalah n_estimators = 100, di mana model akan terdiri dari 100 pohon keputusan dalam proses klasifikasinya.

Kelebihan Random Forest:

- Efektif dalam mengatasi overfitting.
- Mampu menangani data dengan fitur yang banyak dan beragam.
- Tidak memerlukan pre-processing data yang kompleks.

Kekurangan Random Forest:

- Cenderung kompleks dan membutuhkan waktu untuk proses pelatihan.
- Interpretasi model yang sulit dibandingkan dengan model pohon keputusan tunggal.


## Evaluation
Dalam proyek ini, metrik evaluasi yang digunakan adalah akurasi (accuracy). Akurasi adalah metrik yang mengukur sejauh mana model mampu mengklasifikasikan dengan benar data yang ada.

Akurasi dihitung dengan membagi jumlah prediksi yang benar dengan jumlah total data yang diprediksi. Metrik ini memberikan gambaran tentang seberapa baik model dapat memprediksi dengan benar. Namun, akurasi bisa menjadi bias jika jumlah kelas dalam data tidak seimbang.

|           | train     | test      |
|-----------|-----------|-----------|
| KNN       | 97.993311 | 98.120301 |
| RF        | 100.0     | 98.370927 |

![image](https://github.com/wigaaudi/ML_Terapan_Dicoding/assets/116898134/73007ac5-2aec-45aa-858a-06da779254d4)

Berdasarkan hasil proyek, model Random Forest memiliki akurasi train sebesar 100% dan akurasi test sebesar 98.37%. Sementara itu, model KNN memiliki akurasi train sebesar 97.99% dan akurasi test sebesar 98.12%.

Dengan akurasi yang tinggi pada data test, kedua model mampu memberikan prediksi yang akurat dalam memprediksi risiko kredit. Model Random Forest memperoleh akurasi yang sedikit lebih tinggi dibandingkan dengan model KNN, menunjukkan kemampuannya dalam mengklasifikasikan data dengan lebih baik.

