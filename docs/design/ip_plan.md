# IP Address Planning

## Network Configuration

- **Network Type**: Host-Only Adapter
- **Subnet**: 192.168.26.0/24
- **Subnet Mask**: 255.255.255.0
- **Environment**: Isolated Cybersecurity Lab

## IP Address Table

| Hostname | IP Address | OS |
|----------|------------|-----|
| Ubuntu Cybersecurity Workstation (Attacker) | 192.168.26.xx | Ubuntu |
| Ubuntu Server (Target) | 192.168.26.xx | Ubuntu Server |
| Security Onion (Monitoring/SIEM) | 192.168.26.xx | Security Onion |

## System Details

### Attacker Machine
- **VM Name**: Ubuntu Cybersecurity Workstation
- **IP Address**: 192.168.26.xx
- **Tools**: Hydra
- **Target Port**: 22 (SSH)
- **Attack Type**: Brute Force & Dictionary Attack

### Target Server
- **VM Name**: Ubuntu Server
- **IP Address**: 192.168.26.xx
- **Service**: OpenSSH Server
- **Port**: 22

### Monitoring Server (SIEM)
- **VM Name**: Security Onion
- **IP Address**: 192.168.26.xx
- **Function**: 
  - Network Traffic Analysis
  - Brute Force Detection
  - Alert Generation
