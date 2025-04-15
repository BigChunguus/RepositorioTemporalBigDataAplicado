
# Monitoreo de un clúster AWS EMR con Prometheus y Grafana

Este proyecto documenta el proceso de configuración de un entorno de monitoreo para un clúster EMR de AWS utilizando **JMX Exporter**, **Prometheus** y **Grafana**. El objetivo es visualizar métricas relevantes del clúster en tiempo real y optimizar el rendimiento de los servicios distribuidos.

## Tecnologías Utilizadas

- **AWS EMR** (Elastic MapReduce)  
- **Apache Hadoop, Spark, Hive**  
- **JMX Exporter**  
- **Prometheus**  
- **Grafana**

---

## Estructura del Proyecto

### 1. Configuración del Clúster EMR
- Creación del clúster con Hadoop, Spark y Hive.
- 1 nodo maestro y 2 nodos core.
- Conexión vía SSH al nodo maestro.

### 2. Instalación y Configuración de JMX Exporter
- JMX Exporter extrae métricas JMX de las aplicaciones Java.
- Se configura en el NameNode para exponer métricas en formato Prometheus.
- Archivo `config.yml` con reglas de scraping básicas.
- Se reinicia el NameNode para aplicar cambios.

### 3. Despliegue de Prometheus y Grafana
- Se lanza una instancia EC2 para alojar Prometheus y Grafana.
- Configuración de puertos: 22 (SSH), 9090 (Prometheus), 3000 (Grafana).
- Se instalan y configuran ambas herramientas para conectar con el clúster EMR.

### 4. Visualización de Métricas
- Se crea un dashboard en Grafana para mostrar:
  - Uso de CPU y RAM.
  - Espacio en HDFS.
  - Estado del NameNode.
- Algunas funcionalidades no se completaron debido a fallas en Prometheus.

---

## Reflexión

### Métricas clave para EMR
- Uso de CPU, RAM, disco y red.
- Estado de YARN, HDFS y Spark.
- Estas métricas ayudan a detectar cuellos de botella, planificar capacidad y mantener la alta disponibilidad.

### Mejoras al JMX Exporter
- Filtrar métricas específicas relevantes.
- Añadir etiquetas personalizadas.
- Ajustar la frecuencia de scraping.
- Incluir métricas específicas de Spark o Hadoop.

### Ventajas de Prometheus + Grafana
- Open-source, sin costos por métrica.
- Visualización avanzada y personalizable.
- Integración fácil con AWS EMR y otros servicios.

---

## Conclusión

Prometheus y Grafana ofrecen una solución robusta, económica y flexible para monitorear clústeres EMR, facilitando la toma de decisiones basada en datos en tiempo real.
