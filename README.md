# Sistem Rekomendasi Penempatan Industri Berbasis AI

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![Streamlit](https://img.shields.io/badge/Streamlit-Web_App-red)
![LightGBM](https://img.shields.io/badge/Model-LightGBM-green)
![Status](https://img.shields.io/badge/Status-Final_Project-success)

Proyek ini merupakan **Final Project Based Internship VINIX7 - Kelompok 2** berupa sistem rekomendasi penempatan industri berbasis AI. Sistem ini membantu memetakan mahasiswa atau kandidat ke dalam klaster industri yang sesuai berdasarkan preferensi gaya kerja, work values, kompetensi, pengalaman, dan profil psikometrik.

Aplikasi dikembangkan menggunakan pendekatan **Machine Learning klasifikasi multi-kelas** dengan model utama **LightGBM** dan diintegrasikan ke dalam web app interaktif berbasis **Streamlit**.

---

## Demo Aplikasi

Aplikasi dapat diakses melalui link berikut:

[https://vinix7-final-project-kelompok-2.streamlit.app/](https://vinix7-final-project-kelompok-2.streamlit.app/)

---

## Anggota Tim

- Muhammad Fikri Prasetyo
- Achmad Shandy Wijaya
- Abdul Muin

---

## Latar Belakang

Banyak mahasiswa memilih industri magang atau kerja berdasarkan tren, pengaruh lingkungan, atau persepsi umum, bukan berdasarkan kecocokan gaya kerja dan nilai kerja pribadi. Di sisi lain, HR atau lembaga rekrutmen juga menghadapi tantangan dalam memetakan profil kandidat secara manual karena data kompetensi bersifat multidimensi.

Masalah utama yang ingin diselesaikan:

- Skills mismatch antara latar belakang akademik dengan kebutuhan industri.
- Pemilihan industri yang kurang sesuai dengan karakteristik kandidat.
- Proses pemetaan kandidat secara manual yang memakan waktu.
- Kebutuhan sistem rekomendasi yang lebih objektif, cepat, dan berbasis data.

---

## Tujuan Proyek

Tujuan utama proyek ini adalah membangun sistem rekomendasi industri berbasis AI yang mampu:

- Mengklasifikasikan kandidat ke dalam klaster industri yang relevan.
- Memberikan rekomendasi karier yang lebih objektif berbasis data psikometrik.
- Membantu otomasi seleksi awal kandidat untuk mendukung efisiensi HR.
- Menyediakan dashboard interaktif yang mudah digunakan melalui Streamlit.

---

## Klaster Industri

Target awal industri dikelompokkan menjadi **3 klaster makro industri**:

| Klaster Industri | Deskripsi Singkat |
|---|---|
| Bidang Tech dan Digital | Industri yang dinamis, agile, dan berbasis teknologi seperti software, e-commerce, edtech, dan data. |
| Industri Konvensional Terstruktur | Industri yang stabil, hierarkis, dan berorientasi proses seperti perbankan, pemerintahan, manufaktur, dan healthcare. |
| Industri Kreatif dan Proyek | Industri yang kolaboratif, fleksibel, dan berbasis proyek seperti agency, NGO, consulting, desain, dan media. |

---

## Dataset

Dataset yang digunakan terdiri dari **1.392 data observasional mahasiswa** dengan berbagai informasi profil, antara lain:

- Latar belakang akademik dan program studi.
- Skills atau kompetensi teknis.
- Work values dan work style.
- Professional branding.
- Motivasi karier dan dream job.
- Pengalaman magang.
- Preferensi kerja seperti lokasi, fleksibilitas, dan ekspektasi.

Data awal memiliki banyak fitur heterogen, kemudian diproses melalui tahapan preprocessing, encoding, feature engineering, dan seleksi fitur.

---

## Metodologi

Tahapan pengerjaan proyek:

1. **Data Understanding**  
   Memahami struktur dataset, fitur, target, dan distribusi kelas.

2. **Data Preprocessing**  
   Membersihkan data teks, menangani nilai kosong, melakukan standardisasi string, dan menyiapkan format data yang dapat dibaca model.

3. **Feature Engineering**  
   Melakukan mapping program studi, dream job, pengalaman magang, serta transformasi fitur kategorikal menggunakan encoding.

4. **Target Grouping**  
   Mengelompokkan 10 target industri awal menjadi 3 klaster makro industri agar model lebih stabil dan representatif.

5. **Benchmarking Model**  
   Membandingkan beberapa algoritma klasifikasi, seperti Random Forest, XGBoost, dan LightGBM.

6. **Ablation Experiment**  
   Membandingkan performa model dengan SMOTETomek dan native class weight untuk melihat pendekatan terbaik pada data tidak seimbang.

7. **Hyperparameter Optimization**  
   Menggunakan **Optuna Bayesian Optimization** sebanyak 50 trials untuk mencari parameter LightGBM terbaik.

8. **Feature Selection**  
   Menggunakan **RFECV** untuk memilih fitur paling relevan dan mengurangi noise.

9. **Deployment**  
   Model diserialisasi menggunakan `joblib` dan diintegrasikan ke dalam aplikasi web interaktif berbasis Streamlit.

---

## Model Machine Learning

Model utama yang digunakan:

- **LightGBM Classifier**
- Class weighting untuk menangani distribusi kelas
- Optuna untuk hyperparameter tuning
- RFECV untuk seleksi fitur
- Joblib untuk serialisasi model

Artefak model yang digunakan dalam deployment:

```text
model_lightgbm_vinix.pkl
label_encoder_vinix.pkl
fitur_model_vinix.pkl
```

---

## Performa Model

Hasil evaluasi model akhir:

| Metrik Evaluasi | Nilai |
|---|---:|
| Accuracy | 54% |
| Balanced Accuracy | 53.89% |
| Macro F1-Score | 0.54 |
| Weighted F1-Score | 0.55 |

Model menunjukkan performa lebih baik dibandingkan tebakan acak pada klasifikasi 3 kelas, yaitu sekitar 33%.

Performa terbaik terlihat pada klaster **Bidang Tech dan Digital** dengan precision sekitar **66%**.

---

## Fitur Aplikasi

Aplikasi Streamlit menyediakan beberapa fitur utama:

- Input profil kandidat atau mahasiswa.
- Prediksi rekomendasi industri secara real-time.
- Visualisasi profil psikometrik menggunakan radar chart.
- Pengelompokan user archetype.
- Session history untuk menyimpan riwayat sesi pengguna.
- Dashboard interaktif untuk menampilkan hasil rekomendasi.

---

## Tech Stack

| Kategori | Tools / Library |
|---|---|
| Bahasa Pemrograman | Python |
| Data Manipulation | Pandas, NumPy |
| Machine Learning | Scikit-learn, LightGBM, XGBoost, Random Forest |
| Optimization | Optuna |
| Feature Selection | RFECV |
| Visualization | Matplotlib, Seaborn, Plotly |
| Web App | Streamlit |
| Model Serialization | Joblib / Pickle |
| Version Control | Git, GitHub |

---

## Struktur Folder

```text
final-project-karir-ai/
│
├── app.py                         # Aplikasi Streamlit
├── Final_Project_run2.ipynb        # Notebook eksperimen dan training model
├── data_karir_2.xlsx              # Dataset proyek
├── model_lightgbm_vinix.pkl        # Model LightGBM hasil training
├── label_encoder_vinix.pkl         # Label encoder target industri
├── fitur_model_vinix.pkl           # Daftar fitur final untuk model
├── requirements.txt                # Daftar dependency Python
├── .gitignore                      # File pengecualian Git
└── README.md                       # Dokumentasi proyek
```

---

## Cara Menjalankan Project di Lokal

### 1. Clone repository

```bash
git clone https://github.com/abdulmuinn/final-project-karir-ai.git
cd final-project-karir-ai
```

### 2. Buat environment

Menggunakan conda:

```bash
conda create -n karir-ai python=3.10 -y
conda activate karir-ai
```

Atau menggunakan venv:

```bash
python -m venv venv
venv\Scripts\activate
```

### 3. Install dependency

```bash
pip install -r requirements.txt
```

### 4. Jalankan aplikasi

```bash
streamlit run app.py
```

Setelah berhasil, aplikasi akan terbuka di browser melalui alamat lokal seperti:

```text
http://localhost:8501
```

---

## Cara Push Perubahan ke GitHub

Jika ada perubahan file, jalankan perintah berikut:

```bash
git status
git add .
git commit -m "Update project documentation"
git push
```

---

## Insight Utama

Berdasarkan hasil analisis, kesesuaian industri tidak hanya ditentukan oleh latar belakang akademik. Faktor seperti skills, branding profesional, work values, gaya kerja, dan preferensi lingkungan kerja memiliki kontribusi penting dalam menentukan rekomendasi industri.

Dengan pendekatan ini, sistem dapat menjadi alat bantu awal untuk:

- Mahasiswa yang ingin memahami arah karier.
- Universitas dalam layanan career development.
- HR atau industri dalam proses screening awal kandidat.

---

## Limitasi

- Model masih bergantung pada kualitas data survei.
- Data psikometrik manusia bersifat dinamis dan dapat berubah seiring pengalaman.
- Hasil rekomendasi sebaiknya digunakan sebagai alat bantu, bukan keputusan final mutlak.
- Performa model masih dapat ditingkatkan dengan penambahan data dan validasi eksternal.

---

## Rencana Pengembangan

Beberapa pengembangan yang dapat dilakukan ke depan:

- Menambahkan dataset yang lebih besar dan lebih beragam.
- Menambahkan explainability model, seperti SHAP atau feature importance interaktif.
- Menyediakan rekomendasi role pekerjaan yang lebih spesifik.
- Menambahkan autentikasi pengguna.
- Menyimpan hasil prediksi ke database.
- Mengembangkan dashboard admin untuk HR atau kampus.

---

## Catatan

Sistem ini merupakan prototype final project dan ditujukan sebagai alat bantu rekomendasi awal. Keputusan karier tetap perlu mempertimbangkan aspek personal, pengalaman nyata, konsultasi karier, dan kebutuhan industri terkini.
