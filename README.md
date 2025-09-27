# Clustering Analysis on Economic Freedom Index

Repositori ini berisi implementasi kode dan dokumen penelitian **“Comparison of K-means, Gaussian Mixture, and Hierarchical Clustering Models On Countries’ Economic Freedom Index”**.  
Penelitian dilakukan oleh mahasiswa Bina Nusantara University pada tahun 2024.

---

## 🎯 Latar Belakang
Peningkatan penggunaan **machine learning** di bidang ekonomi membuka peluang untuk menganalisis data makroekonomi yang kompleks dan multidimensional.  
Salah satu pendekatan yang relevan adalah **clustering (unsupervised learning)**, yaitu mengelompokkan data negara berdasarkan kemiripan skor **Economic Freedom Index** yang diterbitkan oleh Heritage Foundation.

Economic Freedom Index sendiri menilai **184 negara** berdasarkan 12 indikator utama yang terbagi dalam 4 kategori:
- **Rule of Law** (Property Rights, Judicial Effectiveness, Government Integrity)  
- **Government Size** (Tax Burden, Government Spending, Fiscal Health)  
- **Regulatory Efficiency** (Business, Labor, Monetary Freedom)  
- **Market Openness** (Trade, Investment, Financial Freedom)  

---

## 🔬 Metodologi
1. **Dataset**  
   - Sumber: Heritage Foundation, *2024 Index of Economic Freedom*  
   - Jumlah negara: 184  
   - Variabel: 12 indikator + skor total  

2. **Preprocessing**
   - Seleksi kolom relevan (tanpa skor total)  
   - **Scaling** (normalisasi)  
   - **Principal Component Analysis (PCA)** → reduksi dimensi hingga 4 komponen yang menjelaskan ~80% variansi  

3. **Clustering Models**
   - **K-Means**  
     - Hyperparameter: jumlah cluster (k) → ditentukan dengan **Elbow Method** & **Silhouette Score**  
   - **Gaussian Mixture Model (GMM)**  
     - Distribusi probabilistik dengan EM (Expectation-Maximization)  
     - Jumlah cluster ditentukan dengan **BIC**, **Elbow**, dan **Silhouette**  
   - **Hierarchical Clustering Analysis (HCA)**  
     - Metode agglomerative clustering dengan Ward linkage  
     - Dendrogram untuk melihat jumlah cluster optimal  

4. **Evaluasi**
   - **Elbow Method** → menentukan jumlah cluster optimal dengan SSE (Sum of Squared Errors)  
   - **Silhouette Score** → mengukur kualitas cluster (-1 s/d 1)  

---

## 📊 Hasil
- **K-Means**  
  - Optimal: 4 cluster  
  - Cukup koheren, namun ada beberapa anomali (misalnya negara dengan skor rendah tergabung dengan negara skor tinggi).  

- **Gaussian Mixture Model (GMM)**  
  - Optimal: 3 cluster  
  - Hasil paling konsisten dengan distribusi kuartil skor indeks.  
  - Cluster 0: negara dengan kebebasan rendah (mis. Kongo, Korea Utara).  
  - Cluster 1: negara berkembang dengan kebebasan menengah (mis. Indonesia, Malaysia, Kolombia).  
  - Cluster 2: negara maju dengan kebebasan tinggi (mis. AS, Inggris, Australia, Korea Selatan).  

- **Hierarchical Clustering Analysis (HCA)**  
  - Optimal: 2 cluster (berdasarkan dendrogram & silhouette).  
  - Sederhana, namun terlalu menyatukan kelompok heterogen (misalnya Indonesia dan Saudi Arabia salah cluster).  

---

## 🏆 Kesimpulan
- **GMM** dengan 3 cluster adalah metode terbaik untuk dataset ini karena hasilnya paling sesuai dengan pembagian kuartil skor **Economic Freedom Index**.  
- **K-Means** juga cukup baik, namun menghasilkan 4 cluster dengan beberapa anomali.  
- **HCA** terlalu menyederhanakan dengan hanya 2 cluster, sehingga kurang representatif.  

📌 Secara keseluruhan, **kombinasi PCA + GMM** adalah pendekatan yang paling sesuai untuk analisis ini.

---

## Untuk lebih memvaca lebih dalam, Paper Penelitian ini berada di https://doi.org/10.1109/ICORIS63540.2024.10903728

