# Analisis-Sentimen-Ulasan-Aplikasi-JKN-Mobile
Pipeline NLP untuk analisis sentimen ulasan aplikasi Mobile JKN — data di-scraping dari Google Play Store. Proyek ini mencakup keseluruhan alur kerja: scraping data, preprocessing teks, pelabelan berbasis lexicon, exploratory data analysis, hingga klasifikasi sentimen menggunakan beberapa model.


## Ringkasan
Mobile JKN adalah aplikasi mobile BPJS Kesehatan. Proyek ini menganalisis bagaimana persepsi pengguna terhadap aplikasi tersebut berdasarkan ulasan publik,sekaligus membandingkan pendekatan deep learning (LSTM) dan machine learning klasik (SVM, Logistic Regression) untuk mengklasifikasikan sentimen ulasan secara otomatis.

## Dataset
- **Sumber**: Scraping langsung dari Google Play Store
- **Jumlah**: 11.247 ulasan pengguna
- **Label**: Positif / Netral / Negatif (pelabelan berbasis lexicon)
- **Distribusi kelas**: Negatif 8.848 · Positif 1.912 · Netral 487 (tidak seimbang/imbalanced)

## Alur Pipeline
1. **Pengumpulan Data** — Scraping ulasan mentah dari Google Play Store
2. **Preprocessing Teks** — Cleaning, normalisasi kata slang, tokenisasi, stopword removal (NLTK + Sastrawi untuk Bahasa Indonesia)
3. **Pelabelan Sentimen** — Pendekatan berbasis lexicon untuk menentukan label positif/netral/negatif
4. **Exploratory Data Analysis** — Wordcloud per kelas sentimen, distribusi sentimen, distribusi panjang ulasan, analisis kata paling sering muncul (TF-IDF)
5. **Training Model** — Tiga pendekatan klasifikasi dilatih dan dibandingkan
6. **Inference** — Fungsi terpadu untuk menghasilkan prediksi dari seluruh model yang telah dilatih

## Model & Hasil
| Model | Ekstraksi Fitur | Akurasi Test |
|---|---|---|
| Bidirectional LSTM | Trainable embedding layer | 87,20% |
| **SVM** (tuning GridSearchCV) | TF-IDF | **88,67%** (terbaik) |
| Logistic Regression | TF-IDF | 85,69% |

## Tech Stack
- **Bahasa**: Python
- **NLP**: NLTK, Sastrawi
- **ML/DL**: Scikit-learn, TensorFlow/Keras
- **Data**: Pandas, NumPy
- **Visualisasi**: Matplotlib, WordCloud
