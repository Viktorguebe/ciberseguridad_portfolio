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
nmap -sP 10.0.2.0/24 -oN resultado_nmap.txt
