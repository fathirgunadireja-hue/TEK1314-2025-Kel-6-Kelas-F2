# Incident Response Report - Phase 3

## Informasi Umum

- Proyek: TEK1314-2025-Kel-6-Kelas-F2
- Fase: Phase 3 - Incident Response
- Jenis Insiden: Brute Force / Dictionary Attack pada SSH
- Target: Ubuntu Server (192.168.6.10:2222)
- Sumber Serangan: 172.16.6.10

## Ringkasan Insiden

Simulasi serangan brute force dilakukan terhadap layanan SSH pada port 2222. Aktivitas serangan terdeteksi pada monitoring Security Onion, kemudian direspons dengan kontrol pertahanan host seperti UFW dan Fail2Ban.

## Timeline Singkat

1. Serangan brute force dijalankan dari mesin attacker ke target SSH port 2222.
2. Security Onion menampilkan event dan indikator aktivitas SSH mencurigakan.
3. Fail2Ban memproses log `sshd` dan melakukan ban terhadap sumber serangan.
4. Dilakukan penyesuaian konfigurasi keamanan untuk menekan keberhasilan percobaan lanjutan.

## Tindakan Respons

### Detection

- Korelasi event pada Security Onion/SGUIL.
- Validasi log dan status jail Fail2Ban.

### Containment

- Pembatasan akses dengan UFW (deny/limit pada port terkait).
- Pemblokiran IP attacker oleh Fail2Ban.

### Eradication dan Recovery

- Penyesuaian konfigurasi SSH (termasuk kebijakan autentikasi) sesuai kebutuhan skenario.
- Restart service `ssh` setelah perubahan konfigurasi.
- Verifikasi ulang bahwa kontrol pertahanan tetap aktif.

## Evidence

- ![Percobaan Brute Force SSH pada Port 2222 dan Pemblokiran oleh Fail2Ban](<assets/01-Percobaan Brute Force SSH pada Port 2222 dan Pemblokiran oleh Fail2Ban.png>)
- ![Simulasi Serangan Berhasil dan Monitoring](<assets/02-Simulasi Serangan Berhasil dan Monitoring.png>)
- ![Simulasi Serangan Gagal dan Monitoring](<assets/03-Simulasi Serangan Gagal dan Monitoring.png>)

## Lessons Learned

1. Port non-default membantu mengurangi serangan otomatis pada port default, tetapi tidak menghilangkan risiko scanning.
2. Kombinasi UFW + Fail2Ban + monitoring SIEM lebih efektif dibanding satu kontrol tunggal.
3. Validasi konfigurasi autentikasi SSH perlu dilakukan setiap kali ada perubahan kebijakan.

## Kesimpulan

Phase 3 membuktikan bahwa lingkungan lab mampu mendeteksi, menahan, dan memulihkan insiden brute force SSH secara terukur. Hasil ini menjadi dasar rekomendasi hardening lanjutan untuk produksi.
