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

Lab ini menggunakan arsitektur tiga sistem dengan konfigurasi sebagai berikut:

### Network Configuration
- Network Type: Host-Only Adapter
- Subnet: 192.168.26.0/24
- Subnet Mask: 255.255.255.0
- Environment: Isolated Cybersecurity Lab

### System Components

| Hostname | IP Address | OS | Role |
|----------|------------|-----|------|
| Ubuntu Cybersecurity Workstation | 192.168.26.10 | Ubuntu | Attacker Machine |
| Ubuntu Server | 192.168.26.20 | Ubuntu Server | Target Server |
| Security Onion | 192.168.26.30 | Security Onion | Monitoring/SIEM |

#### 1. Attacker Machine
- VM Name: Ubuntu Cybersecurity Workstation
- IP Address: 192.168.26.10
- Tools: Hydra
- Target Port: 22 (SSH)
- Attack Type: Brute Force & Dictionary Attack
- Function: Melakukan serangan brute force terhadap target SSH

#### 2. Target Server
- VM Name: Ubuntu Server
- IP Address: 192.168.26.20
- Service: OpenSSH Server
- Port: 22
- Function: Server target yang akan diserang

#### 3. Monitoring Server (SIEM)
- VM Name: Security Onion
- IP Address: 192.168.26.30
- Management Ports: 22 (SSH), 443 (HTTPS Web Interface)
- Monitoring Mode: Passive Network Capture
- Function: 
  - Network Traffic Analysis
  - Brute Force Detection
  - Alert Generation
  - Log Monitoring

## Struktur Repository

```
TEK1314-2025-Kel-6-Kelas-F2/
â”œâ”€â”€ docs/
â”‚   â”œâ”€â”€ phase-1-baseline/          # Fase 1: Hardening & Baseline
â”‚   â”‚   â”œâ”€â”€ baseline-report.md     # Laporan utama Phase 1
â”‚   â”‚   â”œâ”€â”€ assets/                # Screenshot & bukti visual
â”‚   â”‚   â””â”€â”€ README.md
â”‚   â”œâ”€â”€ phase-2-va/                # Fase 2: Vulnerability Assessment
â”‚   â””â”€â”€ phase-3-incident/          # Fase 3: Incident Response
â”œâ”€â”€ scripts/                       # Scripts untuk automation
â”œâ”€â”€ documentation/                 # Dokumentasi legacy (design, etc)
â”œâ”€â”€ Evidence-Logs/                 # Log dan bukti (legacy)
â”œâ”€â”€ Reports/                       # Reports (legacy)
â”œâ”€â”€ LOGBOOK.md                     # Logbook aktivitas mingguan
â””â”€â”€ README.md                      # File ini
```

