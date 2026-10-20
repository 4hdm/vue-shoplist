<div align="center">

  # 🛒 VueShop List

  **Aplikasi Catatan Belanjaan Modern, Cepat, dan Interaktif berbasis Vue 3 & Tailwind CSS**

  [![Vue 3](https://img.shields.io/badge/Vue.js-3.x-4FC08D?style=for-the-badge&logo=vuedotjs&logoColor=white)](https://vuejs.org/)
  [![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3.x-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)
  [![License](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)](LICENSE)

  [Demo Aplikasi](#) · [Laporkan Bug](https://github.com/username/repository-name/issues) · [Minta Fitur](https://github.com/username/repository-name/issues)

</div>

---

## 📌 Ringkasan

**VueShop List** adalah aplikasi manajemen daftar belanja harian yang dirancang dengan antarmuka yang bersih, intuitif, dan responsif. Aplikasi ini membantu pengguna mencatat, memfilter, serta memantau progres belanjaan secara *real-time* tanpa khawatir kehilangan data saat halaman direfresh.

---

## ✨ Fitur Unggulan

- 🛍️ **Manajemen Belanjaan**: Tambah barang beserta kuantitasnya dan tandai barang yang sudah dibeli dengan mudah.
- 📊 **Progress Bar Dinamis**: Indikator visual interaktif yang menampilkan persentase penyelesaian belanja.
- 🔍 **Pencarian & Filter Pintar**: Cari barang berdasarkan nama dan filter berdasarkan status (*Semua*, *Belum Dibeli*, *Sudah Dibeli*).
- 💾 **Penyimpanan Otomatis (`localStorage`)**: Data belanjaan Anda tersimpan secara otomatis di browser.
- 🧹 **Hapus Cepat (*Clear Completed*)**: Bersihkan semua item yang sudah selesai hanya dengan satu klik.
- 🎨 **Desain Modern & Animasi Halus**: Tampilan *Glassmorphism* yang elegan dan transisi daftar item yang mulus.
- 📱 **Responsif**: Tampil sempurna di perangkat *desktop*, *tablet*, maupun *smartphone*.

---

## 🛠️ Teknologi yang Digunakan

- **Framework**: [Vue 3](https://vuejs.org/) (Composition API & `<script setup>`)
- **Styling**: [Tailwind CSS](https://tailwindcss.com/)
- **State Management**: Vue Reactivity System (`ref`, `computed`, `watch`)
- **Icons & Badges**: Shields.io

```

##📂 Struktur Folder
├── src/
│   ├── assets/        # File aset (CSS, gambar, logo)
│   ├── components/    # Komponen Reusable Vue
│   ├── App.vue        # Komponen Utama VueShop List
│   └── main.js        # Entry point aplikasi
├── public/            # Aset publik
├── package.json       # Konfigurasi dependensi & script
└── README.md          # Dokumentasi proyek

```

###  📸 Tampilan Aplikasi

| Tampilan Utama | Fitur Filter & Search |
| :---: | :---: |
| <img src="./screenshots/home.png" width="300" style="border-radius: 8px;" /> | <img src="./screenshots/filter.png" width="300" style="border-radius: 8px;" /> |
| *Daftar Belanjaan* | *Pencarian & Status* |
