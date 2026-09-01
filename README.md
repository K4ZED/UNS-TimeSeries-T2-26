# Tugas 2: Analisis Data Time Series

Ini repo tugas 2 mata kuliah Analisis Data Timeseries. Ada dua notebook di dalamnya, jadi aku jelasin dulu biar nggak bingung.

`Analisis_Data_Timeseries_2.ipynb` itu bukan punyaku, itu file dari Bu Ade yang dibagikan di Google Classroom. Isinya contoh-contoh syntax Python pakai data simulasi (dibikin pakai `np.random`), buat nunjukkin konsep white noise, random walk, dekomposisi, ACF/PACF, uji stasioner, sampai invertibilitas secara teori. Aku jadiin ini acuan gaya nulis kode.

`Tugas_2_ADT_BBCA.ipynb` itu punyaku, hasil pengerjaan tugasnya. Datanya pakai data dari Tugas 1, harga penutupan bulanan saham BBCA (ada di `data_BBCA_bulanan.csv`, Januari 2023 sampai Agustus 2026, 44 data bulanan). Jadi bukan data simulasi kayak punya Bu Ade, tapi data beneran, terus dianalisis pakai enam poin yang diminta:

1. White Noise, dicek pakai uji Ljung-Box.
2. Random Walk, cek apakah harga BBCA-nya mengikuti pola $Y_t = Y_{t-1} + \varepsilon_t$.
3. ACF/PACF, di data asli sama data yang sudah di-difference.
4. Dekomposisi, aditif, multiplikatif, sama STL robust.
5. Uji stasioner (ADF & KPSS), kalau belum stasioner di-difference terus diuji ulang.
6. Invertibilitas, dari model ARIMA yang di-fit ke data.

Hasilnya kalau mau diringkas: data harga BBCA di level aslinya bukan white noise dan nggak stasioner (ADF sama KPSS sepakat soal itu). Tapi kalau di-difference satu kali, hasilnya jadi mirip white noise dan stasioner, jadi kesimpulannya data ini kelakuannya kayak random walk. Nggak perlu di-difference dua kali. Terus model MA(1) yang di-fit ke datanya juga invertibel (akarnya di luar lingkaran satuan).

Notebook-nya sudah dijalankan semua jadi outputnya (plot, angka uji) sudah kelihatan tanpa perlu run ulang. Kalau mau run ulang sendiri tinggal install dulu library-nya:

```bash
pip install -r requirements.txt
```

terus run all cell aja, csv-nya sudah satu folder sama notebook-nya jadi nggak perlu ganti path.
