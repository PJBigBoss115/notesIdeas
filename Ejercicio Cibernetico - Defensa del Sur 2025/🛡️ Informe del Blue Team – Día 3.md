**Fecha:** 04 de mayo de 2025  
**Responsable del análisis:** Pedro José Aguilar Vaides  
**Correo:** soc.analyst6@kai.south  
**Segmento protegido:** Boundary FW – Subred 172.16.99.0/26  
**Severidad:** Alta

### **1. Hallazgos Generales**

#### **Direcciones IPv4 externas detectadas:**

|Dirección IP|Ubicación geográfica|Observaciones|
|---|---|---|
|192.168.15.124|Guatemala|Posible origen local|
|1.10.11.120|Wenquan|Tráfico sospechoso|
|104.87.160.10|Kanagawa / USA (VirusTotal)|Sospechoso según reputación externa|
|34.117.228.201|Misuri, USA|Recurrente|
|69.173.146.10|Virginia, USA||
|64.233.176.94|California, USA||
|74.125.21.132|California, USA||
|216.238.147.201|Florida, USA||
|130.41.169.30|México|Tráfico frecuente en intentos HTTP|

#### **Direcciones IP internas (Red corporativa):**

- Segmento 192.168.17.0/24:  
    `192.168.17.11`, `192.168.17.10`, `192.168.17.42`, `192.168.17.41`, `192.168.17.100`
- Segmento 192.168.15.0/24:  
    `192.168.15.124`, `192.168.15.196`, `192.168.15.119`, `192.168.15.81`, `192.168.15.57`
- Segmento 192.168.16.0/24:  
    `192.168.16.195`

#### **Servicios detectados en puertos abiertos:**

|Servicio|Frecuencia detectada|
|---|---|
|`SSH-2.0-OpenSSH_for_Windows_8.6`|2,198 veces|
|`SSH-2.0-OpenSSH_8.9p1 Ubuntu-3ubuntu0.4`|Varias veces|
|`SSH-2.0-OpenSSH_for_Windows_9.5`||
|`SSH-2.0-OpenSSH_8.2p1 Ubuntu-4ubuntu0.9`||

#### **Posibles Indicadores de Spoofing o falsificación de User-Agent:**

- `Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 Chrome/136.0.0.0`
- `Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 Chrome/135.0.0.0`  
    _(Versiones no válidas o inexistentes de Chrome, posible uso por botnets.)_

### **2. Reporte de Incidente - Múltiples Intentos de Escaneo**

**Sistema afectado:** Firewall perimetral (Boundary FW)  
**Dirección atacante:** `130.41.169.22` (México)  
**Servicio atacado:** Puerto 80 (HTTP)  
**PID/TID registrados:** `40818#100501` – Solicitud ID: `*5896`  
**Cliente:** `172.16.99.2` (IP privada interna)

#### **Resumen:**

Se registraron múltiples intentos automáticos de escanear el servicio web. Esto podría tratarse de un bot o script buscando rutas de administración no protegidas.

#### **Recomendaciones:**

1. **Bloquear IP de origen:**

```
sudo iptables -I INPUT -s 172.16.99.2 -j DROP
```
    
2. **Cambiar contraseña de `admin`**
3. **Restringir acceso web al firewall**
4. **Revisar logs de `/var/log/httpd/access.log`, `/var/log/syslog`**
5. **Actualizar el firmware del firewall o router**
6. **Implementar HTTPS obligatorio, cambio de puerto web, y monitoreo constante.**

### **3. Reporte de Incidente - Ingreso Exitoso Sospechoso**

**Sistema afectado:** Boundary FW + Gateway  
**Dirección atacante:** `172.16.99.2`  
**Servicio atacado:** Puertos 80/443  
**Resultado:** Acceso exitoso confirmado a interfaz administrativa

#### **Indicador de compromiso activo:**

- Navegación por archivos del sistema y acceso a estadísticas de red
- Coincide con IP que previamente realizó fuerza bruta vía SSH

#### **Acciones urgentes recomendadas:**

1. Bloquear IP `172.16.99.2` inmediatamente
2. Cambiar contraseñas y revisar usuarios
3. Analizar integridad del sistema y revertir cambios sospechosos
4. Limitar acceso a la administración solo por segmentos internos autorizados

### **Conclusión General del Día 3**

Durante la jornada se identificaron múltiples accesos sospechosos tanto internos como externos, con varios intentos automatizados y un compromiso confirmado. Las medidas defensivas activas (como el firewall) han bloqueado parte de los ataques, pero se requiere:

- Refuerzo de controles de acceso
- Monitoreo continuo de logs
- Hardening del firewall y routers
- Aplicación de parches y actualizaciones
- Validación de integridad en puntos críticos