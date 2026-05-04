# Vulnerability Assessment Report - Phase 2

## Informasi Umum

- Proyek: TEK1314-2025-Kel-6-Kelas-F2
- Fase: Phase 2 - Vulnerability Assessment
- Target: Ubuntu Server (192.168.6.10)
- Attacker: Ubuntu Cybersecurity Workstation (172.16.6.10)
- Layanan Fokus: SSH (port 2222)

## Tujuan Phase 2

1. Memvalidasi surface exposure pada target setelah hardening.
2. Mengidentifikasi port dan service yang masih dapat diakses.
3. Menguji efektivitas kontrol keamanan awal terhadap percobaan brute force.

## Metode Pengujian

- Port scanning dan service discovery menggunakan Nmap.
- Uji akses ke layanan SSH pada port non-default (2222).
- Simulasi brute force terbatas menggunakan Hydra untuk validasi kontrol autentikasi.

## Temuan Utama

1. Port yang terpapar pada target telah berkurang signifikan.
2. Layanan SSH berjalan pada port 2222 (non-default).
3. Percobaan brute force menunjukkan pentingnya kombinasi kontrol autentikasi, UFW, dan Fail2Ban.

## Evidence

- ![Validasi Port Terbuka dengan Nmap](<assets/01-Validasi Port Terbuka dengan Nmap.png>)
- ![Validasi Port SSH dengan Nmap](<assets/02- Validasi Port  SSH dengan Nmap .png>)
- ![Percobaan Brute Force SSH pada Port 2222](<assets/03-Percobaan Brute Force SSH pada Port 2222.png>)

## Kesimpulan

Phase 2 menunjukkan bahwa hardening awal telah menurunkan exposure layanan. Hasil assessment menjadi dasar untuk Phase 3 dalam simulasi insiden dan evaluasi respons keamanan.
