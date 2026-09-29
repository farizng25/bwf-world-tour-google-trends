# 🏸 BWF World Tour Google Trends Indonesia

Analisis hubungan antara jadwal turnamen **Badminton World Federation** dengan minat pencarian daring masyarakat Indonesia terhadap kata kunci **"badminton"** pada periode **April 2025 – Maret 2026**.

## 🎯 Tujuan

- Mengumpulkan data tren pencarian mingguan dari Google Trends (API `pytrends`).
- Mengumpulkan jadwal turnamen BWF melalui *web scraping* Wikipedia Bahasa Indonesia.
- Menganalisis pola jadwal turnamen per bulan dan level, serta dampaknya terhadap tren pencarian.

## 🗂️ Sumber Data

| Data | Metode | Detail |
|------|--------|--------|
| Tren pencarian | API `pytrends` (v4.9.2) | Keyword `badminton`, `geo='ID'`, indeks mingguan skala 0–100 |
| Jadwal turnamen | Web scraping (`requests` + `pandas.read_html`) | Halaman Wikipedia *Tur Dunia BWF* 2025 & 2026 |

## ⚙️ Alur Kerja

1. **Data gathering**: ambil data Google Trends dan scrape tabel jadwal BWF.
2. **Cleaning**: hapus duplikat, ekstrak level turnamen dengan regex, ubah tanggal teks Bahasa Indonesia ke `datetime`, filter periode Apr 2025 – Mar 2026 (**39 turnamen**).
3. **Merge**: setiap minggu tren diberi label level turnamen tertinggi dalam jendela ±4 hari (*window matching*).
4. **Analisis & visualisasi**: statistik deskriptif, bar chart bulanan, pie chart level, dan overlay chart tren vs turnamen.

## 📊 Temuan Utama

- **Semakin tinggi level turnamen, semakin tinggi rata-rata indeks pencarian.**

| Level | Rata-rata indeks |
|-------|:---------------:|
| Super 1000 | 77.0 |
| Super 750 | 71.5 |
| Super 500 | 63.2 |
| Super 300 | 57.8 |
| Super 100 | 52.4 |
| Tanpa turnamen | 48.9 |

- **Puncak pencarian** terjadi pada **Oktober 2025** (indeks 100), bertepatan dengan padatnya jadwal September–Oktober.
- **Terendah** pada **Maret 2026**, saat agenda turnamen besar minim.
- **Anomali April & Agustus 2025**: lonjakan pencarian tanpa turnamen World Tour, dipicu **Sudirman Cup** dan **Kejuaraan Dunia BWF**.
- Jadwal BWF lebih padat di semester kedua (September–Desember).

## 🛠️ Tech Stack

`Python` · `pandas` · `pytrends` · `requests` · `matplotlib` · `seaborn` · `re`

## 🚀 Cara Menjalankan

```bash
git clone https://github.com/<username>/<nama-repo>.git
cd <nama-repo>
pip install pandas pytrends requests lxml matplotlib seaborn
jupyter notebook
```

## ⚠️ Keterbatasan

- Hanya satu kata kunci (`badminton`) dan wilayah Indonesia.
- Jadwal hanya dari Wikipedia; analisis bersifat deskriptif (belum ada uji signifikansi statistik).
- Faktor lain seperti performa atlet Indonesia dan berita viral belum dimodelkan.

## 🔭 Pengembangan Selanjutnya

- Tambah keyword "bulu tangkis".
- Validasi silang dengan data penonton/engagement media sosial.
- Prediksi tren dengan ARIMA atau Prophet.
- Analisis sentimen berita turnamen.

## 👤 Penulis

**Fariz Naufal Gustoro**
