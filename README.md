# Mini Project Integrasi

## Deskripsi

Mini project ini merupakan implementasi pengolahan citra digital untuk melakukan verifikasi dokumen ijazah menggunakan OCR dan deteksi tanda tangan kepala sekolah.

Tahapan pengolahan citra yang digunakan meliputi:

* Konversi citra ke grayscale
* Image enhancement menggunakan Denoise + CLAHE
* Image sharpening
* Adaptive Thresholding
* Otsu Thresholding
* Pembacaan nomor ijazah menggunakan OCR
* Perhitungan Character Error Rate (CER)
* Thresholding pada area tanda tangan
* Operasi morfologi Opening dan Closing
* Perhitungan foreground pixel
* Penentuan status tanda tangan (PRESENT / ABSENT)

Program membandingkan hasil OCR dari beberapa metode enhancement untuk menentukan metode yang paling efektif berdasarkan nilai CER terendah.

---

## Teknologi yang Digunakan

* Python
* OpenCV
* NumPy
* Pandas
* Pytesseract
* Tesseract OCR
* Matplotlib

---

## How to Run

### 1. Clone Repository

Buka Command Prompt atau PowerShell, kemudian jalankan:

```bash
git clone https://github.com/askaasky/Tugas7_PCD_F1G124021.git
```

Kemudian masuk ke folder project:

```bash
cd Tugas7_PCD_F1G124021
```

*Sesuaikan URL repository jika nama repository GitHub yang digunakan berbeda.*

### 2. Siapkan Dataset

Masukkan citra ijazah ke dalam folder:

`Ijazah/`

Format citra yang didukung:

* JPG
* JPEG
* PNG
* BMP
* TIF
* TIFF

Nomor ijazah acuan yang digunakan untuk menghitung CER diatur pada variabel `GROUND_TRUTH` di dalam kode. Sesuaikan nilainya dengan nomor ijazah yang diuji.

Area tanda tangan juga harus disesuaikan dengan posisi tanda tangan pada citra yang digunakan.

### 3. Install Library

Install library yang diperlukan dengan perintah:

```bash
pip install opencv-python numpy pandas pytesseract matplotlib
```

### 4. Install Tesseract OCR

Program membutuhkan Tesseract OCR untuk membaca nomor ijazah. Pastikan Tesseract sudah terinstal pada komputer.

Lokasi Tesseract pada kode diatur melalui variabel:

```python
pytesseract.pytesseract.tesseract_cmd = (
    r"C:\Program Files\Tesseract-OCR\tesseract.exe"
)
```

Sesuaikan lokasi tersebut jika Tesseract terinstal di direktori yang berbeda.

### 5. Jalankan Program

Jalankan program menggunakan perintah:

```bash
python main.py
```

Sesuaikan `main.py` dengan nama file Python yang digunakan. Hasil pemrosesan akan disimpan pada folder `Hasil/`.

---

## Metode yang Digunakan

* **Denoise + CLAHE**
  Denoising digunakan untuk mengurangi noise pada citra, sedangkan CLAHE meningkatkan kontras lokal agar karakter lebih mudah dikenali.

* **Sharpening**
  Digunakan untuk mempertajam tepi dan detail karakter agar membantu proses OCR.

* **Adaptive Thresholding**
  Memisahkan objek dan latar belakang menggunakan nilai ambang yang menyesuaikan kondisi lokal piksel.

* **Otsu Thresholding**
  Menentukan nilai ambang secara otomatis berdasarkan distribusi intensitas citra.

* **Morphology Opening dan Closing**
  Opening membantu mengurangi noise kecil, sedangkan closing membantu menyambungkan bagian foreground yang terputus.

* **Optical Character Recognition (OCR)**
  Menggunakan Tesseract OCR untuk membaca nomor ijazah dari citra.

* **Character Error Rate (CER)**
  Digunakan untuk mengukur kesalahan hasil OCR dibandingkan dengan nomor ijazah acuan. Metode enhancement dengan CER terendah dianggap paling efektif pada pengujian tersebut.

* **Signature Detection**
  Keberadaan tanda tangan ditentukan berdasarkan jumlah dan persentase foreground pixel pada area tanda tangan setelah proses thresholding dan morfologi.

---

## Output

Output program berupa:

* Hasil OCR nomor ijazah
* Nilai CER untuk setiap metode enhancement
* Metode enhancement terbaik berdasarkan CER
* Status tanda tangan (PRESENT / ABSENT)
* Citra hasil enhancement
* Citra hasil thresholding
* Citra hasil morphology
* Histogram perbandingan citra
* File `hasil_verifikasi.csv`
* File `perbandingan_CER.csv`

Seluruh hasil pengolahan disimpan pada folder `Hasil/`.

---

## Dataset

Dataset yang digunakan berupa citra dokumen ijazah yang diletakkan pada folder `Ijazah/`.

Program mendukung pemrosesan beberapa citra dalam satu kali eksekusi. Nomor acuan untuk perhitungan CER dan area tanda tangan perlu disesuaikan dengan karakteristik citra yang digunakan.

---

## Author

* **Nama:** Yus Askia
* **NIM:** F1G124021
* **Mata Kuliah:** Pengolahan Citra Digital
* **Universitas:** Universitas Halu Oleo
