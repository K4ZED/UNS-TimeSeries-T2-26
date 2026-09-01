# Tugas 2 — Analisis Data Time Series

Folder ini berisi dua notebook dengan tujuan berbeda: satu adalah materi referensi dari dosen, satu lagi adalah pengerjaan tugas menggunakan data riil dari Tugas 1.

## Isi Folder

| File | Keterangan |
|---|---|
| [`Tugas_2_ADT_BBCA.ipynb`](Tugas_2_ADT_BBCA.ipynb) | **Tugas yang dikerjakan.** Analisis time series pada data Harga Penutupan Bulanan Saham BBCA (data Tugas 1). |
| [`Analisis_Data_Timeseries_2.ipynb`](Analisis_Data_Timeseries_2.ipynb) | **Materi dari Bu Ade** (Google Classroom). Kumpulan contoh syntax Python dengan data simulasi, dipakai sebagai referensi/acuan cara penulisan kode. |
| [`data_BBCA_bulanan.csv`](data_BBCA_bulanan.csv) | Data mentah: harga penutupan bulanan saham BBCA, Jan 2023 – Agu 2026 (44 observasi), dari Tugas 1. |

---

## 1. `Tugas_2_ADT_BBCA.ipynb` — Notebook Tugas

Notebook ini menjawab 6 poin tugas menggunakan data BBCA (bukan data simulasi), dengan gaya syntax mengacu pada contoh Bu Ade:

1. **White Noise** — uji apakah data berperilaku acak murni (pakai Ljung-Box Test).
2. **Random Walk** — cek apakah harga BBCA mengikuti pola $Y_t = Y_{t-1} + \varepsilon_t$.
3. **ACF / PACF** — plot autokorelasi pada data level dan data hasil differencing.
4. **Dekomposisi** — model aditif, multiplikatif, dan STL (robust).
5. **Uji Stasioneritas** — ADF & KPSS pada data level, lalu differencing, lalu diuji ulang.
6. **Invertibilitas** — fit model ARIMA(0,1,1), cek invertibilitas koefisien MA lewat `ArmaProcess.isinvertible`.

Ringkasan temuan utama (sudah dijalankan, hasil ada di dalam notebook):

- Data **level** BBCA bukan white noise dan **tidak stasioner** (ADF & KPSS sepakat).
- **First difference**-nya berperilaku seperti white noise → data konsisten sebagai **Random Walk**.
- Setelah **differencing 1x (d=1)**, data menjadi **stasioner** (ADF & KPSS sepakat) — tidak perlu differencing kedua.
- Model MA(1) hasil fit terhadap data BBCA terbukti **invertibel** (akar polinomial MA = -6.32, di luar lingkaran satuan).

**Yang masih perlu dilengkapi manual:** isi Nama, NIM, dan Kelas di cell pertama notebook (masih placeholder).

**Cara menjalankan ulang:**
```bash
pip install pandas numpy matplotlib statsmodels
```
lalu jalankan seluruh cell (Run All) — data CSV sudah ada satu folder dengan notebook ini, jadi tidak perlu ubah path.

---

## 2. `Analisis_Data_Timeseries_2.ipynb` — Materi Referensi Dosen

Notebook ini **bukan** hasil pengerjaan tugas, melainkan bahan ajar dari Bu Ade yang berisi contoh-contoh kode dengan **data simulasi** (`np.random`) untuk menunjukkan konsep secara teoritis:

- Simulasi dekomposisi aditif & multiplikatif + STL robust (dengan outlier buatan).
- Simulasi White Noise dan Random Walk (termasuk Random Walk with Drift).
- Simulasi data tren + musiman untuk demonstrasi plot ACF.
- Simulasi proses AR(2) untuk demonstrasi plot PACF.
- Simulasi data non-stasioner untuk demonstrasi Uji ADF & KPSS.
- Simulasi proses MA(1) invertibel vs non-invertibel untuk demonstrasi `ArmaProcess.isinvertible`.

Fungsinya di tugas ini murni sebagai **acuan syntax/struktur kode** — setiap konsep di notebook Bu Ade inilah yang direplikasi (dengan penyesuaian) pada notebook tugas di atas, tetapi diterapkan ke data BBCA yang riil, bukan data hasil `np.random`.

---

## Alur Kerja

```
Analisis_Data_Timeseries_2.ipynb (contoh dosen, data simulasi)
              │  dipelajari & dijadikan acuan syntax
              ▼
data_BBCA_bulanan.csv (data riil Tugas 1)
              │  dianalisis dengan pola yang sama
              ▼
Tugas_2_ADT_BBCA.ipynb (hasil pengerjaan tugas)
```
