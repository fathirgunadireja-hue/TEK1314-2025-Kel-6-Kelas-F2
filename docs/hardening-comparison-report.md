# Hardening Comparison Report
## Perbandingan Kondisi Sebelum dan Sesudah Hardening (Phase 1-3)

## Informasi Umum

- Proyek: TEK1314-2025-Kel-6-Kelas-F2
- Skenario: Brute Force & Dictionary Attack
- Target: Ubuntu Server (192.168.6.10)
- Attacker: 172.16.6.10
- Monitoring: Security Onion

## Tujuan Report

Report ini menjelaskan perubahan kondisi keamanan sistem sebelum hardening, sesudah hardening, serta validasi hasilnya pada Phase 2 dan Phase 3.

## Kondisi Sebelum Hardening

Pada kondisi awal, target masih memiliki exposure layanan yang lebih luas dan proteksi host belum optimal.

### Indikator Utama

1. Ping antar host masih bebas tanpa pembatasan.
2. Service/port masih mudah terdeteksi.
3. Konfigurasi firewall belum ketat.

### Evidence (Phase 1 - Pre-Hardening)

- ![Pre-Hardening Test Ping](<phase-1-baseline/assets/07-Pre-Hardening-Test Ping Target Attacker.png>)
- ![Pre-Hardening Hasil ss](<phase-1-baseline/assets/08-Pre-Hardening- hasil ss.png>)
- ![Pre-Hardening Nmap SSH](<phase-1-baseline/assets/09-Pre-Hardening Nmap ssh.png>)
- ![Pre-Hardening UFW Status](<phase-1-baseline/assets/09-Pre-Hardening-ufw status verbose.png>)

## Proses Hardening

Hardening dilakukan pada sisi SSH, firewall, dan kernel untuk menurunkan attack surface.

### Kontrol yang Diterapkan

1. Aktivasi UFW dan verifikasi rule.
2. SSH dipindah ke port non-default 2222.
3. Penyesuaian konfigurasi SSH untuk pembatasan autentikasi.
4. Hardening kernel melalui sysctl.
5. Validasi dengan monitoring Fail2Ban.

### Evidence (Phase 1 - Proses Hardening)

- ![Aktivasi UFW dan Verifikasi Port](<phase-1-baseline/assets/10-Aktivasi UFW dan Verifikasi Port.png>)
- ![Proses Hardening](<phase-1-baseline/assets/11-Proses Hardening.png>)
- ![Kernel Hardening Sysctl](<phase-1-baseline/assets/12-Kernel-Hardening-Sysctl.png>)
- ![Pengujian SSH Port 2222 dan Monitoring Fail2Ban](<phase-1-baseline/assets/13-Pengujian SSH Port 2222 dan Monitoring Fail2Ban.png>)
- ![Test Hardening](<phase-1-baseline/assets/14-Test Hardening.png>)

## Kondisi Sesudah Hardening (Validasi Phase 2)

Setelah hardening, exposure layanan lebih terbatas dan kontrol proteksi lebih terlihat saat diuji.

### Hasil Validasi

1. Port yang terbuka lebih terkontrol.
2. SSH berjalan pada port 2222.
3. Percobaan brute force dapat diamati sebagai bagian uji keamanan.

### Evidence (Phase 2 - Vulnerability Assessment)

- ![Validasi Port Terbuka dengan Nmap](<phase-2-va/assets/01-Validasi Port Terbuka dengan Nmap.png>)
- ![Validasi Port SSH dengan Nmap](<phase-2-va/assets/02- Validasi Port  SSH dengan Nmap .png>)
- ![Percobaan Brute Force SSH pada Port 2222](<phase-2-va/assets/03-Percobaan Brute Force SSH pada Port 2222.png>)

## Respons Insiden (Phase 3)

Pada fase insiden, serangan brute force dideteksi dan ditangani menggunakan kombinasi monitoring serta kontrol host-based security.

### Hasil Respons

1. Aktivitas brute force terdeteksi di monitoring.
2. Fail2Ban melakukan pemblokiran sumber serangan.
3. Kontrol keamanan disesuaikan untuk menekan percobaan lanjutan.

### Evidence (Phase 3 - Incident Response)

- ![Brute Force dan Pemblokiran Fail2Ban](<phase-3-incident/assets/01-Percobaan Brute Force SSH pada Port 2222 dan Pemblokiran oleh Fail2Ban.png>)
- ![Simulasi Serangan Berhasil dan Monitoring](<phase-3-incident/assets/02-Simulasi Serangan Berhasil dan Monitoring.png>)
- ![Simulasi Serangan Gagal dan Monitoring](<phase-3-incident/assets/03-Simulasi Serangan Gagal dan Monitoring.png>)

## Perbandingan Ringkas

| Aspek | Sebelum Hardening | Sesudah Hardening |
|------|-------------------|-------------------|
| SSH Port | Default/mudah ditebak | Non-default (2222) |
| Firewall | Belum ketat | UFW aktif dengan rule terbatas |
| Monitoring Keamanan | Belum tervalidasi | Tervalidasi via Security Onion |
| Brute Force Handling | Rentan | Ada deteksi dan ban via Fail2Ban |
| Konfigurasi Kernel | Default | Hardened via sysctl |

## Kesimpulan

Hardening pada target server berhasil menurunkan exposure layanan dan meningkatkan ketahanan terhadap brute force. Validasi pada Phase 2 dan simulasi incident pada Phase 3 menunjukkan kontrol keamanan berjalan dan dapat diobservasi secara terukur.

Kombinasi kontrol yang diterapkan (SSH non-default, UFW, Fail2Ban, kernel hardening, dan monitoring SIEM) terbukti efektif dalam menangani skenario serangan brute force pada lingkungan lab.
