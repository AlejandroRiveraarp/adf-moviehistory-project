En esta etapa del pipeline se realiza la ingesta de datos crudos hacia la capa Bronze en Azure Data Lake.

📂 Dataset: Data_set_moviehistory_bronze

Este dataset está configurado en Azure Data Factory para leer archivos en formato JSON desde Azure Data Lake Storage.

⚙️ Características principales
Tipo de datos: JSON
Origen: Azure Data Lake Storage Gen2
Contenedor: bronce
Ruta dinámica: basada en parámetro de fecha
"folderPath": "@dataset().parametro_file_date"

Esto permite procesar datos de forma dinámica según la fecha de carga (ingestión incremental).

📊 Estructura de los datos

El dataset contiene información relacionada a países:

countryId (integer)
countryIsoCode (string)
countryName (string)
🔄 Lógica dentro del pipeline

Este dataset es utilizado como fuente de entrada en el pipeline de ingestión, permitiendo:

Leer archivos JSON desde rutas particionadas por fecha
Facilitar cargas incrementales
Mantener datos en estado crudo (raw data)
🧠 Enfoque de arquitectura

Este componente forma parte de una arquitectura tipo Medallion Architecture:

🥉 Bronze → Datos crudos (ingesta desde origen)
🥈 Silver → Transformaciones y limpieza
🥇 Gold → Datos listos para análisis
🚀 Beneficios
Escalabilidad mediante rutas dinámicas
Separación clara por capas (data lake)
Soporte para procesamiento incremental

## 🏗️ Arquitectura del Pipeline

- Azure Data Factory → Orquestación
- Azure Data Lake Gen2 → Almacenamiento (Bronze, Silver, Gold)
- Azure Databricks → Transformaciones
