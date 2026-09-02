# Tugas 2 ADT

Repo tugas 2 mata kuliah Analisis Data Timeseries.

Terdapat dua notebook:

- `Analisis_Data_Timeseries_2.ipynb`: materi dari Bu Ade (Google Classroom), berisi contoh syntax dengan data simulasi. Dijadikan acuan penulisan kode.
- `L0223024_KenzaAthallah_Tugas2.ipynb`: notebook tugas yang dikumpulkan. Menggunakan data dari Tugas 1 (`data_BBCA_bulanan.csv`, harga penutupan bulanan saham BBCA periode 2023-2026).

Poin yang dianalisis pada notebook tugas: white noise, random walk, ACF/PACF, dekomposisi, uji stasioneritas (differencing bila belum stasioner), dan invertibilitas.

Ringkasan hasil: data pada level asli tidak stasioner. Setelah differencing satu kali, data menjadi stasioner dan berperilaku seperti random walk. Detail dan seluruh output ada di dalam notebook (sudah dijalankan).

Menjalankan ulang:
```
pip install -r requirements.txt
```
File CSV berada satu folder dengan notebook, sehingga path tidak perlu diubah.
