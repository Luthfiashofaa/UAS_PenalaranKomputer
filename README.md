# Case-Based Reasoning (CBR) System untuk Analisis Putusan Pengadilan

Sistem CBR (Case-Based Reasoning) untuk menganalisis dan memprediksi putusan pengadilan berdasarkan kasus-kasus serupa yang telah ada. Sistem ini menggunakan teknik Machine Learning dan Natural Language Processing untuk melakukan retrieval dan prediksi outcome kasus hukum.
🔗 Sumber Data
Direktori Putusan Mahkamah Agung RI: https://putusan3.mahkamahagung.go.id/
📝 Deskripsi
Sistem ini mengimplementasikan 5 tahap utama dalam siklus CBR:

Case Base Building - Pengumpulan dan pembersihan corpus putusan
Case Representation - Representasi putusan dalam struktur data terorganisir
Case Retrieval - Pencarian kasus serupa menggunakan ML/NLP
Solution Reuse - Prediksi outcome berdasarkan kasus serupa
Model Evaluation - Evaluasi performa sistem

🛠️ Requirements
Sistem Requirements

Python 3.8+
RAM minimum 8GB (direkomendasikan 16GB)
Storage 5GB+ untuk dataset

Python Dependencies
txt# requirements.txt
pandas>=1.5.0
numpy>=1.21.0
scikit-learn>=1.1.0
transformers>=4.20.0
torch>=1.12.0
beautifulsoup4>=4.11.0
pdfminer.six>=20220524
requests>=2.28.0
matplotlib>=3.5.0
seaborn>=0.11.0
tqdm>=4.64.0
jupyter>=1.0.0
nltk>=3.7
Installation
bash# Clone repository
git clone <repository-url>
cd cbr-legal-system

# Create virtual environment
python -m venv venv
source venv/bin/activate  # Linux/Mac
# atau
venv\Scripts\activate     # Windows

# Install dependencies
pip install -r requirements.txt

# Download NLTK data (jika diperlukan)
python -c "import nltk; nltk.download('punkt'); nltk.download('stopwords')"
📁 Struktur Direktori
```plaintext
UAS_PenalaranKomputer/
├── CBR/
│   ├── data/
│   │   ├── eval/              # Evaluation datasets
│   │   ├── processed/         # Processed data files
│   │   ├── raw/               # Raw data files
│   │   ├── results/           # Results and outputs
│   ├── logs/                  # Log files
│   ├── PDF/
│   │   ├── Korupsi/           # Corruption-related PDF documents
│   │   ├── Non Korupsi/       # Non-corruption-related PDF documents
│   ├── notebooks/
│   │   ├── 01_scraper.ipynb   # Notebook for data scraping
│   │   ├── 02_representation.ipynb  # Notebook for data representation
│   │   ├── 03_retrieval.ipynb # Notebook for case retrieval
│   │   ├── 04_predict.ipynb    # Notebook for prediction
│   │   ├── 05_evaluation.ipynb # Notebook for evaluation
│   │   ├── requirements.txt    # Python dependencies
├── README.md                  # Project overview (this file)
```
## 🚀 Cara Menjalankan Pipeline End-to-End
Pipeline ini mencakup langkah-langkah berikut:
1. **Scraping Data**: Mengambil dokumen PDF dan mengonversinya ke teks.
2. **Ekstraksi Metadata**: Memproses teks untuk mengekstrak metadata seperti nomor perkara, tanggal putusan, dll.
3. **Retrieval dan Prediksi**: Menggunakan model untuk mencari dokumen relevan dan memprediksi solusi putusan.
4. **Evaluasi**: Menghitung metrik performa dan menganalisis kesalahan.

### 📋 Langkah-langkah Eksekusi
1. **Jalankan 01_scraper.ipynb**
   - Buka notebook di Jupyter:
     ```bash
     jupyter notebook notebooks/01_scraper.ipynb
     ```
   - Jalankan semua sel untuk mengunduh hingga 60 dokumen PDF pidana khusus korupsi dari situs Direktori Mahkamah Agung (`https://putusan3.mahkamahagung.go.id/`) dan menyimpan teksnya di folder `data/raw/`.
   - Catatan: Pastikan koneksi internet stabil. Log disimpan di `logs/cleaning.log`.

2. **Jalankan 02_representation.ipynb**
   - Eksekusi notebook untuk mengekstrak metadata dari file teks di `data/raw/` dan menyimpan hasilnya ke `data/processed/cases.csv`.
   - Log disimpan di `logs/metadata_extraction.log`.

3. **Jalankan 03_retrieval.ipynb**
   - Eksekusi notebook untuk melakukan retrieval dokumen menggunakan IndoBERT dan Logistic Regression.
   - Hasil evaluasi retrieval ditampilkan di output notebook, termasuk akurasi dan recall.

4. **Jalankan 04_predict.ipynb**
   - Eksekusi notebook untuk memprediksi solusi putusan menggunakan tiga model: Logistic Regression, SVM, dan IndoBERT.
   - Hasil prediksi disimpan di `data/results/logreg_predictions.csv`, `data/results/svm_predictions.csv`, dan `data/results/indobert_predictions.csv`.

5. **Jalankan 05_evaluation.ipynb**
   - Eksekusi notebook untuk mengevaluasi performa retrieval dan prediksi.
   - Metrik evaluasi disimpan di `data/eval/retrieval_metrics.csv` dan `data/eval/prediction_metrics.csv`.
   - Visualisasi (confusion matrix dan bar chart) dihasilkan dan disimpan di `data/eval/performance_bar_chart.png`.

### 📚 Referensi

Direktori Putusan MA RI

### 👥 Contributors

Luthfia Shofa Dewi (202210370311303)
Nabil Eka Putra Aqilah (202210370311305)

📄 License
MIT License - see LICENSE file for details

Catatan: Pastikan untuk mematuhi robots.txt dan kebijakan scraping dari website Mahkamah Agung RI. Gunakan sistem ini hanya untuk tujuan penelitian dan pendidikan.
