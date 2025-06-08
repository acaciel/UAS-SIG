# Prediksi Kerawanan Banjir Demak

Proyek ini melakukan analisis dan pemodelan prediksi kerawanan banjir di wilayah Kabupaten Demak menggunakan pendekatan Machine Learning dan data geospasial.

## Deskripsi

Proyek ini mengembangkan sebuah model prediktif untuk mengidentifikasi area-area dengan probabilitas banjir yang tinggi di Kabupaten Demak. Model ini mempertimbangkan berbagai faktor bio-fisik dan lingkungan, seperti:

* Data ketinggian wilayah
* Data kemiringan lereng
* Data curah hujan tahunan
* Data penggunaan lahan (Sawah, Pemukiman, dll.)
* Data historis kejadian banjir

## Data yang Digunakan

Proyek ini menggunakan beberapa set, yaitu:

* **Data Fisik & Geografis**
    * `data_fisik_lokasi_demak.csv`: Berisi data koordinat (latitude, longitude), ketinggian wilayah dalam meter, dan kemiringan lereng dalam derajat.

* **Data Penggunaan Lahan**
    * `data_penggunaan_lahan_demak.csv`: Berisi klasifikasi tutupan lahan pada setiap titik lokasi, seperti 'Sawah Irigasi', 'Pemukiman Padat', 'Tambak', dll.

* **Data Iklim**
    * `data_curah_hujan_demak.csv`: Berisi data simulasi rata-rata curah hujan tahunan dalam milimeter (mm) untuk setiap lokasi.

* **Data Kejadian Bencana**
    * `data_historis_banjir_demak.csv`: Berisi catatan koordinat lokasi yang pernah mengalami kejadian banjir, digunakan sebagai data target untuk melatih model.

## Hasil dan Analisis

### Kinerja Model
Dengan menggunakan metode pembuatan data yang lebih stabil, model yang dilatih menunjukkan kinerja yang sangat baik dan sesuai dengan target, dengan akurasi keseluruhan mencapai **96%**.

**Classification Report:**
```text
              precision    recall  f1-score   support

           0       0.97      0.99      0.98       160
           1       0.95      0.88      0.91        40

    accuracy                           0.96       200
   macro avg       0.96      0.93      0.94       200
weighted avg       0.96      0.96      0.96       200
```
> **Interpretasi:** Model ini sangat andal dalam mengidentifikasi area aman (precision 97%, recall 99%) dan memiliki kemampuan yang kuat untuk mendeteksi area rawan banjir (precision 95%, recall 88%). `weighted avg f1-score` sebesar 96% menunjukkan performa model yang sangat memuaskan.

### Analisis Faktor Penting
Analisis `feature importance` menunjukkan bahwa faktor-faktor berikut memiliki pengaruh terbesar dalam prediksi:
1.  **Ketinggian Wilayah (`ketinggian_m`)**
2.  **Curah Hujan Tahunan (`rata_curah_hujan_mm`)**
3.  **Penggunaan Lahan: Pemukiman Padat (`lahan_Pemukiman Padat`)**
4.  **Kemiringan Lereng (`kemiringan_derajat`)**

## Output

Proyek ini menghasilkan dua output utama:
* Model prediksi banjir yang telah dilatih menggunakan algoritma **Random Forest Classifier**.
* Visualisasi peta `peta_prediksi_banjir_demak.html` yang menampilkan probabilitas kerawanan banjir untuk seluruh wilayah studi.

## Penggunaan

Proyek ini dikembangkan dalam format Google Colab Notebook. Untuk menjalankan ulang analisis dan prediksi, ikuti langkah berikut:

1.  Buka file `Prediksi_Banjir_Demak.ipynb` menggunakan Google Colab.
2.  Unduh 4 file dataset yang diperlukan yang sudah tersedia di repositori.
3.  Jalankan sel pertama dan unggah 4 file dataset yang sudah diunduh.
4.  Jalankan semua sel berikutnya secara berurutan untuk melakukan pre-processing, training model, evaluasi, dan pembuatan peta.
5.  Di akhir proses, file peta `peta_prediksi_banjir_demak.html` akan secara otomatis terunduh ke device.
