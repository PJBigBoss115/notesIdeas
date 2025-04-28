# Recapitulación del Día de Hoy: Inteligencia Sobre Ciberamenazas (CTI)

### Contexto inicial

- **Guardia Costera y Ciberseguridad Marítima:**  
    Se discutió el papel de la Guardia Costera de EE.UU. en el dominio cibernético, especialmente en la **protección de cables submarinos**.  
    **¿Por qué el mar?**  
    Porque muchos sistemas críticos de telecomunicaciones y datos usan **cables submarinos**; estos deben protegerse físicamente y cibernéticamente.  
    Trabajan con **alianzas** y **planificación** para asegurar rutas y sistemas.

[Saber mas acerca de Guardia Costera de los Estados Unidos](https://www.uscg.mil/MaritimeCyber/)

# Conceptos Clave

## ¿Qué es la Inteligencia sobre Ciberamenazas (CTI)?

- **Definición:** 
    Es el análisis de datos crudos para obtener **inteligencia útil** sobre amenazas existentes o potenciales. 
- **Importancia:**  
    Sirve para identificar, entender y prevenir **riesgos** y **ataques**.  
    Se trata de detectar qué activos son deseados por terceros y cómo podrían ser comprometidos.

# Información vs Inteligencia

| Información                 | Inteligencia                                                                |
| --------------------------- | --------------------------------------------------------------------------- |
| Datos crudos (sin analizar) | Interpretación y análisis de los datos para obtener conocimiento accionable |
# Elementos importantes en CTI

### Recolección de datos

Fuentes comunes de información para generar inteligencia:
- **Registros de sistemas** (logs)
- **Tráfico de red**
- **Puntos finales** (endpoints como computadoras, móviles)
- **Análisis de malware**
- **Correos fraudulentos** (phishing)
- **Incidentes pasados**
- **Comunidades ISAC** (grupos de intercambio sectorial de amenazas)
- **Gobierno:** US-CERT, FBI
- **Alianzas organizacionales**
- **Proveedores de seguridad**
- **Código abierto (OSINT)**

# Herramientas de defensa

- **Firewall:** Controla tráfico de red entrante/saliente según reglas de seguridad.
- **IDS (Intrusion Detection System):** Detecta actividad sospechosa o anómala.
- **Firmas electrónicas (Hashes):**  
    Cada archivo/software tiene un "hash" único para detectar alteraciones o infecciones.

# Evaluación de amenazas

**Puntos a analizar:**
- ¿Qué activos tenemos? (servidores, firewalls, bases de datos, etc.)
- ¿Qué usuarios o sistemas consumen esos activos? (operativos, estratégicos, tácticos)
- ¿Qué consecuencias tendría perderlos?

Se debe tener un **catálogo de activos** con información como:
- Ubicación
- Función
- Tiempo de recuperación en caso de pérdida

# Modelos de Ciberamenazas

### Modelo del Diamante

![[Diamond.png]]

4 componentes:

- **Adversario**: El atacante
- **Víctima**: El objetivo
- **Infraestructura**: Los medios usados (servidores, correos, redes)
- **Capacidad**: Herramientas y métodos de ataque

*El adversario utiliza capacidades a través de una infraestructura para atacar a una víctima.*

### Cyber Kill Chain (Cadena de Muerte Cibernética)

![[Cyber_kill_chain.png]]

Pasos típicos de un ataque:

1. **Reconocimiento:** Buscar información de la víctima
2. **Armamento:** Crear herramientas (malware, exploits)
3. **Entrega:** Enviar herramienta (ej: phishing)
4. **Explotación:** Aprovechar una vulnerabilidad
5. **Instalación:** Ejecutar el malware
6. **Comando y control:** Comunicarse con el sistema infectado
7. **Acciones en el objetivo:** Robo de datos, daño, etc.

**Objetivo:** Romper el ataque en cualquier etapa.

# Pirámide del Dolor (David J. Bianco)

**Dificultad para el atacante si lo detectamos:**

![[Pyramid_of_pain.png]]

# Inteligencia de Código Abierto (OSINT)

Fuentes útiles:

- Artículos de noticias
- Foros públicos
- Reportes de seguridad
- Información publicada en redes sociales
- Chats en la dark web pueden servir

#  Herramientas mencionadas

- **MITRE ATT&CK Framework:** Base de datos pública que documenta tácticas, técnicas y procedimientos (TTPs) de atacantes conocidos (ejemplo: APT28, un grupo ruso).

# Procesos en CTI

1. **Recolección** de datos
2. **Validación y priorización** de datos
3. **Interpretación y análisis**
4. **Comunicación** de hallazgos (informes de amenazas)
5. **Uso** de la inteligencia en operaciones TI o en toma de decisiones estratégicas.

#  Ejemplos de comandos útiles en ciberdefensa

| Comando                   | Uso                            |
| ------------------------- | ------------------------------ |
| `netstat -an`             | Ver conexiones activas         |
| `whoami`                  | Ver usuario actual             |
| `ipconfig /all` (Windows) | Ver configuración IP           |
| `tcpdump` (Linux)         | Analizar tráfico de red        |
| `nmap -sV <IP>`           | Escaneo de puertos y servicios |
| `hashdeep -r <carpeta>`   | Ver hashes de archivos         |
| `grep` en logs            | Buscar patrones sospechosos    |
# Otra paginas utilies

[Para realizar inteligencia social](https://osintframework.com/)
[Como reaccionar contra amenazas](https://d3fend.mitre.org/) <- Se utilizara en la siguiente clase Clase_3