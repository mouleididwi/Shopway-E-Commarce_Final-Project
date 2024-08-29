# 🛒 **Unlocking Online Shopper Behavior** 🛒
---
## 📂 **Stage 0 : Problem Statement**
### Problem Statement
- E-commerce didefinisikan sebagai tempat terjadinya transaksi atau pertukaran informasi antara penjual dan pembeli di dunia maya, tanpa harus berada dalam satu tempat atau ruang tertentu. E-commerce juga memberikan manfaat yang dapat dirasakan oleh konsumen secara langsung, yaitu menghemat waktu serta tidak ada batasan jarak. Adapun Indikator dari E-Commerce yaitu tingkat kepercayaan, harga, dan informasi.

- Dalam praktiknya, persaingan industri e-commerce sangat ketat sehingga perusahaan e-commerce bersaing dalam menawarkan beberapa jenis promosi yang mampu menarik perhatian konsumen, seperti gratis ongkir seluruh wilayah, voucher cashback, paket diskon, dan flash sale. Selain itu perusahaan e-commerce bersaing dalam pengembangan website untuk kenyamanan pengguna Hal-hal tersebut sangat mempengaruhi perilaku konsumen dalam mengambil keputusan pembelian. Menurut peneliti, Konsumen merupakan tonggak dari keberhasilan penjual atau pelaku bisnis ecommerce yang menginginkan keuntungan dalam jalannya usaha.

- Sebagai konsultan perusahaan e-commerce yang telah memiliki data pembelian online, kami akan menggunakan data tersebut untuk meningkatkan performa perusahaan dengan cara membangun sebuah model yang dapat memprediksi pengunjung untuk melakukan transaksi pada situs website suatu e-commerce. Hasil prediksi yang tepat dapat digunakan dalam strategi pemasaran suatu produk tertentu sehingga dapat meningkatkan revenue perusahaan.

- Berdasarkan data, dari 12.946 pengguna e-commerce hanya 15.5% yang menghasilkan revenue. Bagaimana cara meningkatkan revenue perusahaan ?


### Goals
- Meningkatkan CVR dengan menargetkan pemasaran pada pelanggan yang berpeluang tinggi untuk membeli.


### Objectives
- Membuat model prediktif untuk memprediksi pengunjung melakukan transaksi di e-commerce.
- Menganalisis faktor-faktor yang mempengaruhi pengunjung melakukan transaksi

### Business Matrics
-  Conversion Rate (Revenue)
<br>

---

## 📂 **Stage 1 : Exploratory Data Analysis**
### Dataset
<p align="center">
  Tabel 1 – Informasi Data <br>
</p>

<p align="center">
  <img src="https://github.com/Juliana9417/Final_Project/assets/172182011/ac551e0f-ec91-4a4a-b7f9-7ae2e1e75501" alt="InformasiData">
</p>

### Descriptive Statistics

<p align="center">
  Tabel 2  – Data Deskriptif Numerikal
</p>

<p align="center">
  <img src="https://github.com/Juliana9417/Final_Project/assets/172182011/8ad6a165-887d-40c2-acbe-42c5c2f50042" alt="DataDeskritiveNumerik">
</p>

<br>

<p align="center">
   Tabel 3  – Data Deskriptive Kategori
</p> 

<p align="center">
  <img src="https://github.com/Juliana9417/Final_Project/assets/172182011/be4758d7-f873-4a03-a39d-08743f801e8f" alt="DataDeskritiveKategori">
</p>

<br>

### Insight Data Deskriptif : 

1. Jumlah pengunjung web tertinggi pada bulan Mei
2. Pelanggan mayoritas adalah Returning_Visitor sebanyak 85.5%
3. kunjungan pelanggan mayoritas diluar weekend 
4. Dari 12946 data, sebanyak 10938 atau 85.5% tidak melakukan pembelian sisanya 2008 atau 15.5% yang melakukan pembelian  
5. Sistem operaasi yang banyak digunakan oleh pengunjung yaitu sistem operasi 2
6. Browser yang banyak digunakan oleh pengunjung yaitu browser 2
7. Region pengunjung banyak berasal dari region 1
8. Traffic type pengunjung terbanyak yaitu traffic type 2 <br>
<br>

### Kesimpulan Data Deskriptif :

1. Terdapat beberapa kolom dengan nilai null yang lebih dari 1-2% (Administrative_Duration, ProductRelated_Duration, OperatingSystems) handling missing value, dan yang <2% akan dilakukan drop data (Administrative, Administrative)
Semua kolom numerik skew (dilihat dari perbedaan antara mean > median)
2. Tidak ada kolom kategori yang perlu didrop karena hanya punya 1 nilai unik atau punya nilai unik sebanyak jumlah baris
<br>

### Univariate Analisis : 
<p align="center">
  
![DisplotNumerikal](https://github.com/Juliana9417/Final_Project/assets/172182011/406d8ad1-c3f7-4946-9328-dd0ea767e99e)

  Gambar 1 – Displot Numerikal 
</p>
<br>
### Insight : 
- Semua kolom cenderung berbentuk positive skewed, dan distribusi data mendekati nilai 0.
- Kolom ‘Informational’ dan ExitRates’ berbentuk Multimodal.
- Kolom ‘BounceRates’ berbentuk Bimodal.
<br>

<p align="center">

![ViolinMunerikal](https://github.com/Juliana9417/Final_Project/assets/172182011/0c32e267-eb43-465d-8300-b6f0dd293f81)

  Gambar 2 – Violin Numerikal 
</p>
<br>
### Insight : 
- Distribusi data cenderung menumpuk ekstrim mendekati nilai 0.00 pada kolom : 
- Administrative, Administrative_Duration, Informational, Informational_Duration, ProductRelated, ProductRelated_Duration, BounceRates, dan PageValues.
- Sementara, pada kolom ‘ExitRates’ distribusi data menumpuk di antara 0.00 - 0.05.
<br>


### Multivariate Analisis : 
<p align="center">
  
![MultivariateNumerikal](https://github.com/Juliana9417/Final_Project/assets/172182011/eaf5da5b-d8f9-446f-834e-5431af3d9bec)
 
  Gambar 3 – Multivariate Numerikal 
</p>
<br>
### Insight : 
-Deteksi kemungkinan moderate redundant features (nilai korelasi tinggi >= 0.6).
1. ‘Administrative’ dan ‘Administrative_Duration’
2. ‘Informational’ dan ‘Informational_Duration’

-Deteksi kemungkinan highly redundant features (nilai korelasi tinggi > 0.7).
1. ‘ProductRelated’ dan ‘ProductRelated_Duration’
2. ‘BounceRates’ dan ‘ExitRates’

- Kolom yang berpotensi redundant, kemungkinan akan di hapus salah satu pada tahap Data Processing.
- Korelasi target ‘Revanue' memiliki korelasi positif kuat dengan fitur ‘PageValues’ (0.50).
<br>
<br>
<p align="center">

  ![MultivariateKategorikal](https://github.com/Juliana9417/Final_Project/assets/172182011/3300d7f4-e99b-41e6-a9ab-ee9ef80114c5)

  Gambar 4 – Multivariate Kategorikal
</p>
<br>
### Insight : <br>
- Korelasi yang cukup kuat antar kolom: <br>
1. ‘VisitorType’ dan ‘OperatingSystems’ 
2. ‘VisitorType’ dan ‘Browser’
3. ‘VisitorType’ dan ‘TrafficType’

- Deteksi kemungkinan moderate redundant features (nilai korelasi tinggi >= 0.6) pada ‘OperatingSystems’ dan ‘Browser’
- Fitur-fitur yang lainnya memiliki korelasi yang cukup rendah.
- Korelasi target ‘Revenue’ dangan semua fitur kategorikal memiliki korelasi positive (walaupun sangat lemah), dengan nilai korelasi fitur ‘Month’ paling tinggi (0,18).
<br>

### Bi-Variate Analisis : 

<p align="center">

 ![Visitortype](https://github.com/Juliana9417/Final_Project/assets/172182011/df78f66a-42c2-4141-bb9f-a64523f1fdf5)

  Gambar 5 – Visitor Type Vs Revenue
</p>
<br>
### Insight <br>
- Terdapat tiga jenis visitor : <br>
1. Jumlah "Returning visitor" paling banyak, namun persentase pengunjung yang menghasilkan revenue paling sedikit dibanding dua jenis lainnya.
2. Pengunjung "New Visitor" lebih sedikit daripada "Returning visitor", namun memiliki persentase pendapatan tertinggi dibanding dua jenis lainnya, yaitu 24.65%.
3. Pengunjung "Other" memiliki persentase pendapatan sebesar 17.98%, lebih rendah dari "New Visitor" tetapi lebih tinggi dari "Returning visitor".
<br>
<br>
<p align="center">

  ![Month](https://github.com/Juliana9417/Final_Project/assets/172182011/ee64fe96-e4fd-4879-8238-756c539a5604)

  Gambar 6 – Month Vs Revenue
</p>
<br>
### Insight <br>
1. Bulan November memiliki jumlah revenue tertinggi (803) di antara semua bulan.
2. Bulan-bulan dengan jumlah revenue yang signifikan tinggi lainnya adalah Mei (379) dan Maret (201).
3. Februari memiliki jumlah revenue yang paling rendah (3), menunjukkan bahwa ini adalah bulan dengan performa paling rendah dalam hal pendapatan.
<br>
<br>
<p align="center">

  ![Region](https://github.com/Juliana9417/Final_Project/assets/172182011/74032eb8-7e71-42d1-862e-11f0b3751e2f)

  Gambar 7 – Visitor per Region Vs Revenue
</p>
<br>
### Insight <br>
1. Wilayah 2 memiliki persentase pendapatan tertinggi (16.64%), diikuti oleh Wilayah 9 (16.54%), dan Wilayah 5 (16.32%).
<br>
<br>
<p align="center">

  ![Weekend](https://github.com/Juliana9417/Final_Project/assets/172182011/cdc11647-39c0-4789-8450-7131ec004786)

  Gambar 8 – Weekend Vs Revenue
</p>
<br>
### Insight <br>
1. Persentase pengunjung yang menghasilkan pendapatan lebih tinggi pada akhir pekan (17.50%) dibandingkan dengan hari biasa (14.91%).
2. Grafik menunjukkan meskipun jumlah pengunjung lebih rendah pada akhir pekan, potensi pengunjung melakukan transaksi lebih besar dibandingkan hari biasa.
<br>
<br>
<p align="center">

![ProductRelated](https://github.com/Juliana9417/Final_Project/assets/172182011/c074167e-426a-49b8-b420-bc10f423fb2e)

  Gambar 9 – Product Related, Administrative, Informational Vs Revenue
</p>
<br>
### Insight <br>
1. Interaksi pengunjung dengan halaman terkait produk (Product Related) merupakan faktor paling penting dalam mendorong pembelian.
<br>


---

### Business Recomendation <br>
1. Fokus pada Pengunjung Baru (New Visitor).Meskipun jumlah pengunjung yang kembali (Returning Visitor) mungkin lebih banyak, namun persentase pendapatan yang dihasilkan oleh pengunjung baru (New Visitor) lebih tinggi. Oleh karena itu, proporsi strategi pemasaran dapat dilakukan untuk new visitor lebih besar dibandingkan dengan returning visitor dan tetap memperhatikan pengalaman pengunjung baru untuk meningkatkan konversi.

2. Meningkatkan strategi pemasaran dan promosi selama bulan-bulan dengan performa tinggi seperti November, Mei, dan Maret. Fokus pada memanfaatkan momentum penjualan yang kuat pada bulan-bulan ini dapat membantu meningkatkan pendapatan secara keseluruhan. Sebaliknya, bulan Februari memerlukan evaluasi lebih lanjut untuk memahami faktor-faktor yang mengakibatkan performa pendapatan yang rendah, mungkin dengan memperkuat strategi promosi untuk menggerakkan penjualan di periode ini.

3. Perhatikan Hari Khusus (Special Day). Mkipun mayoritas transaksi terjadi pada hari biasa, penting untuk tetap memperhatikan hari khusus (Special Day), terutama pada bulan Februari dan Mei, di mana ada banyak hari khusus. Ini bisa menjadi peluang untuk menawarkan penawaran khusus atau promosi untuk menarik lebih banyak konversi.

4. Fokus pada Optimalisasi Halaman Terkait Produk. Karena ata-rata pembeli melakukan kunjungan ke halaman terkait produk lebih banyak dibandingkan halaman lainnya, bisnis harus memastikan halaman ini dioptimalkan dengan baik. Hal ini termasuk memastikan kecepatan halaman yang cepat, desain yang menarik, dan informasi yang relevan serta jelas.

5. Eksplorasi Potensi Akhir Pekan (Weekend).Meskipun jumlah pengunjung mungkin lebih rendah pada akhir pekan, namun persentase transaksi ini menghasilkan pendapatan lebih tinggi. Ini menunjukkan bahwa ada potensi yang belum dimanfaatkan pada akhir pekan, dan bisnis dapat mempertimbangkan untuk mengembangkan strategi pemasaran atau promosi khusus untuk menarik lebih banyak konversi selama periode ini.

6. Region 1, 3, dan 2 memiliki jumlah total dan jumlah pendapatan tertinggi. Alokasikan lebih banyak sumber daya seperti kampanye pemasaran, promosi yang dipersonalisasi, dan dukungan pelanggan ke region tersebut untuk memanfaatkan potensi pendapatan yang lebih tinggi.

7. Traffic type 2 memiliki jumlah pengunjung terbanyak tetapi konversinya rendah. erlu mengalokasikan sumberdaya untuk meningkatkan konversi salah satu contohnya seperti promosi/diskon.
<br>

## 📂 **Stage 2 : Data Pre-Processing**
<br>
1. Missing Value
    Drop semua missing values dengan .dropna()
    
![missing value](https://github.com/user-attachments/assets/d9989fa8-ff50-442d-8698-69e14788c12a)

   <p align="center">
     Gambar 10 - Handling missing values <br>
   </p>
<br>
<br>
2. Duplicated Data
    Drop semua data duplikat dengan .drop_duplicates()
       
![drop duplikat](https://github.com/user-attachments/assets/8343acf6-c640-49ed-af1c-79c0f51b0258)

   <p align="center">
     Gambar 11 - Handling duplikat <br>
   </p>
<br>
<br>
4. Handling Outliers
    Tidak dilakukan handling outlier karena cukup banyak kehilangan data dari outliers handling menggunakan z-score dan IQR, hal ini kemungkinan karena banyak data yang 0. Outliers tidak bisa langsung di-drop karena data tersebut kemungkinan mewakili populasi tertentu.
<br>
<br>
5. Feature Transformation
    Transformasi data dilakukan setelah pemilihan fitur dan pemisahan data menggunakan robust scaller agar model lebih robust terhadap outliers.
<br>
<br>
6. Feature Encoding
      
![encoding](https://github.com/user-attachments/assets/214a3602-02a7-4038-b1c9-a6977dfed28c)

   <p align="center">
     Gambar 12 - Feature Encoding <br>
   </p>
<br>
  - Label encoding untuk fetaure 'Month', 'Revenue', dan 'Weekend' <br>
  - One-hot encoding untuk feature 'VisitorType', kemudian VisitorType_isOther hasil one hot dihapus untuk menghindari multikolinearitas pada modelling.<br>
  - Untuk features : Browser, Region, TrafficType dan SpecialDay tidak dilakukan feature encoding (label encoder/one hot) diasumsikan feature tersebut sudah bernilai ordinal.<br>


### **Feature Engineering**

1. Feature Extraction<br>
   A. Feature Tambahan untuk modelling

![extraction](https://github.com/user-attachments/assets/a91b229e-2008-4a6a-ae1f-a7db45d8b9e8)

   <p align="center">
     Gambar 13 - Feature Engineering <br>
   </p>
<br>

- **Session_Duration**
  - **Definisi:** Total waktu yang dihabiskan pengguna untuk berinteraksi dengan halaman-halaman selama satu sesi.
  - **Alasan Memilih Fitur:** Durasi sesi yang lebih lama bisa menunjukkan minat dan keterlibatan tinggi, berpotensi untuk konversi. Penting untuk meningkatkan prediksi konversi pengunjung web.

- **Page_Count**
  - **Definisi:** Jumlah total halaman (Administratif, Informasional, ProductRelated) yang diakses pengguna selama satu sesi.
  - **Alasan Memilih Fitur:** Jumlah halaman yang banyak menunjukkan eksplorasi mendalam terhadap situs, bisa menjadi indikator kuat minat dan niat untuk konversi. Membantu model prediksi mengenali perilaku pengguna yang cenderung melakukan konversi.

- **Avg_Duration_Per_Page**
  - **Definisi:** Rata-rata waktu yang dihabiskan pada setiap halaman selama satu sesi.
  - **Alasan Memilih Fitur:** Durasi rata-rata per halaman memberi gambaran tentang intensitas interaksi pengguna dengan konten di setiap halaman. Pengguna yang menghabiskan waktu lebih lama di setiap halaman mungkin lebih tertarik dan cenderung untuk konversi. Meningkatkan kemampuan model prediksi mengidentifikasi pengguna berpotensi tinggi untuk konversi.
<br>

2. Feature tambahan (selain dari dataset) :
    - Waktu Kunjungan Terakhir (Time Since Last Visit)
      Definisi: Selang waktu antara kunjungan terakhir pengguna dan kunjungan saat ini. <br>
      Alasan: Pengguna yang baru saja mengunjungi situs web mungkin lebih cenderung untuk melakukan konversi karena situs tersebut masih segar dalam ingatan mereka.
   - Rata-rata Nilai Transaksi Sebelumnya (Average Previous Transaction Value)
     Definisi: Rata-rata nilai transaksi dari kunjungan sebelumnya untuk pengguna yang telah melakukan pembelian sebelumnya. <br>
     Alasan: Pengguna yang memiliki riwayat transaksi dengan nilai tinggi mungkin memiliki probabilitas konversi yang lebih tinggi, serta cenderung melakukan pembelian dengan nilai yang lebih tinggi di masa depan.
   - Jumlah Item dalam Keranjang (Number of Items in Cart)
     Definisi: Jumlah item yang ditambahkan ke keranjang belanja oleh pengguna selama sesi saat ini.<br>
     Alasan: Pengguna yang menambahkan banyak item ke keranjang belanja mungkin menunjukkan niat yang lebih tinggi untuk melakukan pembelian.
   - Metode Pembayaran yang Disukai (Preferred Payment Method)
     Definisi: Metode pembayaran yang paling sering digunakan oleh pengguna (misalnya, kartu kredit, PayPal, dll).<br>
     Alasan: Pengguna dengan metode pembayaran yang jelas mungkin lebih cenderung untuk melakukan konversi karena mereka merasa nyaman dengan proses pembayaran.
   - Tanggal Sesi (Session Date)
     Definisi: Tanggal di mana sesi pengguna terjadi.<br>
     Alasan: Tanggal yang bertepatan dengan periode setelah penerimaan gaji dapat meningkatkan kemungkinan konversi, karena pengguna cenderung memiliki ketersediaan dana yang lebih tinggi untuk melakukan pembelian.<br>
  
  
### **Feature Selection**
  1. Fitur kategorikal - target

![chi2](https://github.com/user-attachments/assets/1469dd79-94cc-43c7-9758-0e1836ac79a1)

   <p align="center">
     Gambar 14 - Chi2 Test <br>
   </p>
   
<br>
Berdasarkan Uji Chi-square dipilih 3 feature yang memiliki nilai korelasi tertinggi yaitu : Month_encoded, VisitorType_isNew_Visitor, SpecialDay <br> 
<br>

  2. Fitur numerikal - target
    
![anova](https://github.com/user-attachments/assets/3ff3d484-ebf5-4822-b22d-4e16d36c32c8)

   </p>
   <p align="center">
     Gambar 15 - Annova Test <br>
   </p>
   
<br>
Berdasarkan Uji Annova dipilih 3 feature yang memiliki nilai korelasi tertinggi yaitu :  PageValues, ExitRates, Page_Count.<br> 

### **Splitting Data Train dan Test**
Pemisahan dataset train dan test dengan proporsi **70 : 30**.

### **Handling Class Imbalance**

![imbalance class](https://github.com/user-attachments/assets/2158dab4-fb73-4cdc-b24e-fd258dec510c)
   
   <p align="center">
     Gambar 16 - Class Imbalance <br>
   </p>
<br>
    
![resampling](https://github.com/user-attachments/assets/ff35f7fb-34fa-406d-9ae8-25f884382c0f)

   <p align="center">
     Gambar 17 - Sampling Methods <br>
   </p>
<br>
    SMOTE adalah pilihan yang tepat dalam klasifikasi model dengan ketidakseimbangan kelas yang signifikan, seperti pada dataset ini. Dengan menciptakan sampel sintetis dari kelas minoritas, SMOTE secara efektif meningkatkan representasi data minoritas dalam dataset, yang memungkinkan model untuk belajar pola yang lebih baik dari kelas minoritas. Ini tidak hanya mengurangi risiko overfitting dengan memperluas variasi data minoritas, tetapi juga meningkatkan akurasi prediksi pada kelas minoritas.

## 📂 **Stage 3 : Modelling**

**Recall (cross validation)** digunakan sebagai matrix evaluasi dengan fokus terhadap nilai **False Negative** dalam membandingkan performa antar algoritma model klasifikasi mechine learning (Supervised Learning). <br>

Menurut Powers, **recall (sensitivitas atau true positive rate)** merupakan metrik evaluasi yang penting, terutama dalam kasus di mana deteksi positif benar (**true positives**) lebih kritis dibandingkan dengan deteksi negatif salah (false negatives). Powers juga menjelaskan bahwa kesalahan tipe II (**false negatives**) memiliki konsekuensi yang lebih serius dibandingkan dengan kesalahan tipe I (false positives). <br>

**Cross-validation** digunakan sebagai teknik evaluasi recall dari model machine learning untuk memastikan model tidak hanya dioptimalkan untuk dataset tertentu, tetapi memiliki generalisasi yang baik pada dataset lainnya (Caruana & Niculescu-Mizil, 2006). <br>

Kasus dalam dataset ini dimana perusahaan ingin meningkatkan revenue. Maka dari itu, recall (cross validation) menjadi fokus utama untuk menghindari model gagal mengidentifikasi pelanggan yang benar-benar menghasilkan revenue. Dengan nilai false negatives rendah, diharapkan lebih banyak peluang revenue yang tidak terlewatkan oleh perusahaan. Model dengan nilai recall (cross validation) mendekati 1 menunjukkan performa yang lebih baik dalam mendeteksi semua kejadian positif. <br>

### **Logistic Regression : Modeling and Evaluation**

Setelah uji coba beberapa algoritma model klasifikasi yaitu Logistic Regression, Decission Tree, Random Forest, AdaBoost, dan XGBoost. Model algoritma **Logistic Regression** dengan Hyperparameter Tuning dipilih karena menunjukkan performa terbaik. Dengan mempertimbangkan recall yang tinggi dan hasil cross-validation yang baik, Logistic Regression memberikan keseimbangan optimal antara deteksi kasus positif dan penghindaran dari false negatives, sehingga mendukung tujuan akhir peningkatan revenue secara efektif.<br>

Berikut hasil evaluasi dari prediksi model Logistic Regression setelah dilakukan Hyperparameter Tuning.
<p align="center">
  <img src="https://github.com/user-attachments/assets/637a0ed5-5f1a-40bf-bf42-37825c5120b7">
   </p>
<p align="center">
  Gambar 18 – Hasil Evaluasi Matriks Logistic Regression dengan Hyperparameter Tuning  <br>

Nilai Recall (cross-validation) dari model Logistic Regression dengan Hyperparameter Tuning pada train sekitar 0.83 dan test 0.81 yang berarti model memiliki performa yang sudah cukup baik.
<p align="center">
  <img src="https://github.com/user-attachments/assets/58c460d5-4508-4ca4-b57d-2fdf50db6a74">
   </p>  
<p align="center">
  Gambar 19 – Confussion Matrix Logistic Regression dengan Hyperparameter Tuning <br>
<br>
</p>
best_model (Logistic Regression dengan Hyperparameter Tuning terbaik) lebih moderat dan lebih seimbang dalam hal recall dengan ukuran/metrik evaluasi lainnya. Dalam konteks bisnis, model ini merupakan pilihan yang lebih baik karena tetap menjaga keseimbangan antara revenue (tujuan utama) dan cost (bukan tujuan utama namun perlu dipertimbangkan juga).

### **Logistic Regression : Feature Importances**
Langkah berikutnya dilakukan pengukuran pengaruh fitur terhadap model berdasarkan nilai absolut dari koefisien fitur dalam model. Dengan kata lain, fitur dengan koefisien yang lebih besar (baik positif maupun negatif) dianggap lebih penting, karena perubahan dalam fitur tersebut akan berdampak lebih signifikan terhadap output model. <br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/acf3cae7-a1a1-4bc3-896b-03279affef92">
   </p>  
<p align="center">
  Gambar 20 – Feature Importances by the absolute value of their coefficients <br>
<br>

Fitur PageValues memiliki koefisien positif (0.02854369)menunjukkan bahwa PageValues berdampak positif terhadap target variabel, tetapi pengaruhnya tidak besar.<br>
Fitur lainnya (Month_encoded, VisitorType_isNew_Visitor, SpecialDay, dan Page_Count) memiliki koefisien 0, menunjukkan bahwa fitur fitur tsb tidak berpengaruh signifikan dalam model ini.
<br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/1beee733-23fb-40db-becd-e8c386b46a0c">
   </p>  
<p align="center">
  Gambar 21 – Feature Importances by the SHAP value (impact on model output) <br>
<br>
  
PageValues memiliki nilai SHAP yang tinggi, berarti fitur ini memiliki pengaruh besar pada prediksi model. Nilai SHAP untuk PageValues cenderung positif yang artinya peningkatan PageValues berdampak pada peningkatan variabel target.
<br>
Fitur lainnya (Month_encoded, VisitorType_isNew_Visitor, SpecialDay, dan Page_Count) memiliki nilai SHAP rendah yang menunjukkan bahwa fitur-fitur tersebut tidak berpengaruh signifikan dalam model ini.

**Business Insight :** <br>
1. Pentingnya Pengalaman Pengguna: <br>
'Page values' yang tinggi menunjukkan bahwa pengunjung yang terlibat secara aktif dengan halaman-halaman situs cenderung lebih mungkin untuk membeli. Ini menekankan pentingnya pengalaman pengguna yang baik dan menarik untuk meningkatkan kemungkinan konversi.<br>
2. Relevansi Konten: <br>
Halaman-halaman dengan 'page values' tinggi mungkin memiliki konten yang lebih relevan dan informatif bagi pengunjung. Konten ini dapat mencakup deskripsi produk yang jelas, testimoni pelanggan, ulasan produk, dan informasi lain yang membantu pengunjung membuat keputusan pembelian. <br>
3. Perilaku Pembelian: <br>
Insight ini menunjukkan bahwa pengunjung yang lebih terlibat dengan konten situs web cenderung lebih cenderung untuk membeli. Ini bisa mencerminkan tahap perjalanan pembelian pengunjung dan faktor-faktor psikologis yang mempengaruhi keputusan pembelian. <br>

**Rekomendasi Bisnis :**
<br>
1. Optimalkan Halaman Produk: <br>
Pastikan deskripsi produk, gambar, dan ulasan pelanggan disajikan dengan baik dan mudah diakses. Gunakan tata letak yang menarik dan intuitif untuk meningkatkan 'page values'. <br>
2. Personalisasi Konten:<br>
Gunakan data pengunjung untuk menyesuaikan rekomendasi produk dan konten yang ditampilkan di halaman. Personalisasi dapat membantu meningkatkan relevansi konten dan minat pengunjung. <br>
3. Uji A/B dan Analisis:<br>
Lakukan uji A/B untuk halaman-halaman kunci dan analisis lanjutan terhadap data 'page values' untuk memahami faktor apa yang paling mempengaruhi konversi. Ini dapat membantu mengidentifikasi perbaikan yang dapat dilakukan dengan cepat. <br>
4. Peningkatan Pengalaman Pengguna: <br>
Fokus pada pengalaman pengguna yang responsif dan intuitif. Pastikan situs web mudah dinavigasi, cepat dimuat, dan menawarkan pengalaman yang menyenangkan bagi pengunjung. <br>
5. Monitoring dan Optimasi Terus-menerus: <br>
Terus pantau metrik 'page values' dan konversi untuk melihat bagaimana perubahan yang diterapkan memengaruhi perilaku pengunjung. Optimalkan strategi berdasarkan temuan dari analisis ini secara berkala.

<br>

---

#### Sumber
Caruana, R. & Niculescu-Mizil, A., 2006. An empirical comparison of supervised learning algorithms. Proceedings of the 23rd International Conference on Machine Learning, pp.161-168. doi: 10.1145/1143844.1143865. <br>
Powers, D. M., 2011. Evaluation: From Precision, Recall and F-Measure to ROC, Informedness, Markedness & Correlation. [online] Available at: https://doi.org/10.48550/arXiv.2010.16061 [Accessed 16 July 2024].
