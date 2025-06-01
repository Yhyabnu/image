# Proyek Akhir Sistem Rekomendasi Obat

#### Disusun oleh : Yahya Ibnu Fajar

Ini adalah proyek akhir sistem rekomendasi untuk memenuhi submission dicoding. Proyek ini membangun model berbasis content based filtering yang dapat menentukan top-N rekomendasi obat bagi pegguna.

## Domain Proyek (Done)

### Latar Belakang

Perkembangan teknologi digital telah mengubah cara pengguna mengakses informasi, termasuk dalam bidang kesehatan. Salah satu terobosan penting dalam era digital ini adalah sistem rekomendasi, yang memanfaatkan data untuk memberikan saran yang personal dan relevan bagi pengguna. Dalam konteks kesehatan, sistem rekomendasi dapat membantu pasien, tenaga medis, maupun caregiver dalam menentukan pilihan pengobatan yang lebih tepat berdasarkan pengalaman nyata pengguna lain.
Di tengah maraknya informasi kesehatan yang tersedia secara online, pasien sering kali kesulitan memilih obat yang sesuai dengan kondisi mereka. Banyaknya pilihan dengan indikasi serupa, perbedaan respons tubuh, dan variasi efek samping membuat proses pemilihan obat menjadi kompleks. Ulasan pengguna pada platform seperti Drugs.com, WebMD, atau Healthgrades menyediakan sumber data berharga yang mencerminkan efektivitas obat, efek samping, serta pengalaman subjektif pasien. Data ini dapat menjadi dasar untuk membangun sistem rekomendasi yang lebih akurat dan berbasis bukti (evidence-based).

![Gambar obat](https://seputarbirokrasi.com/wp-content/uploads/2023/10/obat-puskesmas-1.jpg)

Dengan memanfaatkan teknik content-based filtering, sistem dapat menganalisis kemiripan antar obat berdasarkan pola ulasan, profil pengguna, dan kriteria medis. Pendekatan ini memungkinkan sistem untuk merekomendasikan obat dengan karakteristik serupa yang telah terbukti efektif bagi pengguna dengan kondisi kesehatan mirip.
Proyek ini tidak hanya bertujuan meningkatkan akurasi rekomendasi obat, tetapi juga memberdayakan pasien dengan informasi berbasis komunitas (crowdsourced knowledge). Harapannya, sistem ini dapat mengurangi ketergantungan pada trial-and-error dalam penggunaan obat, serta menjadi pelengkap bagi saran medis profesional. Dalam jangka panjang, pengembangan sistem semacam ini dapat diintegrasikan dengan platform kesehatan digital untuk memberikan layanan yang lebih komprehensif dan terpersonalisasi.

Referensi :
[1] Zheng, Y., et al. (2018). "Drug Recommendation Systems". JMIR Medical Informatics, 6(1).
[2] Yang, C.C., et al. (2020). "Mining Patient Reviews for Drug Recommendation". Journal of Biomedical Informatics, 102.

## Business Understanding (Done)

Proyek ini dibangun untuk perusahaan dengan karakteristik bisnis sebagai berikut :

- Perusahaan pengembang situs atau sistem kesehatan online.
- Perusahaan pengembang situs rekomendasi dan informasi obat.

### Problem Statement
Pasien sering kesulitan menemukan obat yang tepat untuk kondisi mereka berdasarkan pengalaman pengguna lain. Banyak pilihan obat yang tersedia namun informasi yang dimiliki pasien terbatas.

### Goals
1. Mengembangkan sistem rekomendasi obat berdasarkan ulasan pengguna.
2. Membantu pengguna menemukan obat alternatif yang sesuai dengan kondisi medis mereka.
3. Memberikan hasil rekomendasi yang relevan secara konteks dan isi ulasan.

### Solution Statement

1. Mengidentifikasi pola dan sentimen dalam ulasan pengguna.
2. Mencocokkan kondisi medis pengguna dengan ulasan yang relevan.
3. Memberikan rekomendasi obat yang sesuai dengan kebutuhan spesifik pengguna, termasuk alternatif yang tersedia.

## Data Understanding (Done)

Dataset yang digunakan dalam proyek ini berasal dari platform Kaggle dan berjudul "Drug Medical Dataset". Dataset ini memuat informasi terkait berbagai jenis obat yang telah digunakan oleh pasien, beserta karakteristik detail penggunaannya. Secara keseluruhan, dataset ini terdiri dari 15.000 entri data dan 7 kolom yang mencakup informasi seperti ID obat (uniqueID), nama obat (drugName), kondisi medis yang diobati (condition), ulasan pasien (review), rating efektivitas obat (rating), tanggal ulasan (date), dan jumlah pengguna yang merasa ulasan tersebut berguna (usefulCount).
Data ini sangat kaya dan relevan untuk pengembangan sistem rekomendasi, karena menggabungkan elemen objektif (seperti kondisi medis dan nama obat) serta elemen subjektif (seperti review dan rating dari pasien). Dengan struktur ini, dataset memberikan landasan yang kuat untuk membangun sistem rekomendasi berbasis konten, yang bertujuan membantu pasien menemukan alternatif obat berdasarkan pengalaman pengguna lain. Dataset ini dapat diakses dan diunduh secara publik melalui tautan berikut:
kaggle : [Drug_Madical](https://www.kaggle.com/datasets/yahyaazz/drug-madical)

Berikut informasi pada dataset :
Dataset obat
- Dataset memiliki format CSV.
- Dataset memiliki 15000 sample dengan 7 fitur.
- Dataset memiliki 3 fitur bertipe int64, dan 4 fitur bertipe object.
- Terdapat missing value pada dataset sebanyak 81 data
- jumlah data adalah 15.000 
- jumlah kolom adalah 7
- 
### Variable - Variable Pada Dataset
- `uniqueID` = ID unik untuk setiap entri data obat atau drugName
- `drugName` = Nama obat yang digunakan oleh pasien atau pengguna.
- `condition` = Kondisi medis atau penyakit yang menjadi alasan penggunaan obat
- `review` = Ulasan teks dari pengguna mengenai pengalaman mereka menggunakan obat tersebut.
- `rating` = Skor penilaian dari pengguna terhadap obat tersebut,  dalam skala 1–10.
- `date` = Tanggal ketika ulasan ditulis.
- `usefulCount` = Jumlah pengguna lain yang menganggap ulasan tersebut bermanfaat.

#### Analisis distribusi data rata-rata rating obat

<div><img src="https://drive.google.com/file/d/1-Gs0XZJD_P7AuM-YAlCfvBYKFiM9zrUW/view?usp=sharing" width="500"/></div

Sebagian besar rata-rata rating obat berada pada nilai 10 hal ini menunjukan kepuasan pelanggan atau konsumen.

### Multivariate Analysis

Multivariate Analysis menunjukkan hubungan antara dua atau lebih fitur dalam data.

#### Top 10 obat berdasarkan pada kondisi

<div><img src="https://drive.google.com/file/d/13c4p35gBtRtVVwO8DmJAzkaXOV0d9kDv/view?usp=drive_link" width="1000"/></div

Grafik ini menunjukkan obat-obatan yang paling banyak digunakan oleh pasien untuk berbagai kondisi medis. Levonorgestrel adalah obat yang paling sering digunakan, dengan 378 penggunaan.Diikuti oleh Etonogestrel (286) dan Ethinyl estradiol/norethindrone (240).Obat-obatan hormonal dan kontrasepsi mendominasi daftar ini, menunjukkan prevalensi penggunaannya untuk kondisi terkait reproduksi atau hormonal.

#### Top 10 obat berdasarkan rata-rata rating 

<div><img src="https://drive.google.com/file/d/1zjqiGOlcy10IARN712TsPVef8dx6aerc/view?usp=drive_link"  width="1000"/></div>
Meskipun rating 10.0 bisa mengindikasikan keefektifan tinggi, penting untuk mengevaluasi jumlah pengguna dan konteks penggunaan agar tidak bias oleh jumlah ulasan yang terlalu sedikit.

#### Top 10 obat berdasarkan usefulCount atau manfaat 

<div><img src="https://drive.google.com/file/d/1unrEYfhfYHt3YEBoDn_d9u8dLgEen9Pk/view?usp=drive_link" width="1000"/></div>

Grafik yang ditampilkan menggambarkan obat-obatan yang memiliki ulasan paling berguna menurut penilaian pengguna lain. Dari data yang terlihat, Sertraline menempati posisi teratas dengan total 949 pengguna yang menganggap ulasan mengenai obat ini bermanfaat.posisi kedua ditempati oleh Oxycodone, dengan 695 suara yang menyatakan bahwa ulasan tentang obat ini berguna. Di urutan ketiga terdapat Clonazepam dengan 559 suara. Kedua obat ini, bersama Sertraline, termasuk dalam kategori obat psikotropika atau penghilang nyeri, yang umumnya digunakan untuk menangani gangguan mental, kecemasan, atau nyeri kronis. beberapa obat lain seperti Prozac dan Adipex-P juga masuk dalam daftar sepuluh besar, memperkuat temuan bahwa obat-obatan yang berkaitan dengan kesehatan mental dan pengendalian rasa sakit cenderung menghasilkan ulasan yang dianggap sangat informatif oleh pengguna lain.

## Data Preparation

1. mengatasi missing value atau null
langkah awal dalam mengatasi missing value atau null adalah melakukan pengecekan dengan `isnull().sum()` setelah melakaukan pengecekan nilai kosong atau null pada dataset tersebut ditemukan 81 nilai kosong pada kolom condition. dikarenakan jumlah data yang relatif besar maka menghapus data tersebut tentu saja tidak akan berpengaruh secara signifikat terhadap proses selanjutnya. seletalah melakukan pengapusan missing data pada kolom condition maka jumlah data yang awalnya 15.000 menjadi 14.919.

2. mengecek dan menghapus duplicate dataset.
angkah selanjuntya yaitu melakukan pengecekan duplicate data dengan menggunakan fungsi duplicated, dengan hasil tidak ditemukannya data yang duplicate.

3. Menghapus symbol pada review.
Menghapus simbol pada kolom `review` menggunakan regex (regular expression) memiliki tujuan penting dalam preprocessing data teks sebelum dianalisis lebih lanjut.

4. Melakukan groupby pada kolom `drugName`, `Conditon` dan `rating` . groupby digunakan untuk menghitung jumlah entri data untuk setiap nama obat (drugName, condition, rating) dalam DataFrame obat.

### Pembuatan fitur Content dari penggabungan `drugName`, `condition`, dan `review`
Dalam sistem rekomendasi berbasis konten, keberhasilan model sangat bergantung pada representasi data teks yang digunakan untuk membandingkan kemiripan antar item. Untuk kasus rekomendasi obat, informasi penting tersebar di berbagai kolom seperti drugName (nama obat), condition (kondisi penyakit), dan review (ulasan dari pasien). Menggabungkan ketiga kolom ini menjadi satu fitur teks baru yang disebut content merupakan strategi untuk memperkaya informasi kontekstual dalam proses pembelajaran model.

penggabungan drugName, condition, dan review memberikan model akses terhadap seluruh deskripsi yang relevan dari sebuah entri obat. Kolom drugName membantu dalam membedakan merek atau jenis obat, condition menggambarkan konteks penggunaan (misalnya untuk "Depression" atau "Birth Control"), sedangkan review mengandung opini pengguna yang dapat memuat manfaat, efek samping, hingga pengalaman subjektif. Ketika ketiganya digabungkan menjadi satu teks utuh, model seperti TfidfVectorizer dapat menangkap kata-kata kunci penting dari seluruh komponen tersebut sekaligus.

Dengan membuat satu fitur content, memungkinkan sistem untuk melakukan perhitungan cosine similarity antar obat secara lebih akurat karena representasi vektor yang dihasilkan mencakup informasi yang lebih luas. Misalnya, dua obat yang berbeda nama tetapi digunakan untuk kondisi yang sama dan memiliki ulasan serupa akan memiliki skor kemiripan yang tinggi, dan ini menjadi dasar dalam memberikan rekomendasi.

### TfidfVectorizer

TF-IDF atau Term Frequency - Inverse Document Frequency adalah ukuran statistik yang menggambarkan pentingnya suatu istilah dalam sebuah dokumen relatif terhadap seluruh kumpulan dokumen (korpus). Metrik ini umumnya digunakan sebagai pembobot dalam pencarian informasi, penambangan teks, dan pemodelan preferensi pengguna. Nilai TF-IDF meningkat secara linier dengan jumlah kemunculan istilah dalam satu dokumen, namun juga menurun jika istilah tersebut umum dan muncul di banyak dokumen dalam korpus.
Dalam sistem rekomendasi obat, TF-IDF digunakan untuk menentukan representasi fitur penting dari ulasan pengguna terhadap masing-masing obat. Dengan menggunakan fungsi TfidfVectorizer() dari library scikit-learn, sistem dapat mengubah teks ulasan menjadi bentuk numerik yang mewakili tingkat kepentingan kata-kata dalam konteks setiap obat.
Setelah proses ini, hasil vektorisasi TF-IDF ditransformasikan ke dalam bentuk matriks menggunakan fungsi todense(). Matriks ini kemudian dimasukkan ke dalam dataframe baru yang menunjukkan skor TF-IDF untuk beberapa obat dan kata-kata kunci dalam ulasan pengguna.
Semakin tinggi nilai skor pada matriks tersebut, semakin kuat hubungan antara obat dengan kata kunci tertentu. Misalnya, jika obat Ibuprofen memiliki skor TF-IDF tinggi untuk kata "nyeri", maka sistem dapat mengenali bahwa obat tersebut erat kaitannya dengan pengobatan nyeri, dan dapat digunakan untuk merekomendasikan obat-obat lain dengan asosiasi kata kunci serupa.
Secara matematis, TF dari sebuah term dalam dokumen dihitung dengan membagi jumlah kemunculan kata tersebut dengan total jumlah kata dalam dokumen. Sementara IDF dihitung dengan menggunakan logaritma dari total jumlah dokumen dibagi jumlah dokumen yang mengandung kata tersebut, kemudian ditambahkan 1 untuk menghindari pembagian dengan nol. Dengan rumus lengkap sebagai berikut:
$$
TFIDF(t, d) = \frac{f_{t,d}}{N_d} \times \log\left( \frac{1 + N}{1 + df_t} \right) + 1
$$

### TruncatedSVD
TruncatedSVD adalah teknik reduksi dimensi yang digunakan untuk mengurangi kompleksitas data tinggi (high-dimensional) menjadi bentuk yang lebih ringkas namun tetap mempertahankan informasi penting. Berbeda dengan PCA (Principal Component Analysis), TruncatedSVD bisa digunakan langsung pada data sparse seperti hasil dari TF-IDF tanpa perlu merata-ratakan data.

Dalam sistem rekomendasi, khususnya yang berbasis matriks fitur seperti hasil dari TF-IDF Vectorizer, jumlah dimensi data bisa menjadi sangat besar. Setiap kata yang muncul dalam ulasan pengguna akan menjadi satu dimensi tersendiri, dan ini menghasilkan matriks yang sangat besar dan jarang (sparse). Di sinilah peran Truncated Singular Value Decomposition (TruncatedSVD) menjadi penting.
Transformasi dari dimensi (14919, 20949) menjadi (14919, 100) menggunakan TruncatedSVD menunjukkan keberhasilan sistem dalam menyaring informasi penting dan mengurangi beban komputasi tanpa mengorbankan akurasi rekomendasi. Langkah ini merupakan praktik standar dalam pemrosesan teks berskala besar dan menjadi fondasi penting dalam pembuatan sistem rekomendasi modern.

## Content Based Filtering Model & Result

Sistem yang dibangun oleh proyek ini adalah sistem rekomendasi sederhana untuk obat berdasarkan content-based filtering.
Sistem rekomendasi berbasis konten adalah sistem yang menyarankan obat-obatan yang memiliki karakteristik serupa dengan obat yang disukai atau pernah digunakan sebelumnya oleh pengguna. Jika suatu obat memiliki deskripsi, kategori, atau ulasan pengguna yang mirip dengan obat lainnya, maka kedua obat tersebut dianggap memiliki kemiripan.
Sebagai contoh, dalam sistem rekomendasi obat, apabila seorang pengguna menyukai atau memberikan ulasan positif terhadap obat Ibuprofen untuk nyeri sendi, maka sistem dapat merekomendasikan obat antiinflamasi nonsteroid (NSAID) lain dengan fungsi serupa, seperti Naproxen atau Ketoprofen.

#### Cosine Similarity
Cosine Similarity mengukur kesamaan antara dua vektor dan menentukan apakah kedua vektor menunjuk ke arah yang sama. Teknik ini bekerja dengan menghitung sudut cosinus antara dua vektor. Semakin kecil sudut cosinus antara dua vektor, semakin besar nilai kemiripan cosinusnya.

<div><img src="https://drive.google.com/file/d/1ZsZkce4BaCva6YOosd1YZt_6Dt-7xAQE/view?usp=drive_link" width="400"/></div>

Cosine similarity digunakan untuk menghitung derajat kesamaan antar obat berdasarkan representasi vektor dari ulasan pengguna. Untuk menghitung cosine similarity, digunakan fungsi cosine_similarity dari library scikit-learn.
Tahapan ini menghitung kesamaan antar obat menggunakan dataframe tfidf_matrix yang telah dihasilkan pada proses TF-IDF sebelumnya. TF-IDF merepresentasikan pentingnya kata-kata dalam ulasan, dan cosine similarity mengukur seberapa mirip dua obat berdasarkan kemiripan kata-kata yang muncul dalam ulasan pengguna.
Selanjutnya dibuat dataframe baru yang menampilkan nilai cosine similarity antar obat. Nilai ini menunjukkan tingkat kemiripan antara satu obat dengan obat lainnya. Semakin tinggi nilai cosine similarity (mendekati 1), maka kedua obat dianggap memiliki tingkat kemiripan yang tinggi dari sisi ulasan atau manfaat.
Sebagai contoh, obat Ibuprofen, Naproxen, dan Ketoprofen menunjukkan nilai cosine similarity yang tinggi satu sama lain, yang berarti ulasan pengguna terhadap ketiga obat ini mengandung kata-kata yang mirip, dan kemungkinan besar digunakan untuk kondisi medis yang serupa, seperti nyeri atau peradangan.

### Result

Fungsi `recommend_drugs` dibuat untuk menemukan rekomendasi obat menggunakan similarity yang telah didefinisikan sebelumnya. Fungsi ini bekerja dengan cara mengambil obat dengan similarity terbesar dari index yang ada.

Selanjutnya adalah menemukan rekomendasi yang mirip dengan Citalopram :

| uniqueID | drugName   | condition                     | review                                                                                    | rating | date      | usefulCount | content                                                                                    |
| -------- | ---------- | ----------------------------- | ----------------------------------------------------------------------------------------- | ------ | --------- | ----------- | ------------------------------------------------------------------------------------------ |
| 52       | Citalopram | Obsessive Compulsive Disorder | I suffered from severe panic attacks and OCD, and Citalopram has significantly helped me. | 10     | 25-Apr-16 | 30          | Citalopram Obsessive Compulsive Disorder I suffered from severe panic attacks and OCD, ... |


Berikut top 5 rekomendasi obat berdasarkan  kesamaan dengan Citopram :


| uniqueID | drugName  | condition     |
|----------|-----------|---------------|
| 9272     | Sertraline| Panic Disorde |
| 13894    | Paxil     | Panic Disorde |
| 5320     | Klonopin  | Panic Disorde |
| 5773     | Lorazepam | Panic Disorde |
| 8930     | Lorazepam | Panic Disorde |

Sistem telah berhasil merekomendasikan 5 obat teratas yang paling mirip dengan Citopram, yaitu beberapa obat lain yang juga digunakan untuk menangani Panic Disorder, seperti Sertraline, Paxil, Klonopin Lorazepam. Dengan demikian, jika seorang pengguna menyukai atau merespons positif terhadap Citopram maka sistem dapat merekomendasikan obat alternatif seperti Paxil atau Sertraline yang memiliki efek dan fungsi serupa dalam mengatasi kondisi tersebut

## Evaluation

### 1. Metrik Evaluasi yang Digunakan
Untuk mengevaluasi kinerja sistem rekomendasi, digunakan dua metrik utama:
*1. Precision@K:*
Precision@K mengukur seberapa banyak dari K rekomendasi teratas yang memiliki kondisi medis (condition) yang sama dengan obat acuan. Ini menunjukkan seberapa relevan hasil rekomendasi dalam konteks penggunaan obat. Dalam implementasi sistem, precision dievaluasi berdasarkan seberapa banyak dari rekomendasi obat yang benar-benar relevan dengan kondisi pengguna, yaitu berdasarkan kemiripan isi ulasan (TF-IDF dan cosine similarity), serta relevansi kondisi medis. Sebagai contoh, jika sistem merekomendasikan 5 obat dan 4 di antaranya memang relevan berdasarkan pengalaman pengguna dengan kondisi yang sama.

### 2. Hasil Proyek berdasarkan metrik evaluasi.
*Precision dihitung dengan rumus:*
$$
\text{Precision (P)} = \frac{\text{Jumlah rekomendasi yang relevan}}{\text{Jumlah total rekomendasi yang diberikan}}
$$

Artinya, precision mengukur seberapa banyak dari obat-obat yang direkomendasikan oleh sistem benar-benar relevan atau bermanfaat bagi pengguna. Nilai precision yang tinggi menunjukkan bahwa sebagian besar rekomendasi sistem memang sesuai dan berguna, sedangkan precision yang rendah mengindikasikan bahwa sistem memberikan banyak rekomendasi yang tidak relevan.

### 3. Kesesuaian Metrik dengan Konteks Proyek
* Kecocokan dengan konteks data*
Metrik evaluasi yang digunakan dalam sistem ini sangat selaras dengan karakteristik data yang digunakan. Data yang dianalisis berupa ulasan berbasis teks dari pengguna obat, yang mencerminkan pengalaman pribadi mereka dalam menggunakan suatu produk farmasi. Oleh karena itu, penggunaan metrik seperti cosine similarity menjadi tepat karena mampu menangkap kedekatan makna antar ulasan dalam bentuk representasi vektor. Ini memungkinkan sistem untuk memahami dan mengukur kemiripan konteks antara satu ulasan dengan yang lain secara efektif.
*Kesesuaian dengan problem statement*
metrik evaluasi yang diterapkan juga sesuai dengan problem statement yang telah ditetapkan. Dalam proyek ini, tantangan utamanya adalah bagaimana membantu pasien yang seringkali kesulitan menemukan obat yang tepat berdasarkan pengalaman orang lain. Dengan mengukur relevansi antar ulasan dan mencocokkannya berdasarkan kondisi medis yang sama, sistem dapat memberikan rekomendasi yang tidak hanya mirip secara teks, tetapi juga relevan dengan kebutuhan medis pengguna.
*Solusi yang diharapkan*
Akhirnya, metrik evaluasi ini juga mendukung pencapaian solusi yang diinginkan, yaitu menghasilkan rekomendasi obat yang sesuai secara kontekstual dengan isi ulasan dan kebutuhan pengguna. Sistem tidak hanya memberikan alternatif obat yang secara statistik mirip, tetapi juga mempertimbangkan apakah obat tersebut benar-benar digunakan dan dinilai bermanfaat oleh pasien dengan kondisi serupa. Hal ini menjadikan sistem lebih personal, informatif, dan bermanfaat bagi pengguna yang membutuhkan panduan berbasis pengalaman nyata.

[sdfghjop987654ewsdfghj] (https://github.com/Yhyabnu/image/blob/e51ffff9969e15bb92c405da78e0d6ad770d0c7d/cosine.png)