# 🛡️ Portafolio de Ciberseguridad - ViktorCyber

Bienvenido a mi portafolio práctico de hacking ético y ciberseguridad ofensiva.  
Aquí encontrarás una recopilación de ejercicios, prácticas reales, documentación y pruebas realizadas en Kali Linux, acompañadas de explicaciones paso a paso.

---

📚 Índice
1. Configuración de entorno

2. Reconocimiento con Nmap

3. Escaneo agresivo con Nmap

4. Próximos pasos

---

## 🧰 Configuración de entorno

- **SO:** Kali Linux
- **Interfaz de red:** `eth0`
- **IP Local:** `10.0.2.15/24`
- **Herramientas instaladas:** Git, Nmap, etc.
- **Modo de red:** NAT (por ahora)

---

## 🔎 Reconocimiento con Nmap

### Objetivo:

Identificar hosts activos en la red local y descubrir puertos abiertos en ellos.

### Comando ejecutado:

nmap -sP 10.0.2.0/24


### Resultado:
Se identificaron varios hosts activos en la red. Se detallan a continuación:
| Host     | MAC Address       |
| -------- | ----------------- |
| 10.0.2.2 | 52:55:0A:00:02:02 |
| 10.0.2.3 | 52:55:0A:00:02:03 |


### Escaneo de puertos(host 10.0.2.2):
nmap 10.0.2.2


Resultado:
Not shown: 1000 closed tcp ports

✅ Explicación rápida:
El host está activo, pero no muestra puertos abiertos o puede tener un firewall que los bloquea. Esto es común en redes NAT o entornos protegidos.

Archivo de resultados
Los resultados fueron guardados con el siguiente comando:

nmap -sP 10.0.2.0/24 -oN resultado_nmap.txt

---

### 🔎 Escaneo agresivo con Nmap

### Comando utilizado:
nmap -A -T4 10.0.2.2 -oN escaneo_agresivo.txt


### Resultados destacados:
| Puerto   | Servicio                           |
| -------- | ---------------------------------- |
| 135/tcp  | Microsoft Windows RPC              |
| 445/tcp  | microsoft-ds (SMB)                 |
| 2869/tcp | Microsoft HTTPAPI httpd 2.0 (UPnP) |

### Sistema operativo detectado:

- Entorno virtualizado (QEMU, VirtualBox, Slirp)

- No se pudo determinar un OS exacto por falta de puertos cerrados

### Información adicional:

- SMB con firma opcional (puede ser una debilidad)

- Hora del sistema remoto detectada

- Red: Distancia 1 salto (misma red)

### Red: Distancia 1 salto (misma red)

### Archivo generado:
escaneo_agresivo.txt

## ⏭️ Próximos pasos:
- Prueba con escaneo más agresivo (nmap -A, -sV, -O)
- Banner grabbing con Netcat
- Enumeración de servicios
- Análisis de resultados
