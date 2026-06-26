# CBR-Putusan-Wanprestasi
Proyek implementasi sistem Case-Based Reasoning (CBR) berbasis Python yang dirancang untuk mendukung analisis putusan pengadilan Indonesia. Proyek ini memanfaatkan data putusan resmi yang dipublikasikan di Direktori Putusan Mahkamah Agung Republik Indonesia khusus untuk domain hukum Perdata Gugatan Wanprestasi.


# Alur Siklus CBR (Pipeline)
1. Tahap 1 (Membangun Case Base): Mengonversi berkas PDF putusan MA menjadi teks mentah dan pembersihan teks dari komponen formalitas (header, footer, watermark) menggunakan Reguler Expression  (Regex)
2. Tahap 2 (Case Representation): Ekstraksi otomatis metadata penting seperti Nomor Perkara, Tanggal, Nama Pihak, sert akonten kunci berupa ringkasan fakta dan amar putusa.
3. Tahap 3 (Case Retrieval): Pembagian data train dan data test (rasio 80:20), pembobotan statistik menggunakan TF-IDF, dan perhitungan skor kemiripan berbasis Cosine Similarity untuk menyusun peringkat kasus terdekat.
4. Tahap 4 (Case Solution Reuse): Pemninjaman solusi menggunakan pendekatan Weighted Similarity untuk merumuskan rekomendasi amar keputusan bagi kasus hukum baru.
5. Tahap 5 (Model Evaluation): Proses evaluasi performa model menggunakan library scikit-learn dan analisis kritis kegagalan sistem.

# Petunjuk Instalasi & Eksekusi Pipeline
- Pemasangan Library : Jalankan perintah **pip install pdfminer.six pandas numpy scikit-learn** pada terminal atau sel kode untuk menginstal seluruh Library pendukung.
- Eksekusi Pipeline: Hubungkan Google Drive (mount drive) ke Google Colab, lalu buka dan jalankan berkas Jupyter Notebook di folder __notebooks/__ secara berurutan mulai dari Tahap 1 sampai Tahap 5.

# Hasil Evaluasi Metrik Retrieval

- Accuracy : 0.00 (0%)
- Precision : 0.00 (0%)
- Recall : 0.00 (0%)
- F1-Score : 0.00 (0%)

Hasil evaluasi menunjukkan status gagal temu/rejection pada seluruh kueri kasus hukum baru yang diuji oleh sistem.

# Analisis Kegegalan Model 
1. Keterbatasan Leksikal TF-IDF: Model statistik TF-IDF hanya mengandalkan pencocokan kata secara harfiah (lexical matching) sehingga tidak mampu memahami esensi hukum secara kontekstual.
2. Noise Template Kalimat Formalitas: Adanya struktur kalimat pengantar persidangan yang seragam di hampir semua dokumen putusan MA mendominasi pembobotan vektor dokumen dan mengaburkan keunikan teks kronologi utama kasus wanprestasi.
3. Keterbatas Kualitas data hasil Ekstraksi: Penulisan teks asli yang tidak baku pada beberapa PDF menyebabkan permotongan string pada pola Regex menghasilkan teks keuri yang sangat pendek atau kosong, sehingga memicu nilai kemiripan seragam yang acak.

# Rekomendasi Pengembangan Selanjutnya
1. Penerapan Text Embedding: Mengganti model statistik TF-IDF dengan pendekatan Text Embedding berbasis deep learning Transformer secara IndoBERT agar mampu menangkap kesamaan makna semantik hukum secara cerdas.
2. Optimasi Regec Pembersihan Data: Memperketat pola penyaringan Regac pada tahap prapemrosesan guna menyapu bersih seluruh kalimat template formalitas sidang.

  
   
