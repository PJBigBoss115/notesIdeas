## **Preparación para el ejercicio práctico con Security Onion**

### **Herramienta principal: Security Onion**

- **Security Onion** será el entorno principal para las prácticas.
- Es una plataforma de código abierto para **detección de intrusos**, **monitoreo de seguridad** y **análisis forense de red**.
- Incluye una serie de herramientas ya integradas como:
    - **Suricata** (detección de intrusos – IDS)
    - **Zeek** (análisis de tráfico)
    - **Wazuh** (detección de amenazas en endpoints)
    - **TheHive**, **Cortex**, **CyberChef**, entre otras.

### **Arquitectura general**

- Basado en **Linux** como sistema operativo.
- Sobre Linux están montadas todas las herramientas necesarias.
- Existen versiones optimizadas para distintos entornos y capacidades, incluso imágenes listas para virtualizar o desplegar en la nube.

### **Kibana y Elastic Stack**

- **Elastic Stack** se utiliza para **almacenar, analizar y visualizar datos** (logs, alertas, registros de red).
- **Kibana** es la interfaz gráfica principal:
    - Permite crear dashboards, filtros, visualizaciones de ataques.
    - Útil para realizar análisis rápidos o búsquedas específicas.
- Se recomienda enviar los logs a un **servidor externo** (no local) para conservar integridad en caso de compromisos.

### **Ecosistema de herramientas en Security Onion**

- Todas las herramientas incluidas están bien documentadas.
- Cada componente (Zeek, Suricata, Wazuh, etc.) tiene una **función específica**, pero están **interconectadas para brindar visibilidad total** de la red.
- El sistema permite monitorear múltiples protocolos y capturar tráfico en tiempo real.

### **Caza de amenazas en Security Onion**

- El módulo de **"Hunt" (caza de amenazas)** es una de las secciones más importantes.
- Ofrece múltiples formas de búsqueda de actividad sospechosa:
    - Por IP
    - Por puertos
    - Por alertas generadas por Suricata
    - Por logs de eventos de Zeek
- También se puede usar para detectar **movimientos laterales, beaconing, o patrones fuera de lo normal.**

## Instalación de Security Onion (resumen solicitado)

Para instalar Security Onion:
1. Descargar la ISO desde [https://securityonion.net](https://securityonion.net).
2. Montar en una máquina virtual (recomendada VirtualBox, VMware, o Proxmox).
3. Al arrancar, elegir "Install Security Onion".
4. Seguir los pasos del asistente gráfico (configurar red, nombre del host, clave de admin).
5. Después de la instalación, se puede configurar el modo:
    - **Standalone** (todo en un solo nodo, ideal para laboratorio)
    - **Distributed** (en varios nodos para entornos reales).

> ⚠️ Requisitos mínimos: 2 CPU, 8 GB de RAM, 200 GB de disco (para pruebas básicas).

### **Datos a entregar en el ejercicio**

En el análisis de tráfico debes reportar lo siguiente:

|Elemento|Descripción|
|---|---|
|**IP de origen**|Dirección IP desde donde se generó la comunicación o posible ataque|
|**Puesto de origen**|Host o nombre del equipo que originó la actividad|
|**IP de destino**|IP hacia donde iba dirigida la comunicación|
|**Hora**|Fecha y hora exacta del evento o alerta detectada|
|**Protocolo**|TCP, UDP, ICMP, HTTP, etc. (depende del tipo de conexión o amenaza)|
|**Alerta**|Descripción de la alerta generada (por ejemplo: "ET TROJAN Possible")|
|**Resumen**|Breve explicación de lo que pasó (en tus propias palabras, análisis)|

### Tips para el ejercicio final:

- Usá **filtros en Kibana** para reducir la cantidad de resultados.
- **Correlacioná eventos entre Zeek y Suricata** para tener un mejor panorama.
- Si ves comportamiento inusual (como puertos raros o tráfico constante a un solo destino), documentalo.
- Guarda capturas de pantalla o evidencia si es necesario armar un reporte.