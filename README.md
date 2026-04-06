# Named Entity Recognition untuk Bahasa Indonesia

Proyek ini membangun sistem Named Entity Recognition (NER) untuk teks bahasa Indonesia menggunakan model BERT multilingual. Alur kerja mencakup persiapan data, tokenisasi, pelatihan model, evaluasi, dan penyimpanan model terbaik berdasarkan F1-score pada data validasi.

## Ringkasan Proyek

Tujuan utama proyek ini adalah mengenali entitas berikut dalam kalimat bahasa Indonesia:

- PERSON
- ORGANIZATION
- LOCATION
- TIME
- QUANTITY

Pendekatan yang digunakan adalah fine-tuning `bert-base-multilingual-cased` untuk tugas token classification.

## Sumber Dataset

Dataset yang digunakan berasal dari repositori Indolem pada GitHub:

[https://github.com/indolem/indolem/tree/main/ner](https://github.com/indolem/indolem/tree/main/ner)

Data asli tersedia dalam format TSV, lalu diproses menjadi file CSV agar lebih mudah digunakan di pipeline pelatihan ini:

- `train_data.csv`
- `dev_data.csv`
- `test_data.csv`

## Struktur File

- `RayzanFazriRamdany_DSML40_Day43.py` - skrip utama untuk preprocessing, training, dan evaluasi model
- `RayzanFazriRamdany_DSML40_Day43.ipynb` - versi notebook dari eksperimen
- `train_data.csv` - data latih hasil preprocessing
- `dev_data.csv` - data validasi hasil preprocessing
- `test_data.csv` - data uji hasil preprocessing
- `README.md` - dokumentasi proyek

## Dependensi

Pastikan lingkungan Python Anda memiliki paket berikut:

- pandas
- numpy
- matplotlib
- seaborn
- torch
- transformers
- datasets
- seqeval

Jika diperlukan, instal dengan:

```bash
pip install pandas numpy matplotlib seaborn torch transformers datasets seqeval
```

## Alur Kerja

1. Ambil data NER dari repo Indolem.
2. Ubah data TSV menjadi CSV.
3. Muat data CSV dan parsing token serta label.
4. Tokenisasi menggunakan tokenizer BERT multilingual.
5. Bentuk dataset dan dataloader PyTorch.
6. Fine-tune model `BertForTokenClassification`.
7. Evaluasi model pada validation set dan test set.
8. Simpan model terbaik berdasarkan F1-score.

## Cara Menjalankan

1. Pastikan file CSV sudah tersedia di folder proyek.
2. Jalankan skrip Python berikut:

```bash
python RayzanFazriRamdany_DSML40_Day43.py
```

3. Model terbaik akan disimpan sebagai `best_ner_model.pt`.

## Konfigurasi Utama

Pengaturan utama yang digunakan dalam eksperimen ini:

- Model dasar: `bert-base-multilingual-cased`
- Panjang maksimum token: 128
- Batch size: 16
- Epoch: 5
- Learning rate: 2e-5
- Warmup ratio: 0.1

## Evaluasi

Evaluasi dilakukan menggunakan metrik:

- Precision
- Recall
- F1-score

Metrik dihitung dengan library `seqeval`, yang umum digunakan untuk tugas sequence labeling seperti NER.

## Catatan

- Skrip utama saat ini masih mengacu pada folder data mentah lokal untuk proses konversi awal TSV ke CSV. Jika Anda hanya ingin menjalankan eksperimen dari CSV yang sudah tersedia, bagian preprocessing awal dapat disesuaikan.
- File model hasil training `best_ner_model.pt` tidak disertakan di repositori ini dan akan dibuat saat training selesai.

## Lisensi Dataset

Silakan cek repositori sumber Indolem untuk ketentuan penggunaan dataset dan atribusi yang berlaku.