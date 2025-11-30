🏆 **Data Science Competition 2025 – Tim ThreeVolution**

**Peringkat 7 dari 70 Tim**
Diselenggarakan oleh **UPN Veteran Jawa Timur (Online)**

Anggota tim:

* **Dalila Tazkia**
* **Jihan Aqilah**
* **Asri Sabilla Putri**

Notebook ini memuat seluruh alur analisis data dan permodelan yang digunakan dalam kompetisi.

---

# 📂 **Struktur Project**

```
DSC2025_ThreeVolution.ipynb   → Notebook utama
products.csv                 → Dataset master produk
sales.csv                    → Dataset transaksi penjualan
marketing.csv                → Dataset aktivitas marketing
reviews.csv                  → Dataset ulasan
```

---

# 🎯 **Tujuan Analisis**

Notebook ini dikembangkan untuk:

* Membersihkan & memproses 4 dataset besar (products, sales, marketing, reviews)
* Menggabungkan ke satu dataset analitis
* Melakukan EDA mendalam (distribusi, korelasi, missing values, outliers)
* Melakukan feature engineering (efektif harga, skor review, agregasi mingguan/bulanan)
* Melakukan forecasting penjualan menggunakan:

  * **ARIMA (per brand)**
  * **VAR (Vector AutoRegression)**
* Uji **Granger Causality** untuk melihat hubungan antar merek
* Evaluasi menggunakan **RMSE, MAPE, dan MASE**

---

# 🧹 **Tahap 1 — Data Preprocessing**

Notebook memuat preprocessing lengkap:

### **Products**

* Konversi `launch_date` → datetime
* Pemeriksaan missing & duplicated
* Penanganan outlier numerik menggunakan **winsorizing**
* Visualisasi missing values menggunakan heatmap

### **Sales**

* Penggabungan date + product_id
* Pembuatan kolom:

  * `discount_value`
  * `effective_price`
  * `revenue`
  * `log_units_sold`
* Resampling mingguan & bulanan

### **Marketing**

* Normalisasi pengukuran marketing
* Merge ke dataset sales

### **Reviews**

* Pembuatan skor review agregat per produk
* Join ke dataset akhir

---

# 📊 **Exploratory Data Analysis (EDA)**

Analisis meliputi:

* Distribusi produk per kategori
* Trend penjualan mingguan & bulanan
* Korelasi numerik (heatmap)
* Performansi brand berdasarkan:

  * revenue
  * effective_price
  * units_sold
* Visualisasi time-series tiap brand

---

# 🔧 **Tahap 2 — Feature Engineering**

Dilakukan beberapa teknik:

* Log transformation (`log_units_sold`)
* Handling imbalance menggunakan **SMOTE** (untuk data klasifikasi)
* Merging multi-dataset menjadi **sales2**
* Resampling:

  * Weekly time series
  * Monthly aggregated brand performance
* Pembuatan dataset panel time-series

---

# 📈 **Tahap 3 — Time Series Forecasting**

Notebook menggunakan dua jenis pendekatan:

---

## **1️⃣ ARIMA (per brand)**

Untuk setiap brand, dilakukan:

* Uji stasioneritas (ADF test)
* Differencing jika diperlukan
* Training ARIMA model
* Forecasting **6 periode ke depan**
* Evaluasi per brand:

  * **RMSE**
  * **MAPE**
  * **MASE**

Hasil akhir dirangkum dalam bentuk tabel performa model.

---

## **2️⃣ VAR (Vector AutoRegression)**

Digunakan untuk melihat interaksi antar brand:

* Seleksi lag menggunakan AIC
* Training VAR model
* Impulse Response Function (IRF)
* Forecasting multi-brand secara simultan

---

## **3️⃣ Granger Causality Test**

Dilakukan untuk mengetahui:

> Brand mana yang *mempengaruhi* brand lain dalam jangka pendek.

Notebook menghasilkan:

* Tabel hasil Granger Test
* Daftar hubungan signifikan berdasarkan p-value

---

# 🧪 **Evaluasi Model**

Notebook menampilkan tabel akurasi berisi:

* RMSE
* MAPE
* MASE

Serta visualisasi:

* Actual vs Fitted
* Forecast plots per brand

---

# 🚀 **Cara Menjalankan**

## Prasyarat

```
Python 3.9+
Jupyter Notebook
```

## Install Library

Jika ingin otomatis:

```
pip install pandas numpy matplotlib seaborn scikit-learn statsmodels imbalanced-learn
```

## Jalankan Notebook

```
jupyter notebook
```

---

# 📜 **Lisensi**

Project digunakan untuk keperluan lomba dan portofolio edukasi tim ThreeVolution.
