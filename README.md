# suricata-ids-lab
Laboratorio de Blue Team con Suricata IDS para monitoreo de tráfico, detección de escaneos y ataques, y creación de reglas personalizadas.

Arquitectura

- Kali Linux: máquina atacante
- Kali Linux: servidor IDS con Suricata 8.0.6
- Debian: servidor objetivo con Apache y SSH
- VirtualBox: entorno de virtualización

 Kali - Atacante
       |
       | TCP / SSH / HTTP
       v
Kali - IDS
Suricata 8.0.6
       |
       v
Debian - Servidor
Apache / SSH

Tecnologías utilizadas:

Suricata 8.0.6
Kali Linux
Debian
Apache
OpenSSH
Nmap
tcpdump
curl
VirtualBox

Detecciones realizadas:
Se realizó un escaneo TCP contra el servidor Debian utilizando Nmap.
Suricata detectó la actividad mediante reglas.

SSH Scan
Se realizaron múltiples conexiones contra el servicio SSH.

HTTP Monitoring
Se configuró Apache en Debian y se generó tráfico HTTP desde Kali.
Las peticiones fueron registradas por Suricata en eve.json.

Regla personalizada:
Se desarrolló una regla personalizada para detectar un patrón asociado a un posible intento de SQL Injection: alert tcp-pkt any any -> any 80 (msg:"CUSTOM Possible SQL Injection"; content:"OR%201=1"; nocase; sid:1000007; rev:1;).
La regla detecta el patrón: OR%201=1

