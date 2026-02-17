# TEK1314-2025-Kel-6-Kelas-F2
Mata Kuliah Keamanan Siber
## Deskripsi Proyek

Proyek ini mengimplementasikan skenario **Remote Access Security Management Server** dengan fokus pada serangan Brute Force & Dictionary Attack terhadap layanan SSH (Port 22).

### Skenario Attack
- **Target Service**: SSH (Secure Shell)
- **Port**: 22
- **Attack Type**: Brute Force & Dictionary Attack
- **Tools**: Hydra
- **Karakteristik**: Simulasi serangan otomatis yang menebak password SSH ribuan kali dalam satu menit, menghasilkan aktivitas yang sangat terlihat di log SIEM.

## Topologi Jaringan

Lab ini menggunakan arsitektur tiga sistem dengan konfigurasi sebagai berikut:

### Network Configuration
- **Network Type**: Host-Only Adapter
- **Subnet**: 192.168.26.0/24
- **Subnet Mask**: 255.255.255.0
- **Environment**: Isolated Cybersecurity Lab

### System Components

| Hostname | IP Address | OS | Role |
|----------|------------|-----|------|
| Ubuntu Cybersecurity Workstation | 192.168.26.xx | Ubuntu | Attacker Machine |
| Ubuntu Server | 192.168.26.xx | Ubuntu Server | Target Server |
| Security Onion | 192.168.26.xx | Security Onion | Monitoring/SIEM |

#### 1. Attacker Machine
- **VM Name**: Ubuntu Cybersecurity Workstation
- **IP Address**: 192.168.26.xx
- **Tools**: Hydra
- **Function**: Melakukan serangan brute force terhadap target SSH

#### 2. Target Server
- **VM Name**: Ubuntu Server
- **IP Address**: 192.168.26.xx
- **Service**: OpenSSH Server
- **Port**: 22
- **Function**: Server target yang akan diserang

#### 3. Monitoring Server (SIEM)
- **VM Name**: Security Onion
- **IP Address**: 192.168.26.xx
- **Function**: 
  - Network Traffic Analysis
  - Brute Force Detection
  - Alert Generation
  - Log Monitoring

## Dokumentasi

- [IP Address Planning](docs/design/ip_plan.md)