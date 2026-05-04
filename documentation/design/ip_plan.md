# IP Plan & Adapter Mapping

Networks:
- Attacker LAN: 172.16.6.0/24
- Target LAN: 192.168.6.0/24

Hosts & IPs:
- Attacker (Ubuntu Workstation)
  - Adapter (internal at): 172.16.6.10/24
- Router (Mikrotik)
  - Adapter 1 (internal at): 172.16.6.1/24
  - Adapter 2 (internal on): 192.168.6.1/24
- Target Server (Ubuntu Server)
  - Adapter (internal ta): 192.168.6.10/24
- Monitoring Server (Security Onion)
  - Adapter 1 (internal on): 172.16.6.30/24
  - Adapter 2 (internal ta): 192.168.6.30/24
  - Adapter 3 (monitoring): NAT (for internet access / updates)
  - Bridge: br0 connects adapter1 + adapter2 for packet monitoring



