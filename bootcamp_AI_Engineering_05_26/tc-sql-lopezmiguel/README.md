<div align="center">

# 📊 ElectroMarket — Modelo de datos en BigQuery

### Proyecto de modelado y análisis de datos para una tienda online ficticia

![BigQuery](https://img.shields.io/badge/BigQuery-Google_Cloud-4285F4?style=for-the-badge&logo=google-cloud&logoColor=white)
![Python](https://img.shields.io/badge/Python-3.12+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.0+-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Faker](https://img.shields.io/badge/Faker-20.0+-FF6B6B?style=for-the-badge&logo=python&logoColor=white)
![3FN](https://img.shields.io/badge/Normalización-3FN-4CAF50?style=for-the-badge)

<br>

![Status](https://img.shields.io/badge/status-completado-brightgreen?style=flat-square)
![Version](https://img.shields.io/badge/version-1.0.0-blue?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)

</div>

# Tabla de Contenido

- [🎯 Descripción General](#-descripción-general)
- [✨ Características Principales](#-características-principales)
- [📊 Modelo de Datos](#-modelo-de-datos)
- [🏗️ Estructura del Proyecto](#️-estructura-del-proyecto)
- [💻 Tecnologías Utilizadas](#-tecnologías-utilizadas)
- [🗄️ Datos Generados](#️-datos-generados)
- [⚙️ Instalación y Configuración](#️-instalación-y-configuración)
- [🚀 Ejecución del Proyecto](#-ejecución-del-proyecto)
- [📈 Consultas Analíticas](#-consultas-analíticas)
- [📚 Dependencias Principales](#-dependencias-principales)
- [🔒 Seguridad](#-seguridad)
- [📄 Licencia](#-licencia)

---

<div align="center">

## 🎯 Descripción General

</div>

**ElectroMarket** es un proyecto de modelado y análisis de datos para una tienda online ficticia, desarrollado con **Google BigQuery**, Python y Jupyter Notebook.

El proyecto implementa un modelo relacional completamente normalizado hasta **Tercera Forma Normal (3FN)**, genera datos sintéticos realistas y ejecuta consultas analíticas sobre el modelo en la nube de Google.

**¿Qué problema resuelve?**  
Proporciona un entorno de datos completo y profesional para demostrar habilidades de:
- Modelado de datos relacionales
- Generación de datos sintéticos con Faker
- Trabajo con BigQuery en Google Cloud
- Análisis de datos y consultas SQL avanzadas
- Integración de Python con servicios en la nube

**Público objetivo:** Científicos de datos, ingenieros de datos, analistas de BI, estudiantes y profesionales que quieran demostrar su dominio de BigQuery y modelado de datos.

---

<div align="center">

## ✨ Características Principales

</div>

| Funcionalidad | Estado | Descripción |
|--------------|--------|-------------|
| ✅ Modelo Normalizado (3FN) | Completo | 7 entidades relacionadas con integridad referencial |
| ✅ Datos Sintéticos | Completo | Generación realista con Faker para todas las tablas |
| ✅ BigQuery Integration | Completo | Conexión directa con Google BigQuery API |
| ✅ Notebooks Orquestados | Completo | Flujo de trabajo paso a paso en 3 notebooks |
| ✅ Consultas Analíticas | Completo | 6 consultas de negocio sobre los datos |
| ✅ Validación de Datos | Completo | Verificación de integridad y cantidad de registros |
| ✅ Documentación ER | Completo | Diagrama Entidad-Relación incluido |
| ✅ Gestión de Credenciales | Completo | Uso de variables de entorno para seguridad |
| ✅ Datos Realistas | Completo | Nombres, países, fechas y precios coherentes |
| ✅ Carga Automatizada | Completo | Inserción de DataFrames directamente en BigQuery |

---

<div align="center">

## 📊 Modelo de Datos

</div>

El modelo está compuesto por **7 entidades** totalmente normalizadas:

### 📋 Entidades

| Entidad | Descripción |
|---------|-------------|
| `customers` | Información de los clientes (nombre, email, país, fecha de registro) |
| `categories` | Categorías de productos (nombre, descripción) |
| `products` | Catálogo de productos (nombre, precio, categoría) |
| `orders` | Pedidos realizados (cliente, fecha, estado, total) |
| `order_items` | Líneas de cada pedido (producto, cantidad, precio unitario) |
| `payments` | Pagos asociados a los pedidos (método, fecha, importe) |
| `reviews` | Reseñas asociadas a líneas de pedido (valoración, comentario) |

### 🔗 Relaciones Principales

~~~
mermaid
graph LR
    A[customers] -->|1:N| B[orders]
    C[categories] -->|1:N| D[products]
    B -->|1:N| E[order_items]
    D -->|1:N| E
    B -->|1:N| F[payments]
    E -->|1:N| G[reviews]
    
    style A fill:#f9f,stroke:#333,stroke-width:2px
    style C fill:#f9f,stroke:#333,stroke-width:2px
    style D fill:#bbf,stroke:#333,stroke-width:2px
    style B fill:#bbf,stroke:#333,stroke-width:2px
    style E fill:#bfb,stroke:#333,stroke-width:2px
    style F fill:#fbb,stroke:#333,stroke-width:2px
    style G fill:#ffb,stroke:#333,stroke-width:2px
~~~

Nota: La relación N:M entre orders y products se resuelve mediante la tabla asociativa order_items.

El diagrama completo se encuentra en:


docs/er_diagram.png
<div align="center">
🏗️ Estructura del Proyecto
</div>
El proyecto está organizado de forma clara y modular:

~~~
parte_2_modelo_bigquery/
├── 📁 docs/
│   └── 📄 er_diagram.png              # Diagrama Entidad-Relación
│
├── 📁 notebooks/
│   ├── 📓 01_setup_bigquery.ipynb     # Configuración de BigQuery
│   ├── 📓 02_generate_data.ipynb      # Generación y carga de datos
│   └── 📓 03_queries_verification.ipynb # Consultas analíticas
│
├── 📁 credentials/                     # Credenciales (ignorado por git)
│   └── 🔒 tu-archivo-credenciales.json
│
├── 📄 .env                             # Variables de entorno (ignorado)
├── 📄 .env.example                     # Ejemplo de variables de entorno
├── 📄 requirements.txt                 # Dependencias de Python
├── 📄 .gitignore                       # Archivos ignorados
└── 📄 README.md                        # Documentación principal
~~~


<div align="center">
💻 Tecnologías Utilizadas
| Categoría                | Tecnología            | Versión | Propósito                       |
| ------------------------ | --------------------- | ------- | ------------------------------- |
| 🐍 Lenguaje              | Python                | 3.12+   | Lenguaje principal              |
| 📓 Entorno               | Jupyter Notebook      | —       | Desarrollo interactivo          |
| ☁️ Cloud Platform        | Google Cloud Platform | —       | Infraestructura en la nube      |
| 🗄️ Data Warehouse       | Google BigQuery       | —       | Almacenamiento y consultas SQL  |
| 🐼 Manipulación de Datos | Pandas                | 2.0+    | Procesamiento de DataFrames     |
| 🎲 Generación de Datos   | Faker                 | 20.0+   | Generación de datos sintéticos  |
| 🔐 Variables de Entorno  | python-dotenv         | 1.0+    | Gestión de variables de entorno |
| 🔌 BigQuery Client       | google-cloud-bigquery | 3.0+    | API de BigQuery para Python     |
| 🔄 Integración           | pandas-gbq            | 0.19+   | Carga de DataFrames a BigQuery  |
| 🔢 Tipado                | db-dtypes             | —       | Tipos de datos para BigQuery    |
| ⚡ Serialización          | pyarrow               | —       | Serialización eficiente         |
| 💻 IDE                   | VS Code / Jupyter     | —       | Entorno de desarrollo           |

<div align="center">
🗄️ Datos Generados
</div>

| Entidad       |  Registros | Descripción                                                      |
| ------------- | ---------: | ---------------------------------------------------------------- |
| `categories`  |          7 | Categorías predefinidas como Electrónica, Hogar, Deportes, etc.  |
| `customers`   |        500 | Clientes con nombres, emails y países de todo el mundo           |
| `products`    |         70 | Productos distribuidos en las 7 categorías con precios realistas |
| `orders`      |      2.000 | Pedidos con fechas, estados y totales calculados                 |
| `order_items` |      5.044 | Líneas de pedido con cantidades y precios                        |
| `payments`    |      2.000 | Pagos con diferentes métodos como tarjeta, PayPal, etc.          |
| `reviews`     |        306 | Reseñas con valoraciones del 1 al 5 y comentarios                |
| **TOTAL**     | **~7.927** | **Volumen de datos completo para análisis**                      |


<div align="center">
⚙️ Instalación y Configuración
</div>
📋 Prerrequisitos

Antes de comenzar, es necesario disponer de:

🐍 Python 3.12 o superior
☁️ Cuenta de Google Cloud
📁 Proyecto de Google Cloud activo
🔌 BigQuery API habilitada
🔑 Service Account con permisos para BigQuery
📓 Jupyter Notebook o VS Code con soporte para notebooks
🚀 Pasos de Instalación




1️⃣ Clonar el repositorio

~~~
git clone <URL_DEL_REPOSITORIO>
cd <NOMBRE_DEL_REPOSITORIO>
~~~

2️⃣ Crear el entorno virtual
En Windows con Git Bash:
~~~
python -m venv .venv
source .venv/Scripts/activate
~~~
En PowerShell:
~~~
powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
~~~
En Linux/Mac:
~~~
python3 -m venv .venv
source .venv/bin/activate
~~~
3️⃣ Instalar las dependencias
~~~
pip install -r requirements.txt
~~~
4️⃣ Configurar Google Cloud
Crear una Service Account en Google Cloud Console

Descargar la clave JSON de la Service Account

Guardar el archivo JSON en la carpeta credentials/
~~~
credentials/
└── tu-archivo-credenciales.json
~~~
⚠️ Importante: Nunca subir el archivo de credenciales al repositorio

5️⃣ Configurar variables de entorno
Crear un archivo .env en la raíz del proyecto a partir de .env.example:
~~~
GCP_PROJECT_ID=tu-proyecto-gcp
BQ_DATASET_ID=electromarket
GOOGLE_APPLICATION_CREDENTIALS=credentials/tu-archivo-credenciales.json
~~~
<div align="center">
🚀 Ejecución del Proyecto
</div>
Los notebooks deben ejecutarse en el siguiente orden:

1️⃣ Configuración de BigQuery
Abrir:
~~~
notebooks/01_setup_bigquery.ipynb
~~~
Este notebook:

✅ Carga las variables de entorno

✅ Configura las credenciales

✅ Crea la conexión con BigQuery

✅ Crea/verifica el dataset electromarket

✅ Define los esquemas de las 7 tablas

✅ Crea/verifica las tablas en BigQuery

2️⃣ Generación y carga de datos
Abrir:
~~~
notebooks/02_generate_data.ipynb
~~~
Este notebook:

✅ Genera datos sintéticos utilizando Python y Faker

✅ Crea registros para las 7 entidades

✅ Valida la integridad de los datos

✅ Carga los DataFrames en BigQuery

✅ Verifica el número de registros cargados

3️⃣ Consultas analíticas y verificación
Abrir:
~~~
notebooks/03_queries_verification.ipynb
~~~
Este notebook:

✅ Ejecuta consultas analíticas directamente sobre BigQuery

✅ Realiza verificaciones de integridad

✅ Genera insights de negocio

<div align="center">
📈 Consultas Analíticas
</div>
El proyecto incluye 6 consultas analíticas que responden preguntas de negocio clave:

|  # | Consulta                                 | Descripción                                  |
| -: | ---------------------------------------- | -------------------------------------------- |
|  1 | 📊 Ingresos por mes                      | Análisis de tendencias mensuales de ingresos |
|  2 | 🏆 Productos más vendidos                | Ranking de productos por cantidad vendida    |
|  3 | 🌍 Distribución de clientes por país     | Análisis geográfico de la base de clientes   |
|  4 | ⏱️ Tiempo medio de entrega               | Métricas de eficiencia en entregas           |
|  5 | 💰 Ingresos y margen bruto por categoría | Rentabilidad por categoría de producto       |
|  6 | 📍 Distribución de estados de pedidos    | Análisis del ciclo de vida de los pedidos    |

Cada consulta está optimizada para BigQuery y utiliza funciones SQL avanzadas.

<div align="center">

📚 Dependencias Principales
</div>

~~~
pandas>=2.0.0                # Manipulación y análisis de datos
faker>=20.0.0                # Generación de datos sintéticos
python-dotenv>=1.0.0         # Gestión de variables de entorno
google-cloud-bigquery>=3.0.0 # Cliente oficial de BigQuery
pandas-gbq>=0.19.0           # Carga de DataFrames a BigQuery
db-dtypes>=1.0.0             # Tipos de datos para BigQuery
pyarrow>=12.0.0              # Serialización eficiente
~~~

Las versiones completas se encuentran en:
~~~
requirements.txt
~~~

<div align="center">
🔒 Seguridad
</div>
✅ Buenas Prácticas Implementadas
✅ Uso de variables de entorno para credenciales

✅ Archivos .env ignorados por .gitignore

✅ Claves de Service Account no versionadas

✅ Dataset con permisos limitados

✅ Sin exposición de secretos en el código

✅ Documentación clara de requisitos de seguridad

❌ Archivos que NUNCA deben subirse al repositorio
❌ Archivos .env

❌ Claves privadas de Service Account

❌ Archivos JSON de credenciales

❌ Cualquier otro secreto o credencial de Google Cloud

Estas rutas están incluidas en .gitignore.

<div align="center">
📄 Licencia
</div>
Este proyecto está bajo la licencia MIT - ver el archivo LICENSE para más detalles.

<div align="center">
⭐ ¡Gracias por visitar este proyecto!
Si te ha sido útil, no olvides darle una ⭐ en GitHub.

</div



