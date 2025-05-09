#### **Actividad Sospechosa y Escalada de Privilegios**

#### **Clasificación del riesgo**: **CRÍTICO**

### 1. Conexión Remota al Servidor MariaDB (entdmzdberp)

- **Dirección IP de origen**: `1.10.11.120` (China)
- **Hora**: 10:20:25
- **Puerto destino**: `3306` (MariaDB)
- **Resultado**: Conexión aceptada
- **Observación**: La conexión proviene de una región no autorizada. No hay evidencia clara de actividad posterior, lo que sugiere que pudo haberse tratado de una conexión de reconocimiento o exfiltración.

### 2. Conexión al Servidor de Correo Exchange (entmail)

- **IP de origen**: `1.10.11.120` (misma de arriba)
- **Puerto destino**: `25` (SMTP)
- **Resultado**: Conexión aceptada
- **Posible impacto**: Uso como relay SMTP para spam o intentos de phishing; reputación comprometida del servidor de correo.

**Recomendación común para ambos eventos:**  
Bloquear la IP `1.10.11.120` en todos los puntos de entrada.  
Restringir los puertos 25 y 3306 a IPs internas o vía VPN.  
Implementar **firewall de aplicación** o inspección DPI (Deep Packet Inspection).

### 3. Descarga de archivo tipo GIF desde Rusia

- **IP de origen**: `5.2.32.30` (Rusia)
- **Puerto destino**: `80`
- **Archivo**: `image/gif`, 11.2 MB
- **Resultado**: Transferencia exitosa
- **Riesgo**: Aunque el archivo es un GIF, puede contener código malicioso embebido (e.g. GIFAR o esteganografía).

**Recomendación:**  
Realizar análisis forense del archivo descargado.
Auditar acceso al servidor destino (`192.168.17.70`). 
Activar inspección de tráfico web y bloquear países no relacionados con operaciones.

### 4. Escalada de privilegios múltiples en dominio `kai`

- **Hora**: 14:18:16
- **IP atacante interna**: `192.168.16.187`
- **Usuario comprometido**: `kai6` (posiblemente usado como punto de entrada inicial)
- **Dominio afectado**: Todo el dominio `kai`
- **Privilegios asignados**: `SeDebugPrivilege`, `SeTakeOwnershipPrivilege`, `SeImpersonatePrivilege`, etc.

**Recomendaciones urgentes:** 
Cambiar contraseñas del dominio `kai`
Revocar privilegios asignados manualmente
Desconectar y aislar temporalmente el host con IP `192.168.16.187`
Verificar con herramientas como **KAPE, Velociraptor o Sysmon + Splunk** los movimientos laterales.  
Analizar si se utilizó **Mimikatz, Juicy Potato** u otra herramienta para la elevación.

## Conclusión general del día 4

Este día marca una **etapa avanzada del ataque**. El atacante ya no solo realiza conexiones externas, sino que se encuentra **dentro de la red interna** y está escalando privilegios, probablemente como preparación para un **ataque de mayor impacto (ransomware, exfiltración, sabotaje)**. Es indispensable asumir que **el dominio `kai` ha sido comprometido por completo**.