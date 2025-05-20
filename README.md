# 🛡️ Portafolio de Ciberseguridad - ViktorCyber

Bienvenido a mi portafolio práctico de hacking ético y ciberseguridad ofensiva.  
Aquí encontrarás una recopilación de ejercicios, prácticas reales, documentación y pruebas realizadas en Kali Linux, acompañadas de explicaciones paso a paso.

---

📚 **Índice**

1. Configuración de entorno  
2. Escaneos de red con Nmap  
   2.1 Escaneo básico (Ping scan)  
   2.2 Escaneo agresivo  
   2.3 Escaneo con detección de versiones y sistema operativo  
3. Próximos pasos y temas a estudiar

---

## 🧰 Configuración de entorno

- **SO:** Kali Linux
- **Interfaz de red:** `eth0`
- **IP Local:** `10.0.2.15/24`
- **Herramientas instaladas:** Git, Nmap, etc.
- **Modo de red:** NAT (por ahora)

---

🔎 Escaneos de red con Nmap
1. Escaneo básico (Ping scan)
Objetivo: Identificar hosts activos en la red local.

Comando:

bash
Copiar
Editar
nmap -sP 10.0.2.0/24 -oN resultado_nmap.txt
Resultado:
Se identificaron hosts activos, por ejemplo:

10.0.2.2 (MAC: 52:55:0A:00:02:02)

10.0.2.3 (MAC: 52:55:0A:00:02:03)

2. Escaneo agresivo
Objetivo: Detectar puertos abiertos, servicios, versiones y scripts básicos.

Comando:

bash
Copiar
Editar
nmap -A -T4 10.0.2.2 -oN escaneo_agresivo.txt
Resultado destacado:

Puertos abiertos: 135, 445, 2869

Servicios: Microsoft Windows RPC, SMB, HTTPAPI httpd 2.0

Sistema operativo estimado: Entorno virtualizado (QEMU, VirtualBox, etc.)

3. Escaneo con detección de versiones y sistema operativo
Objetivo: Identificar versiones exactas de servicios y detectar sistema operativo con más detalle.

Comando:

bash
Copiar
Editar
nmap -sV -O 10.0.2.2 -oN nmap_servicios_y_os.txt
Resultado destacado:

Servicios detectados y versiones (ejemplo): RPC, SMB, HTTPAPI

Sistema operativo: Entorno virtualizado

Nota: Precisión limitada por condiciones del entorno.

⏭️ Próximos pasos y temas a estudiar
Realizar banner grabbing con Netcat

Enumeración de servicios específicos (SMB, FTP, HTTP)

Escaneo con herramientas adicionales (Nikto, Dirb)

Comenzar pruebas de explotación en entorno controlado
