# 🏁 Tugas Akhir (TA) - Final Project

**Nama Mahasiswa**: Wan Sabrina Mayzura  
**NRP**: 5025211023  
**Judul TA**: Interpretasi Otomatis Citra Medis Otak Menggunakan Kombinasi Model Klasifikasi Berjenjang Dan *Image Captioning*  
**Dosen Pembimbing**: Prof. Drs.Ec. Ir. Riyanarto Sarno, M.Sc.,Ph.D.  
**Dosen Ko-pembimbing**: Dr. Kelly Rossa Sungkono, S.Kom.,M.Kom.

---

## 🎯 Deskripsi Program

Program ini merupakan sistem otomatis untuk interpretasi citra medis otak yang menggabungkan proses **klasifikasi berjenjang** dan **image captioning**. Melalui tahapan klasifikasi berjenjang (bertingkat), model ini mampu mengenali berbagai informasi penting dari citra medis, seperti modalitas pencitraan, orientasi bidang potong (plane), status abnormalitas, hingga tipe tumor secara spesifik. Selanjutnya, hasil klasifikasi tersebut diintegrasikan ke dalam proses captioning untuk menghasilkan deskripsi klinis yang lebih kontekstual dan informatif.

---

## 📺 Demo Aplikasi  

[![Demo Aplikasi](https://i.ytimg.com/vi/dLTcBD8TKZA/maxresdefault.jpg)](https://youtu.be/dLTcBD8TKZA)  
*Klik gambar di atas untuk menonton demo, skip ke menit 4:10 jika ingin langsung melihat demonstrasi dashboard.*

---

## 🛠 Panduan Instalasi & Menjalankan Software  

### Prasyarat  
Daftar dependensi:
  - Python 3.10+
  - pip
  - GPU (direkomendasikan)
  - Akun [Hugging Face](https://huggingface.co/) (untuk menyimpan model, opsional apabila model disimpan dan digunakan secara lokal)

### Langkah-langkah  
1. **Clone Repository**  
   ```bash
   git clone https://github.com/Informatics-ITS/ta-wansabrina.git
   cd ta-wansabrina
   ```
2. **Dependensi**  
   Tidak ada requirements.txt terpisah. Semua dependensi sudah disebutkan dan diinstal langsung di dalam masing-masing notebook menggunakan perintah pip.

3. **Urutan Eksekusi Notebook**  
   Notebook dijalankan secara berurutan:
   1. **Notebook 1** – Fine-tuning klasifikasi citra otak.
   2. **Notebook 2** – Fine-tuning model image captioning.
   3. **Notebook 3** – Integrasi klasifikasi dan captioning menjadi satu sistem.

   📌 Catatan: Jika ingin langsung menjalankan Notebook 3, tidak masalah karena model-model dari Notebook 1 dan 2 sudah diunggah ke Hugging Face dan otomatis akan diunduh saat notebook dijalankan.

4. **Alternatif: Langsung Gunakan Demo Interaktif di Hugging Face Spaces**  
   👉 [Coba Space Hugging Face di sini](https://huggingface.co/spaces/bombshelll/brain-hierarchical-captioning)

   Jika ingin mencoba langsung, bisa menggunakan test data yang telah disediakan di folder berikut:  
   📁 [Test Data](https://github.com/Informatics-ITS/ta-wansabrina/tree/main/Test%20Data)

   Output yang dihasilkan dari interface ini meliputi:
   * **Keyword hasil klasifikasi berjenjang** yang digunakan sebagai input tambahan pada captioning.
   * **Deskripsi otomatis (caption)** dari citra medis otak dengan dan tanpa integrasi klasifikasi.
   * **Skor evaluasi BLEU** untuk membandingkan kualitas deskripsi.

## 📚 Dokumentasi Tambahan
Berikut adalah rincian lengkap dari masing-masing notebook:
- ### Notebook 1 – Fine-tuning Klasifikasi Otak
   Melatih model klasifikasi individual, diantaranya:
   * Abnormalitas otak
   * Modalitas citra (T1, T2, dll)
   * Plane (axial, sagittal, coronal)
   * Jenis tumor (glioma, meningioma, dll)

   #### Model dan Dataset yang Digunakan
   | Kategori| Model Pretrained| Link Sumber Dataset|
   |------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
   | Abnormalities    | [swin-brain-abnormalities-classification](https://huggingface.co/bombshelll/swin-brain-abnormalities-classification)        | [brain_normal_vs_abnormal](https://huggingface.co/datasets/bombshelll/brain_normal_vs_abnormal)                                                  |
   | Modality         | [swin-brain-modality-classification](https://huggingface.co/bombshelll/swin-brain-modality-classification)                  | [brain_modality](https://huggingface.co/datasets/bombshelll/brain_modality)                                                                      |
   | Plane            | [swin-brain-plane-classification](https://huggingface.co/bombshelll/swin-brain-plane-classification)                        | [brain_plane](https://huggingface.co/datasets/bombshelll/brain_plane)                                                                            |
   | Tumor Type       | [swin-brain-tumor-type-classification](https://huggingface.co/bombshelll/swin-brain-tumor-type-classification)              | [brain_14_tumor_classes](https://huggingface.co/datasets/bombshelll/brain_14_tumor_classes)                                                      |


- ### Notebook 2 – Fine-tuning Model Image Captioning  
   Melatih model image captioning berbasis ViT + BioMedBERT untuk menghasilkan deskripsi klinis dari citra otak.

   #### Model dan Dataset untuk Image Captioning
   | Dataset        | Model Pretrained                                                                                                 | Link Sumber Dataset                                                                                                  |
   |-----------------|------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|
   | ROCO-Brain      | [ViT_BioMedBERT_Captioning_ROCO](https://huggingface.co/bombshelll/ViT_BioMedBert_Captioning_ROCO)              | [Kaggle](https://www.kaggle.com/datasets/hieugiaosu/roco-brain), [Hugging Face](https://huggingface.co/datasets/bombshelll/rocobrain) |


- ### Notebook 3 – Integrasi Sistem Klasifikasi & Captioning  
   Notebook ini digunakan untuk melakukan beberapa hal:
   * Menggabungkan hasil klasifikasi individual menjadi klasifikasi berjenjang.
   * Mengekstraksi keyword dari hasil klasifikasi berjenjang.
   * Menggunakan keyword tersebut pada proses generate caption menggunakan fine-tuned captioning model dari notebook 2.
   * Melakukan inference dan evaluasi terhadap caption hasil gabungan tersebut.

## ⁉️ Pertanyaan?

Hubungi:
- Penulis: wansabrina.ws@gmail.com
- Pembimbing Utama: riyanarto@if.its.ac.id
- Ko-pembimbing: kelly@its.ac.id
