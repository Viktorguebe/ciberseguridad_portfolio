# 🛡️ Portafolio de Ciberseguridad - ViktorCyber

Bienvenido a mi portafolio práctico de hacking ético y ciberseguridad ofensiva.  
Aquí encontrarás una recopilación de ejercicios, prácticas reales, documentación y pruebas realizadas en Kali Linux, acompañadas de explicaciones paso a paso.

---

## 📚 Índice

1. [Reconocimiento con Nmap](#reconocimiento-con-nmap)
2. [Configuración de entorno](#configuración-de-entorno)
3. [Próximos temas](#próximos-temas)

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

```bash
nmap -sP 10.0.2.0/24

### Resultado:
Se identificaron varios hosts activos en la red. Se detallan a continuación:
Host: 10.0.2.2 -> MAC: 52:55:0A:00:02:02
Host: 10.0.2.3 -> MAC: 52:55:0A:00:02:03

### Escaneo de puertos:
nmap 10.0.2.2

### Resultado:
Not shown: 1000 closed tcp ports

✅ Explicación rápida:
Esto significa que el host está activo, pero no tiene puertos abiertos visibles o bien un firewall los bloquea.
💡 Este tipo de comportamiento es común en redes NAT o entornos protegidos.

### Archivo de resultados:
Los resultados fueron guardados en un archivo de texto con el siguiente comando:
nmap -sP 10.0.2.0/24 -oN resultado_nmap.txt


## ⏭️ Próximos pasos:
- Prueba con escaneo más agresivo (nmap -A, -sV, -O)
- Banner grabbing con Netcat
- Enumeración de servicios
- Análisis de resultados
