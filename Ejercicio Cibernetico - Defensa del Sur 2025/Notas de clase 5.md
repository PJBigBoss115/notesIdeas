#  **Apuntes de Clase - Ciberseguridad, Derechos Humanos y Herramientas de Análisis**

## Derechos Humanos y Crímenes Cibernéticos

### ¿Se pueden aplicar los Derechos Humanos a los crímenes cibernéticos?
Sí, **los derechos humanos aplican siempre**, incluso en el entorno digital. No pierden vigencia aunque el medio sea virtual.

- **Importancia de los Derechos Humanos**:
    
    - Son **universales**, no pueden ser removidos ni negociados.
    - Se deben respetar **sin importar el contexto o medio**.
    - Aplican también a las víctimas de delitos cibernéticos, como el acoso, robo de identidad, trata de personas, etc.

### Ejemplos de crímenes cibernéticos que afectan derechos:
- **Engaños digitales** para reclutar personal laboral de forma forzada o con fines de trata.
- Daños a terceros mediante **difamación, suplantación de identidad o manipulación**.
- Ataques que afectan la **privacidad y dignidad** de las personas.

### Mención sobre legislación:
- Se discutió cómo **ciertas leyes en EE. UU.**, como la de **legítima defensa**, no aplican igual en Guatemala.
    
    - En Guatemala, la legítima defensa tiene parámetros más estrictos que en EE. UU.

##  **Greenbone/OpenVAS – Análisis de Vulnerabilidades**

### ¿Qué es una evaluación de vulnerabilidades?
Es un proceso para identificar **fallas o debilidades en una red** que podrían ser explotadas por un atacante.

### ¿Qué hace Greenbone/OpenVAS?
- Escanea redes para encontrar:
    - **Puertos abiertos**.
    - **Servicios inseguros**.
    - **Configuraciones mal hechas**.
        
- Es ideal para analizar **sistemas de código abierto**.
- Puede ser **lento** y **difícil de configurar**, y no tiene el mejor soporte técnico.

### Advertencias:
- Escanear dispositivos como **impresoras u otros equipos sensibles** puede dañarlos.

### Personalización del escaneo:
- Se pueden **crear tareas personalizadas**, usuarios y ajustar parámetros del escaneo para enfocarlo según el objetivo.

##  **Introducción a Security Onion**

Security Onion es una **plataforma de análisis de seguridad** compuesta por múltiples herramientas que trabajan en conjunto.

### Características:
- Utilizada para **pruebas de detección, recolección y análisis de incidentes**.
- Hoy se trabajó con un **único nodo**, aunque puede funcionar en modo distribuido.

### Componentes principales:
- **Zeek**: interpreta conversaciones completas en la red. Más legible y útil para el análisis.    
- **Suricata**: motor de detección de intrusos basado en firmas.
- **CyberChef**: permite visualizar y transformar datos (por ejemplo, de binario o hexadecimal a texto).
- **Kibana** y **Grafana**: herramientas de visualización para crear dashboards con datos de la red.
- **TheHive**: plataforma colaborativa para **gestión de incidentes**.
- **ANY.RUN**: sandbox para análisis de malware (link: [https://app.any.run](https://app.any.run)).

## Consolas y Herramientas en Security Onion

| Consola/Herramienta | Función principal                                                             |
| ------------------- | ----------------------------------------------------------------------------- |
| **Hunter Console**  | Permite cambiar entre aplicaciones y compartir datos entre ellas.             |
| **Alert Console**   | Muestra alertas generadas por Suricata o Zeek.                                |
| **PCAP Console**    | Permite capturar y analizar tráfico de red en formato PCAP.                   |
| **Analyst Console** | Muestra servicios activos y permite análisis profundo.                        |
| **Kibana**          | Visualiza datos y ayuda a crear líneas base de comportamiento.                |
| **Grafana**         | Dashboard dinámico con visualizaciones en tiempo real.                        |
| **CyberChef**       | Visualiza y transforma datos en varios formatos (hex, base64, binario, etc.). |

## Despliegue de Security Onion

### Tipos de despliegue:
- **Independiente (Standalone)**: Todo corre en una sola máquina.
- **Distribuido**: Cada nodo cumple una función específica.

### Tipos de nodos:
- **Storage Node**: Almacena grandes cantidades de datos.
- **Master Node**: Controla y coordina el sistema.
- **Forward Node**: Redirige datos hacia el nodo maestro.