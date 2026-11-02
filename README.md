# SIMUTEH - Evaluasi Praktikum Computer Vision P1-P4

**Nama:** Adriana Syahban
**NIM:** 2330511027
**Kelas:** 7A
**SEED dataset:** `1027`
**Repository:** https://github.com/Dr1anz/SIMUTEH-2330511027

## Ringkasan proyek

SIMUTEH merupakan studi kasus alat bantu penyortiran pucuk dan daun teh berdasarkan keberadaan bercak. Evaluasi ini mengerjakan pipeline awal: formulasi masalah, akuisisi, ruang warna, histogram, operasi titik, konvolusi, penapisan, dan integrasi praproses. Dataset yang digunakan adalah dataset sintetis dari Lampiran A petunjuk praktikum, bukan foto lapangan atau alat diagnosis penyakit nyata.

## Struktur repository

```text
SIMUTEH-2330511027/
├── data/
│   └── sintetis/              # dibuat otomatis; tidak perlu disertakan di ZIP kode
├── notebook/
│   ├── B1_lingkungan.ipynb
│   ├── B2_citra_warna.ipynb
│   ├── B3_histogram.ipynb
│   ├── B4_penapisan.ipynb
│   └── B5_praproses.ipynb
├── src/
│   ├── buat_dataset_sintetis.py
│   ├── utils_cv.py
│   ├── praproses.py
│   ├── eksperimen_awal.py
│   ├── eksperimen_penapis.py
│   ├── gambar_hasil.py
│   └── lengkapi_hasil.py
├── hasil/                     # tabel CSV, grafik, dan parameter hasil eksperimen
├── laporan/                   # laporan dan presentasi
├── requirements.txt
├── LEMBAR_HITUNG_MANUAL.md
└── README.md
```

## Cara menjalankan di Windows

Disarankan menggunakan Python 3.11 atau lebih baru agar cocok dengan versi pustaka yang dikunci pada requirements.txt. Dari folder utama repository, jalankan:

```powershell
py -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install -r requirements.txt
python src/buat_dataset_sintetis.py
jupyter lab
```

Setelah JupyterLab terbuka, masuk ke folder `notebook/` dan jalankan notebook dari **B1 sampai B5 secara berurutan** menggunakan `Kernel > Restart Kernel and Run All Cells`. Notebook menggunakan jalur relatif ke folder utama repository, jadi jangan memindahkannya keluar dari `notebook/`.

Dataset akan dibuat di `data/sintetis/` dengan 60 citra berukuran 640 × 480: 20 sehat, 20 bercak ringan, dan 20 bercak berat. Setiap kelas memiliki lima kondisi cahaya yang berulang. Skrip memakai `SEED = 1027`; jangan mengubah nilai itu untuk pengumpulan tugas ini.

## Hasil eksperimen utama

- Kanal R menghasilkan rerata Kontras Bercak (KB) tertinggi di antara tujuh kanal yang diuji pada kelas ringan dan berat untuk lima kondisi pencahayaan.
- Pada contoh `teh_045.png`, KB citra asli adalah 2,031; ekualisasi histogram global menghasilkan 1,509; CLAHE menghasilkan 2,278.
- Pada percobaan penapisan, median 3 × 3 memberikan PSNR tertinggi untuk derau garam-merica 4%. Median 9 × 9 memberikan PSNR tertinggi untuk Gaussian 20 pada satu citra uji, tetapi lebih lambat dan berisiko menghilangkan bercak kecil.
- Pengaturan integrasi yang diuji adalah lebar 640, gamma 1,0, CLAHE kanal V (clip 2,0; tile 8), median 3 × 3, dan tanpa penajaman. Rerata KB meningkat pada empat kondisi dan turun 3,09% pada kondisi terang.

Angka waktu komputasi dapat berubah menurut perangkat dan beban sistem. Semua hasil perlu diperiksa kembali setelah notebook dijalankan di komputer sendiri.

## Penggunaan AI dan keterbatasan

AI digunakan sebagai alat bantu dalam pengembangan kode, pelaksanaan dan pemeriksaan eksperimen, serta penyusunan dokumentasi. Hasil numerik diperoleh dari eksekusi dataset dengan SEED 1034. Penjelasan penggunaan bantuan tercantum pada bagian refleksi laporan.

## Berkas pendamping

- Laporan praktikum: [Word](<Laporan Eval P1-P4 Adrian - 2330511027.docx>) dan [PDF](<Laporan Eval P1-P4 Adrian - 2330511027.pdf>).
- Presentasi: [PowerPoint](<PPT Eval P1-P4 Adrian - 2330511027.pptx>) dan [PDF](<PPT Eval P1-P4 Adrian - 2330511027.pdf>).
- Lembar Hitung Manual: [Word](<Lembar Hitung Manual Adrian - 2330511027.docx>) dan [PDF](<Lembar Hitung Manual Adrian - 2330511027.pdf>).
