# Onboarding Buddy System

AI Agent pendamping karyawan baru, dibuat dengan IBM Bob sebagai Capstone Project.

Catatan: seluruh data perusahaan (PT Nusantara Digital, jadwal, kebijakan, kontak) adalah data simulasi untuk keperluan demonstrasi.

## Ringkasan

Onboarding Buddy System adalah AI Agent yang berperan sebagai "buddy" virtual bagi karyawan baru selama minggu-minggu pertama bekerja. Tujuannya membantu karyawan baru memahami budaya perusahaan, kebijakan, alat kerja, dan tugas awal tanpa harus selalu bertanya ke HR atau atasan.

Fungsi utama agent:

- Menjawab pertanyaan seputar perusahaan berdasarkan basis pengetahuan di prompt.
- Menyusun checklist dan jadwal onboarding sesuai peran dan hari kerja.
- Menjelaskan istilah internal.
- Mengarahkan ke HR, IT, atau atasan bila informasi tidak tersedia.

## Problem Statement

Informasi onboarding biasanya tersebar di dokumen PDF, email, chat grup, wiki, dan penjelasan lisan. Karyawan baru jadi harus bertanya berulang untuk hal dasar, dan sering merasa canggung. Akibatnya waktu adaptasi lebih lama. Di sisi lain, HR dan buddy manusia menghabiskan waktu menjawab pertanyaan yang sama. Bila tidak ditangani, risiko turnover di masa awal kerja meningkat dan beban HR bertambah seiring jumlah karyawan baru.

## Target Users

- Pengguna utama: karyawan baru dalam 90 hari pertama kerja.
- Pengguna sekunder: tim HR dan buddy manusia.

## Arsitektur Prompt

Prompt terdiri dari enam layer:

1. Peran: identitas dan gaya bahasa Buddy.
2. Konteks: data perusahaan sebagai basis pengetahuan.
3. Tugas: hal-hal yang boleh dikerjakan agent.
4. Batasan: larangan mengarang informasi, memberi keputusan HR final, dan membagikan data pribadi.
5. Format jawaban: ringkas, langkah bernomor, dan ditutup dengan "Langkah berikutnya:".
6. Fallback dan eskalasi: perilaku saat informasi tidak tersedia.

Prompt lengkap ada di [prompt.md](prompt.md).

## Proses Penyusunan Prompt

Prompt disusun bertahap, dimulai dari peran, lalu ditambah konteks perusahaan, tugas, batasan, format jawaban, dan fallback. Setelah semua layer lengkap, prompt dikirim ke IBM Bob sebagai satu prompt final. (Bila ada perbaikan setelah pengujian, tambahkan di sini dan di bagian Catatan Perbaikan pada [test-cases.md](test-cases.md).)

## Cara Menggunakan

1. Buka IBM Bob dan buat percakapan baru.
2. Salin seluruh isi blok kode di [prompt.md](prompt.md) dan kirim sebagai prompt.
3. Agent akan menyapa dan menanyakan nama, posisi, dan hari kerja ke berapa.
4. Coba skenario pada [test-cases.md](test-cases.md).

## Struktur Repository

```
onboarding-buddy-system/
├── README.md
├── prompt.md
├── test-cases.md
└── screenshots/
    ├── prompt-ibm-bob.png
    └── hasil-pengujian.png
```

## Pengembangan Lanjutan

- Integrasi dengan Slack atau Microsoft Teams.
- Integrasi dengan HRIS agar checklist terhubung dengan status tugas yang sebenarnya.
- Pengingat otomatis untuk tugas onboarding yang belum selesai.
- Dukungan dua bahasa dan kuis singkat untuk menguji pemahaman kebijakan.
- Dashboard HR berisi pertanyaan yang paling sering diajukan.
