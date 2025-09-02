# Mengenal Outlier

## Apa Itu Outlier?

Secara sederhana, **outlier** adalah sebuah data dengan perbedaan nilai yang cukup signifikan dengan data lainnya.

Akibatnya **Outlier** dapat menggangu dan merusak perhitungan akhir data.
---

## Metode Umum untuk Mendeteksi Outlier

Metode yang paling umum digunakan untuk mendeteksi outlier ada dua, yaitu **Interquartile Range (IQR) Score** dan **Z-Score**.

### 1. Metode Interquartile Range (IQR)

Metode ini adalah metode yang lebih populer karena tidak terpengaruh oleh seberapa tinggi perbedaan data. Metode ini mengambil titik tengah dari data.

**Cara Kerjanya:**
1.  **Urutkan data** dari yang terkecil hingga terbesar.
2.  **Bagi data menjadi empat bagian sama besar (kuartil)**.
    * **Q1 (Kuartil 1):** Nilai tengah dari setengah data bagian bawah.
    * **Q3 (Kuartil 3):** Nilai tengah dari setengah data bagian atas.
3.  **Hitung IQR:** Selisih antara Q3 dan Q1. `IQR = Q3 - Q1`.
4.  **Tentukan "Pagar" Batas Atas dan Bawah:**
    * Batas Bawah = `Q1 - (1.5 * IQR)`
    * Batas Atas = `Q3 + (1.5 * IQR)`
5.  Setiap data yang berada **di luar** rentang pagar ini dianggap sebagai *outlier*.

**Contoh:**
Misalkan kita punya data nilai ujian: `[65, 70, 72, 75, 78, 80, 82, 85, 90, 150]`
Angka `150` terlihat mencurigakan. Mari kita buktikan dengan IQR.

* **Q1:** `72`
* **Q3:** `85`
* **Hitung IQR:** `85 - 72 = 13`
* **Hitung Batas:**
    * Batas Bawah: `72 - (1.5 * 13) = 72 - 19.5 = 52.5`
    * Batas Atas: `85 + (1.5 * 13) = 85 + 19.5 = 104.5`

**Kesimpulan:** Karena nilai `150` berada di atas batas atas (`104.5`), maka **150 adalah outlier**.

### 2. Metode Z-Score

Metode ini mengukur seberapa jauh sebuah titik data dari nilai rata-rata dalam satuan simpangan baku (standar deviasi).

**Cara Kerjanya:**
1.  **Hitung nilai rata-rata (μ)** dan **simpangan baku (σ)** dari seluruh data.
2.  Untuk setiap titik data (X), hitung **Z-Score**-nya dengan rumus: `Z = (X - μ) / σ`.
3.  Tentukan ambang batas. Umumnya, titik data dengan Z-Score **di atas 3** atau **di bawah -3** dianggap sebagai *outlier*.

**Contoh:**
Menggunakan data yang sama: `[65, 70, 72, 75, 78, 80, 82, 85, 90, 150]`

* **Rata-rata (μ):** `84.7`
* **Simpangan Baku (σ):** `25.3`
* **Hitung Z-Score untuk nilai 150:**
    * `Z = (150 - 84.7) / 25.3 = 65.3 / 25.3 ≈ 2.58`

**Kesimpulan:** Dalam kasus ini, Z-Score `2.58` tidak melewati ambang batas 3. Ini menunjukkan salah satu kelemahan Z-Score: nilai rata-rata dan simpangan baku itu sendiri terpengaruh oleh *outlier*, sehingga terkadang bisa "menyamarkan" *outlier* tersebut. Metode IQR umumnya lebih dapat diandalkan.

---
