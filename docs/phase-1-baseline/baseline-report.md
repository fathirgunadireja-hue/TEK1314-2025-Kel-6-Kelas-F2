# Baseline Report - Phase 1 (Hardening & Baseline)

## Informasi Umum

- Proyek: TEK1314-2025-Kel-6-Kelas-F2
- Mata Kuliah: Keamanan Siber
- Skenario: Remote Access Security Management Server
- Periode Pelaksanaan: Minggu 4-7 (10-19 Maret 2026)
- Status: Selesai

## Tujuan Phase 1

Phase 1 bertujuan membangun baseline lingkungan lab yang stabil dan aman sebelum fase serangan serta analisis insiden dilakukan. Fokus kegiatan meliputi:

1. Menetapkan konfigurasi IP antar VM.
2. Melakukan hardening dasar pada server target.
3. Memastikan firewall dan layanan SSH berjalan sesuai kebutuhan skenario.
4. Memvalidasi konektivitas antar host.
5. Memastikan aktivitas sistem dan jaringan terekam di Security Onion.

## Arsitektur Baseline

### Konfigurasi Jaringan

- Network Type: Host-Only Adapter
- Subnet: 192.168.26.0/24
- Subnet Mask: 255.255.255.0
- Environment: Isolated Cybersecurity Lab

### Tabel Host dan Peran

| Hostname | IP Address | OS | Role |
|----------|------------|----|------|
| Ubuntu Cybersecurity Workstation | 192.168.26.10 | Ubuntu | Attacker Machine |
| Ubuntu Server | 192.168.26.20 | Ubuntu Server | Target Server |
| Security Onion | 192.168.26.30 | Security Onion | Monitoring/SIEM |

## Aktivitas Implementasi

### 1) Setup Topologi dan Security Onion

- Menyiapkan 3 VM sesuai rancangan topologi.
- Melakukan instalasi dan aktivasi Security Onion sebagai monitoring server.
- Memastikan mode monitoring mendukung kebutuhan capture traffic lab.

Evidence:
- ![Topologi Lab](assets/01-topology.png)
- ![Instalasi Security Onion](<assets/02- instalasi security onion.png>)

### 2) System Hardening (Target Server)

- Menerapkan hardening awal pada Ubuntu Server.
- Melakukan konfigurasi firewall untuk membatasi akses hanya pada layanan yang diperlukan.
- Menjaga layanan SSH (port 22) tetap aktif untuk kebutuhan skenario brute force pada fase berikutnya.

Evidence:
- ![Hardening](<assets/03- Hardening.png>)
- ![System Hardening](<assets/07-System Hardening.png>)

### 3) Konfigurasi IP Setiap Host

- Menetapkan alamat IP statis pada setiap VM sesuai IP plan.
- Menyesuaikan konfigurasi attacker, target server, dan Security Onion pada subnet yang sama.

Evidence:
- ![IP Attacker](<assets/04-Konfigurasi IP Attacker.png>)
- ![IP Security Onion](<assets/05-Konfigurasi IP Onion.png>)
- ![IP Target Server](<assets/06-Konfigurasi IP Target Server.png>)

### 4) Validasi Konektivitas dan Logging

- Melakukan pengujian ping antar VM untuk memastikan komunikasi jaringan berjalan baik.
- Melakukan logging verification di Security Onion untuk memastikan aktivitas terekam.

Evidence:
- ![Ping Antar VM](<assets/09-Ping antar VM.png>)
- ![Logging Verification](<assets/08-Logging Verification.png>)

## Hasil Baseline

1. Seluruh host aktif pada subnet 192.168.26.0/24 dan dapat saling terhubung.
2. Target server telah melalui hardening dasar dan konfigurasi firewall.
3. Layanan SSH target berjalan untuk kebutuhan skenario pengujian fase berikutnya.
4. Security Onion berhasil menerima log/aktivitas dari lingkungan lab.

## Kesimpulan

Phase 1 telah menghasilkan baseline jaringan dan keamanan yang siap digunakan untuk:

1. Phase 2 (Vulnerability Assessment) untuk identifikasi celah.
2. Phase 3 (Incident Response) untuk simulasi dan analisis insiden brute force SSH.

Dengan baseline ini, aktivitas di fase lanjutan dapat dilakukan secara terukur, terdokumentasi, dan dapat divalidasi melalui data monitoring.


