# 🍽️ Analisis Sentimen Publik terhadap Program Makan Bergizi Gratis (MBG)

> **Studi berbasis data komentar YouTube untuk memahami persepsi masyarakat Indonesia terhadap kebijakan MBG**

---

## 📌 Gambaran Umum

Program **Makan Bergizi Gratis (MBG)** merupakan salah satu kebijakan pemerintah Indonesia yang menuai banyak perhatian publik. Program ini dirancang untuk meningkatkan kualitas gizi anak-anak sekolah dan menekan angka stunting. Namun, di balik tujuan mulia tersebut, muncul berbagai pertanyaan dan kekhawatiran di masyarakat — terutama soal anggaran, transparansi, dan risiko korupsi.

Proyek analisis ini hadir untuk **menjawab pertanyaan-pertanyaan tersebut secara objektif dan berbasis data**, dengan memanfaatkan opini publik yang terekam di platform YouTube.

---

## 🎯 Tujuan Analisis

Analisis ini bertujuan untuk:

1. **Mengukur sentimen publik** — seberapa banyak komentar yang bersifat positif, negatif, atau netral terhadap program MBG?
2. **Mengidentifikasi topik utama** — isu apa yang paling banyak dibicarakan masyarakat?
3. **Menganalisis emosi dominan** — apakah masyarakat marah, sedih, takut, atau senang?
4. **Merumuskan rekomendasi** berbasis data untuk pemerintah, peneliti, dan pemangku kepentingan.

---

## ❓ Rumusan Masalah

| No | Pertanyaan |
|----|-----------|
| 1 | Bagaimana distribusi sentimen publik terhadap program MBG? |
| 2 | Topik apa yang paling sering dibahas terkait MBG? |
| 3 | Apa emosi dominan yang muncul di kolom komentar? |
| 4 | Apakah masyarakat cenderung mendukung, netral, atau menolak MBG? |

---

## 📦 Sumber Data

| Atribut | Detail |
|---------|--------|
| **Platform** | YouTube |
| **Video** | *"Program Makan Bergizi Gratis (MBG): Solusi Ekonomi atau Beban Negara?"* |
| **Channel** | Ngomongin Uang |
| **Tanggal Upload Video** | Maret 2026 |
| **Tanggal Scraping** | 28 Mei 2026 |
| **Total Views** | ±115.000 |
| **Jumlah Komentar Diambil** | 1.000 komentar |
| **Jumlah Komentar Dianalisis** | 865 komentar (setelah cleaning) |
| **Bahasa** | Indonesia (informal) |

Data dikumpulkan secara mandiri melalui teknik **web scraping** menggunakan library `youtube-comment-downloader` — tanpa memerlukan API key resmi dari Google.

---

## 🛠️ Metode & Tools yang Digunakan

### Metode Analisis

| Metode | Tujuan |
|--------|--------|
| **Analisis Sentimen** | Mengklasifikasikan komentar ke dalam kategori positif, negatif, atau netral |
| **Word Cloud & Frekuensi Kata** | Mengetahui kata/topik yang paling sering muncul dalam diskusi |
| **Analisis Emosi** | Mengidentifikasi emosi dominan (marah, sedih, senang, takut, cinta) |

### Tools & Library

| Tool/Library | Fungsi |
|-------------|--------|
| `youtube-comment-downloader` | Scraping komentar YouTube tanpa API key |
| `pandas` | Pengolahan dan manipulasi data |
| `transformers` (Hugging Face) | Implementasi model AI untuk sentimen & emosi |
| `indonesian-roberta-base-sentiment-classifier` | Model AI analisis sentimen Bahasa Indonesia (akurasi 94,36%) |
| `indonesian-roberta-base-emotion-classifier` | Model AI analisis emosi Bahasa Indonesia |
| `Sastrawi` | Stemming dan stopword removal Bahasa Indonesia |
| `WordCloud` | Visualisasi frekuensi kata |
| `matplotlib` & `seaborn` | Visualisasi grafik dan chart |

### Proses Pembersihan Data (Data Cleaning)

Sebelum dianalisis, data melalui serangkaian proses pembersihan:

- Mengubah semua teks ke **huruf kecil**
- Menghapus **URL, mention (@user), dan hashtag (#)**
- Normalisasi **satuan angka informal** (contoh: "300jt" → "300 juta", "1,2T" → "1,2 triliun")
- Normalisasi **kata slang dan singkatan** (contoh: "gak" → "tidak", "yg" → "yang")
- Menghapus **karakter berulang** yang berlebihan
- Memfilter komentar dengan **minimal 5 kata** agar analisis lebih bermakna

---

## 📊 Hasil & Insight Utama

### 1. Distribusi Sentimen

Dari 865 komentar yang dianalisis:

| Sentimen | Jumlah Komentar | Persentase |
|----------|----------------|------------|
| 🔴 Negatif | 631 | **72,9%** |
| 🟢 Positif | 144 | 16,6% |
| 🔵 Netral | 90 | 10,4% |

> **Temuan:** Mayoritas komentar (hampir 3 dari 4) bersifat negatif — menunjukkan bahwa masyarakat yang aktif berkomentar lebih banyak mengekspresikan kritik dan kekhawatiran dibandingkan dukungan terhadap program MBG.

---

### 2. Topik yang Paling Banyak Dibahas (Word Cloud)

Kata-kata yang paling sering muncul dalam diskusi:

| Kata | Frekuensi | Makna |
|------|-----------|-------|
| mbg | 720 | Program itu sendiri |
| program | 332 | Konteks kebijakan |
| makan | 257 | Isu utama program |
| gizi | 230 | Tujuan program |
| rakyat | 213 | Penerima manfaat |
| negara | 196 | Konteks nasional |
| anak | 160 | Target penerima |
| anggar | 137 | Kekhawatiran anggaran |

Selain kata-kata terkait tujuan program, kata seperti **korupsi, uang, pemerintah, beban**, dan **pajak** juga muncul sangat dominan.

> **Temuan:** Masyarakat bukan hanya membahas manfaat program, melainkan lebih banyak mempersoalkan **besarnya anggaran, risiko korupsi, dan efektivitas pengelolaan** program oleh pemerintah.

---

### 3. Distribusi Emosi

Analisis emosi memberikan pemahaman yang lebih dalam dari sekadar "positif/negatif":

| Emosi | Jumlah | Persentase | Deskripsi |
|-------|--------|------------|-----------|
| 😡 Marah (Anger) | 489 | **56,5%** | Ketidakpuasan kuat terhadap program |
| 😢 Sedih (Sadness) | 170 | 19,7% | Pesimis terhadap kemampuan pemerintah |
| 😊 Senang (Happy) | 165 | 19,1% | Dukungan karena manfaat gizi anak |
| 😨 Takut (Fear) | 40 | 4,6% | Khawatir dampak ekonomi & korupsi |
| ❤️ Cinta (Love) | 1 | 0,1% | Hampir tidak ada |

> **Temuan:** Lebih dari separuh komentar mengandung emosi **kemarahan** — bukan sekadar kritik biasa, tetapi ketidakpuasan yang aktif dan kuat. Ini berbeda dari sekadar kekhawatiran (fear) atau kesedihan (sadness).

---

### 4. Hubungan Sentimen & Emosi

Analisis lintas dua metode mengungkap pola yang menarik:
- Komentar **negatif** didominasi emosi **marah (439 komentar)** — jauh lebih besar dari sedih dan takut.
- Komentar **positif** didominasi emosi **senang (happy)**, mencerminkan dukungan nyata karena melihat manfaat konkret program.

> **Insight Kunci:** Masyarakat tidak hanya khawatir — mereka **aktif memprotes**. Ini merupakan sinyal penting bagi pemerintah untuk merespons dengan komunikasi yang lebih transparan dan akuntabel.

---

### 5. Implikasi Temuan

**Implikasi Sosial**
Masyarakat pada dasarnya memahami pentingnya gizi anak, terbukti dari kemunculan kata "anak", "gizi", dan "stunting". Namun, mereka mempertanyakan **efektivitas mekanisme pelaksanaan** program.

**Implikasi Ekonomi**
Kata-kata seperti "anggaran", "pajak", "uang", dan "korupsi" mendominasi percakapan — menunjukkan bahwa masyarakat mengkhawatirkan program MBG sebagai **beban fiskal** yang membuka peluang penyalahgunaan dana.

**Implikasi Politik**
Kemunculan nama "pemerintah" dan "Presiden" secara dominan menunjukkan bahwa persepsi terhadap MBG **tidak terpisah dari kepercayaan publik terhadap pemimpin yang mengusung program**. Polarisasi politik berpengaruh pada cara masyarakat menerima kebijakan.

---

## ✅ Kesimpulan

1. **Sentimen mayoritas negatif (72,9%)** — sebagian besar masyarakat yang berpartisipasi dalam diskusi memiliki pandangan kritis terhadap program MBG.
2. **Isu tata kelola & anggaran mendominasi** diskusi, bukan isu gizi itu sendiri — menunjukkan ketidakpercayaan terhadap implementasi, bukan penolakan terhadap tujuan program.
3. **Emosi marah (56,5%) paling dominan** — komentar negatif bukan sekadar kritik pasif, tetapi mencerminkan ketidakpuasan aktif yang kuat.
4. **Masyarakat tidak menolak tujuan MBG**, melainkan mempertanyakan transparansi, akuntabilitas, dan potensi penyalahgunaan anggaran.

---

## 💡 Rekomendasi

### Untuk Pemerintah & Pemangku Kepentingan

- **Tingkatkan transparansi** mengenai sumber pendanaan, mekanisme distribusi, dan sistem pengawasan program MBG.
- **Perkuat komunikasi publik** — jelaskan manfaat jangka panjang program secara konkret dan mudah dipahami masyarakat luas.
- **Libatkan masyarakat** dalam proses pengawasan untuk membangun kepercayaan publik.

### Untuk Penelitian Selanjutnya

- Perluas sumber data ke platform lain (X/Twitter, Instagram, TikTok, portal berita) untuk gambaran yang lebih representatif.
- Pertimbangkan pengembangan model Machine Learning yang dilatih khusus pada data komentar kebijakan publik Indonesia — untuk hasil yang lebih akurat dalam mendeteksi sarkasme dan bahasa informal khas netizen Indonesia.
- Lakukan analisis perbandingan lintas waktu untuk memantau perubahan sentimen publik seiring berjalannya program.

### Untuk Pemantauan Opini Publik

- Pendekatan kombinasi **sentimen + emosi + Word Cloud** terbukti memberikan gambaran yang lebih komprehensif dibandingkan satu metode saja.
- Metodologi ini dapat diadaptasi untuk memantau opini publik terhadap berbagai program kebijakan pemerintah lainnya secara real-time dan berbasis data.

---

## ⚠️ Keterbatasan Analisis

- Data hanya bersumber dari **satu video YouTube** — belum merepresentasikan seluruh opini masyarakat Indonesia.
- Model pre-trained memiliki **keterbatasan dalam mendeteksi sarkasme** dan bahasa informal/slang khas Indonesia.
- Audiens YouTube memiliki **profil demografi tertentu** yang mungkin tidak mewakili populasi umum.
- Beberapa komentar menunjukkan **ketidaksesuaian antara sentimen dan emosi** yang terdeteksi model — hal ini merupakan keterbatasan model NLP saat ini.

---

## 👤 Tentang Analisis Ini

| | |
|--|--|
| **Analyst** | Muhammad Rafli Febriyanto |
| **Program** | BeData Internship — Data Analyst |
| **Topik** | Analisis Sentimen Program Makan Bergizi Gratis (MBG) |
| **Tanggal Analisis** | Mei 2026 |

---

*Analisis ini dibuat sebagai bagian dari Technical Assessment BeData Internship Program. Data yang digunakan merupakan komentar publik yang tersedia secara terbuka di platform YouTube.*
