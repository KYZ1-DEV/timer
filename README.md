# Konsep
Buatkan saya sebuah web app dalam 1 file (index.html) menggunakan:
- HTML
- TailwindCSS (via CDN)
- JavaScript (vanilla, tanpa framework)

Kriteria utama:
- Desain RESPONSIVE (mobile-first)
- Tampilan elegan, modern, clean
- Menggunakan efek GLASSMORPHISM (blur, transparansi, shadow halus)
- UI smooth dengan animasi ringan (transition, fade, scale)

Fitur utama aplikasi:
1. TIMER BELAJAR (countdown timer)
   - User bisa input durasi (menit)
   - Tombol: Start, Pause, Reset
   - Tampilan waktu besar di tengah (format mm:ss)
   - Timer tidak membuat text baru, tetapi update di tempat (live changing)

2. MODE POMODORO
   - Default:
     - Fokus: 25 menit
     - Istirahat: 5 menit
   - Setelah 4 sesi fokus → istirahat panjang (15 menit)
   - Indikator sesi (misalnya: Session 1/4)
   - Auto switch antara fokus & break
   - Notifikasi (alert dan sound menggunakan js) saat sesi selesai 

3. UI/UX
   - Card utama di tengah dengan efek glassmorphism:
     - backdrop-blur
     - bg-white/10 atau transparan
     - border tipis
   - Background gradient modern (dark mode lebih diutamakan)
   - Ikon sederhana (boleh pakai emoji atau SVG)
   - Button rounded, smooth hover effect

4. FITUR TAMBAHAN
   - Toggle antara:
     - Mode Timer biasa
     - Mode Pomodoro
   - Progress bar animasi
   - suara notifikasi/alarm menggunakan JS 

5. TEKNIS
   - Semua dalam satu file index.html
   - Gunakan Tailwind CDN
   - Code harus rapi dan mudah dipahami
   - Gunakan struktur yang clean (pisahkan HTML, style, script)

6. BONUS 
   - Simpan state timer di localStorage (biar tidak reset saat reload)


Output:
- Berikan kode lengkap index.html
- Tidak perlu penjelasan panjang, fokus ke kode yang siap jalan
