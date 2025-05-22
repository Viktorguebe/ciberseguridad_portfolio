# 🛡️ Portafolio de Ciberseguridad - ViktorCyber

Bienvenido a mi portafolio práctico de hacking ético y ciberseguridad ofensiva.  
Aquí encontrarás una recopilación de ejercicios, prácticas reales, documentación y pruebas realizadas en Kali Linux, acompañadas de explicaciones paso a paso.

---

📚 **Índice**

1. [Configuración de entorno](docs/configuracion.md)  
2. [Escaneos de red con Nmap](docs/escaneos.md)    
   2.1 Escaneo básico (Ping scan)  
   2.2 Escaneo agresivo  
   2.3 Escaneo con detección de versiones y sistema operativo
3. Banner Grabbing
4. [Próximos pasos y temas a estudiar](docs/proximos_pasos.md)

---

## 🧰 Configuración de entorno

- **SO:** Kali Linux
- **Interfaz de red:** `eth0`
- **IP Local:** `10.0.2.15/24`
- **Herramientas instaladas:** Git, Nmap, etc.
- **Modo de red:** NAT (por ahora)

---

## 🔎 Escaneos de red con Nmap

### 1. Escaneo básico (Ping scan)

**Objetivo:** Identificar hosts activos en la red local.

**Comando:**
nmap -sP 10.0.2.0/24 -oN resultado_nmap.txt

**Resultados:**
Hosts activos detectados:

10.0.2.2 → MAC: 52:55:0A:00:02:02

10.0.2.3 → MAC: 52:55:0A:00:02:03

**Escaneo de puertos:**
nmap 10.0.2.2

**Resultados:**
Not shown: 1000 closed tcp ports


✅ Interpretación:
El host está activo pero no tiene puertos abiertos visibles, o un firewall los está bloqueando. Esto es común en redes NAT o entornos protegidos.

**Archivo de Resultados:**
Los resultados completos están guardados y disponibles en el archivo resultado_nmap.txt.


### 2. Escaneo agresivo

**Objetivo:** Detectar puertos abiertos, servicios, versiones y scripts básicos.

**Comando:**
nmap -A -T4 10.0.2.2 -oN archivo_agresivo.txt

**Resultados destacados:**
- Puertos abiertos: 135, 445, 2869
- Servicios: Microsoft Windows RPC, SMB, HTTPAPI httpd 2.0
- Sistema operativo estimado: Entorno virtualizado (QEMU, VirtualBox, etc.)


✅ Interpretación:
El escaneo agresivo identificó puertos abiertos importantes (135, 445, 2869) con servicios Microsoft RPC, SMB y HTTPAPI corriendo en un entorno virtualizado (VirtualBox/QEMU). Esto indica que la máquina está activa y ofrece servicios que pueden ser evaluados para posibles vulnerabilidades. Además, la configuración del protocolo SMB muestra que la firma está habilitada pero no obligatoria, lo que puede representar un riesgo de seguridad.

**Archivo de Resultados:**
Los resultados completos están guardados y disponibles en el archivo archivo_agresivo.txt.


### 3. Escaneo con detección de versiones y sistema operativo

**Objetivo:** Identificar versiones exactas de servicios y detectar sistema operativo con más detalle.

**Comando:**
nmap -sV -O 10.0.2.2 -oN nmap_servicios_y_os.txt

**Resultados destacados:**
- Servicios detectados y versiones (ejemplo): RPC, SMB, HTTPAPI
- Sistema operativo: Entorno virtualizado
- Nota: Precisión limitada por condiciones del entorno.


✅ Interpretación:
Se detectaron versiones específicas de servicios clave como RPC, SMB y HTTPAPI. El sistema operativo se identificó como un entorno virtualizado, aunque con precisión limitada por las condiciones de la red y la configuración del host. Esta información es esencial para planificar ataques más específicos y elegir herramientas adecuadas para la siguiente fase de pruebas.

**Archivo de Resultados:**
Los datos completos están disponibles en nmap_servicios_y_os.txt.

---

### 🛠️ Banner Grabbing

**Objetivo:** Obtener información detallada de los servicios a través de los banners que muestran al establecer conexiones TCP.

**Comando:**
nc -v 10.0.2.2 80

**Resultados destacados:**
HEAD / HTTP/1.0
200 OK
Content-Length: 1012
Content-Type: text/html
Last-Modified: Wed, 23 Apr 2025 10:18:43 GMT
...
403 Forbidden

✅ Interpretación:
El servidor responde con un código 403 Forbidden, indicando que la conexión fue exitosa pero el acceso al recurso está restringido. Este banner puede revelar información útil sobre el servidor web y sus configuraciones de seguridad.

**Archivo de Resultados:**
Los datos completos están disponibles en banner_grabbing.txt.
