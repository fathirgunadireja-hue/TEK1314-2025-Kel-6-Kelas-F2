# TEK1314-2025-Kel-6-Kelas-F2
Mata Kuliah Keamanan Siber
## Deskripsi Proyek

Proyek ini mengimplementasikan skenario Remote Access Security Management Server dengan fokus pada serangan Brute Force & Dictionary Attack terhadap layanan SSH (Port 22).

### Skenario Attack
- Target Service: SSH (Secure Shell)
- Port: 22
- Attack Type: Brute Force & Dictionary Attack
- Tools: Hydra
- Karakteristik: Simulasi serangan otomatis yang menebak password SSH ribuan kali dalam satu menit, menghasilkan aktivitas yang sangat terlihat di log SIEM.

## Topologi Jaringan

Lab ini menggunakan arsitektur empat komponen utama dengan konfigurasi sebagai berikut:

### Network Configuration
- Network Segments:
  - Attacker LAN: 172.16.6.0/24
  - Target LAN: 192.168.6.0/24
- Network Type: Internal/Host-Only + NAT untuk monitoring VM
- Environment: Isolated Cybersecurity Lab

### System Components

| Hostname | IP Address(es) | OS | Role |
|-------------------------------|------------------------|--------|------------------------------|
| Ubuntu Cybersecurity Workstation | 172.16.6.10 | Ubuntu | Attacker Machine (172.16.6.0/24) |
| Router (Mikrotik) | 172.16.6.1 / 192.168.6.1 | Router | Gateway between two LANs |
| Ubuntu Server | 192.168.6.10 | Ubuntu Server | Target Server (192.168.6.0/24) |
| Security Onion | 172.16.6.30 / 192.168.6.30 | Security Onion | Monitoring / SIEM (dual-homed) |

#### 1. Attacker Machine
- VM Name: Ubuntu Cybersecurity Workstation
- IP Address: 172.16.6.10
- Tools: Hydra
- Target Port: 22 (SSH)
- Attack Type: Brute Force & Dictionary Attack
- Function: Melakukan serangan brute force terhadap target SSH via Router

#### 2. Router (Mikrotik)
- VM Name: Router Mikrotik
- IP Address: 172.16.6.1 dan 192.168.6.1 
- Function: Gateway sekaligus pemisah segmen jaringan

#### 3. Target Server
- VM Name: Ubuntu Server
- IP Address: 192.168.6.10
- Service: OpenSSH Server
- Port: 22

#### 4. Monitoring Server (Security Onion)
- VM Name: Security Onion
- IP Address: 172.16.6.30 dan 192.168.6.30
- Adapters: dual-homed atau bridge agar dapat memonitor lalu lintas antar-segmen
- Management Ports: 22 (SSH)
- Monitoring Mode: Passive Network Capture
- Function:
  - Network Traffic Analysis
  - Brute Force Detection
  - Alert Generation
  - Log Monitoring




