
# Sistem Pelacakan dan Penghitungan Kendaraan dengan YOLOv8 & DeepSORT

![Python](https://img.shields.io/badge/Python-3.9%2B-blue.svg)

Proyek ini adalah sebuah prototipe sistem berbasis visi komputer untuk mendeteksi, melacak, dan menghitung kendaraan dari rekaman video. Menggunakan arsitektur modern **YOLOv8** untuk deteksi dan **DeepSORT** untuk pelacakan, sistem ini mampu menganalisis lalu lintas secara otomatis dan menghasilkan laporan kuantitatif.

Proyek ini dikembangkan dalam lingkungan Google Colab untuk memanfaatkan akselerasi GPU gratis (T4).


## Fitur Utama

-   **Deteksi Multi-Kelas**: Mampu mendeteksi 4 jenis kendaraan utama: mobil, motor, bus, dan truk.
-   **Pelacakan Objek dengan ID Unik**: Setiap kendaraan yang terdeteksi diberikan ID unik yang konsisten selama terlihat di layar.
-   **Penghitungan Lalu Lintas Dua Arah**: Menghitung jumlah kendaraan yang bergerak naik dan turun melintasi garis virtual.
-   **Estimasi Kecepatan**: Memberikan perkiraan kecepatan setiap kendaraan dalam km/jam (memerlukan kalibrasi).
-   **Visualisasi Lengkap**: Menampilkan kotak pembatas, ID, jejak pergerakan, dan OSD (*On-Screen Display*) pada video hasil.
-   **Ekspor Laporan ke File Excel**: Secara otomatis menghasilkan file laporan `.xlsx` yang merangkum hasil penghitungan.
-   **Antarmuka Interaktif**: Dilengkapi widget di Jupyter Notebook untuk kemudahan penggunaan.

---

## Teknologi

-   **Python 3.9+**
-   **PyTorch**
-   **Ultralytics YOLOv8**
-   **DeepSORT**
-   **OpenCV**
-   **Pandas & Openpyxl**
-   **Jupyter Notebook / Google Colab**

---

## Struktur Folder

Untuk menjalankan proyek ini dengan benar, pastikan mengikuti struktur folder berikut di dalam Google Drive:

```

/content/drive/MyDrive/Proyek\_Object\_Tracking/
├── icons/
│   ├── car.png
│   ├── motorcycle.png
│   ├── bus.png
│   └── truck.png
├── output/
│   ├── (Folder ini akan berisi video hasil dan laporan Excel)
└── videos/
└── test\_video1.mp4

```

-   **`icons/`**: Simpan semua file ikon kendaraan (`.png` dengan latar belakang transparan).
-   **`output/`**: Folder ini akan dibuat secara otomatis untuk menyimpan semua hasil.
-   **`videos/`**: Tempatkan semua file video yang ingin Anda analisis di sini.

---

## Instalasi & Cara Penggunaan

Proyek ini dirancang untuk dijalankan di **Google Colab**.

1.  **Persiapan Google Drive**:
    -   Buat folder utama `Proyek_Object_Tracking` di `MyDrive`.
    -   Di dalamnya, buat folder `videos` dan `icons`.
    -   Unggah file-file video Anda ke folder `videos`.
    -   Unggah file-file ikon ke folder `icons`.

2.  **Buka Notebook di Google Colab**:
    -   Unggah dan buka file `object_tracking_with_yolo.ipynb` di Google Colab.
    -   Pastikan runtime diatur untuk menggunakan **GPU** (`Runtime` -> `Change runtime type` -> `T4 GPU`).

3.  **Jalankan Sel Secara Berurutan**:
    -   **Sel 1 (Instalasi)**: Akan menginstal semua library yang dibutuhkan seperti `ultralytics` dan `openpyxl`.
    -   **Sel 2 (Hubungkan Drive)**: Akan meminta otorisasi untuk mengakses Google Drive Anda.
    -   **Sel 3 (Setup DeepSORT)**: Akan mengunduh dan mengekstrak library DeepSORT secara otomatis.
    -   **Sel 4 (Implementasi Utama)**: Ini adalah sel utama di mana Anda akan berinteraksi dengan program.

4.  **Mulai Analisis**:
    -   Pada antarmuka widget yang muncul, **pilih video** dari dropdown.
    -   Atur tingkat **confidence** menggunakan slider.
    -   Klik tombol **"Mulai Proses"**.
    -   Tunggu hingga proses analisis selesai. Semua log, output, dan hasil akhir akan ditampilkan di bawah sel tersebut.

---

## 📄 Contoh Output

Setelah proses selesai, Anda akan mendapatkan:
1.  **Video Hasil**: Sebuah file video baru (`hasil_nama_video.mp4`) di dalam folder `output/` yang berisi semua visualisasi.
2.  **Laporan Excel**: Sebuah file Excel (`Laporan_nama_video.xlsx`) di folder `output/` yang berisi tabel ringkasan jumlah kendaraan per jenis dan per arah, lengkap dengan total.

---

## ⚠️ Keterbatasan

-   **Oklusi (Tumpang Tindih)**: Sistem mungkin kesulitan melacak objek jika tertutup oleh objek lain dalam waktu yang lama.
-   **Akurasi Kecepatan**: Estimasi kecepatan sangat bergantung pada kalibrasi manual `PPM_RATIO` dan sudut pandang kamera.
-   **Kebutuhan Komputasi**: Memerlukan GPU untuk pemrosesan yang efisien dan tidak dirancang untuk *real-time* pada perangkat keras standar.

---
