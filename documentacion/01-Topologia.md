# 🌐 Topología del laboratorio

## Objetivo

Diseñar la infraestructura del laboratorio SOC antes de iniciar la implementación, definiendo las máquinas virtuales, la red y la comunicación entre los equipos.

---

# Arquitectura

| Máquina | Función |
|----------|---------|
| FortiGate | Firewall |
| Ubuntu Server | Wazuh SIEM/XDR |
| Windows Server 2022 | Active Directory y DNS |
| Windows 10 | Endpoint monitoreado |
| Kali Linux | Simulación de ataques |

---

# Especificaciones de las máquinas

| Máquina | CPU | RAM | Disco |
|----------|-----|-----|-------|
| FortiGate | 2 | 2 GB | 10 GB |
| Ubuntu Server | 4 | 8 GB | 80 GB |
| Windows Server 2022 | 2 | 4 GB | 60 GB |
| Windows 10 | 2 | 4 GB | 50 GB |
| Kali Linux | 2 | 4 GB | 40 GB |

---

# Topología

# 🌐 Topología

La infraestructura del laboratorio estará compuesta por un firewall FortiGate que actuará como puerta de enlace entre Internet y la red interna del laboratorio.

Todas las máquinas virtuales estarán conectadas a una red LAN interna protegida por FortiGate. Esto permitirá monitorear el tráfico, aplicar políticas de seguridad y centralizar los eventos mediante Wazuh.

```text
                     Internet
                         │
                  Adaptador NAT
                         │
                    FortiGate
                         │
                  Red Interna SOC
                         │
      ┌──────────┬──────────┬──────────┬──────────┐
      │          │          │          │
 Ubuntu       Windows    Windows      Kali
 Wazuh        Server      10          Linux
```

## Descripción

- **FortiGate** será el firewall del laboratorio y la puerta de enlace hacia Internet.
- **Ubuntu Server** alojará Wazuh Manager para el monitoreo y análisis de eventos.
- **Windows Server 2022** funcionará como controlador de dominio y servidor DNS.
- **Windows 10** será el equipo cliente monitoreado mediante el agente de Wazuh y Sysmon.
- **Kali Linux** se utilizará para realizar pruebas de seguridad controladas y generar eventos para su análisis.

---

# Red

LAN SOC

192.168.100.0/24

Gateway

192.168.100.1

---

# Direccionamiento IP

| Equipo | IP |
|---------|----|
| FortiGate | 192.168.100.1 |
| Wazuh | 192.168.100.10 |
| Windows Server | 192.168.100.20 |
| Windows 10 | 192.168.100.30 |
| Kali Linux | 192.168.100.40 |

---

# Adaptadores VMware

FortiGate

NIC 1 → NAT

NIC 2 → LAN Interna

Ubuntu

NIC 1 → LAN Interna

Windows Server

NIC 1 → LAN Interna

Windows 10

NIC 1 → LAN Interna

Kali Linux

NIC 1 → LAN Interna

---

# Objetivo de la siguiente fase

Crear las máquinas virtuales y configurar la red antes de instalar cualquier herramienta.
