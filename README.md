# Predicción inteligente de gasto en clientes e-commerce

Este repositorio aloja el proyecto del **Módulo 6: Predicción inteligente de gasto en clientes e-commerce**, perteneciente al **"Bootcamp Fundamentos de Ciencias de Datos 2026"** de **Talento Digital para Chile - SENCE**.

Como analista de datos junior del Departamento de Analítica Comercial, se nos ha encomendado construir un modelo predictivo robusto. La meta es estimar el monto de compra que se espera de un cliente basándonos en variables históricas como el comportamiento en línea, duración de membresía y edad, utilizando técnicas de aprendizaje de máquina supervisado (regresión) y su posterior optimización.

## Estructura del Proyecto

- [`main.ipynb`](main.ipynb): Notebook interactivo principal que contiene todo el desarrollo del caso paso a paso. Combina explicaciones teóricas con la implementación del código; limpieza de datos, entrenamiento y validación de modelos ([▶ Ver en nbviewer](https://nbviewer.org/github/c-mena/dsb26-supervised-machine-learning/blob/main/main.ipynb)).
- [`data/data.csv`](data/data.csv): Dataset original a utilizar ([Ecommerce Customer Data](https://www.kaggle.com/datasets/iabdulw/ecommerce-customer-data)), equivalente al registro histórico de compras.
- [`README.md`](README.md): Archivo de presentación y documentación del repositorio (este documento).
- [`technical_report.md`](technical_report.md): Reporte técnico en formato narrativo que incluye las justificaciones teóricas, insights y reflexiones obtenidas a partir de los datos.

## Requisitos y Tecnologías

Para desplegar este proyecto y reproducir los experimentos, es necesario disponer del gestor de paquetes `uv` y un entorno de Python conformado con las siguientes bibliotecas:

- **pandas**: Esencial para manipulación, limpieza y estructuración tabular de los datos.
- **numpy**: Necesario para realizar operaciones matriciales y simular distribuciones estadísticas (ej. imputación de edades).
- **scikit-learn**: La biblioteca núcleo para las rutinas de Machine Learning, incluyendo preprocesamiento, partición de los datos (CV), y para el instanciamiento de regresiones, ensamble de árboles (Boosting) y métricas de error corporativas.
- **matplotlib** y **seaborn**: Herramientas por excelencia para la generación de gráficas estáticas, distribuciones de variables y análisis del rendimiento (curvas de sobreajuste).
- **ipykernel**: Ejecución del cuaderno en entorno Jupyter / VS Code.

## Instalación y Despliegue Local

### 1. Clonar el repositorio

```bash
git clone https://github.com/c-mena/dsb26-supervised-machine-learning
cd dsb26-supervised-machine-learning
```

### 2. Crear e inicializar el entorno virtual con `uv`

Para asegurar la máxima reproducibilidad y eficiencia en la gestión de entornos, se recomienda usar [uv](https://docs.astral.sh/uv/). Esto ayuda aislar y no contaminar tu versión global de Python de forma extremadamente veloz.

```bash
uv venv
```

### 3. Activar el entorno virtual

```bash
# Windows
.venv\Scripts\activate

# macOS / Linux
source .venv/bin/activate
```

### 4. Instalar dependencias

Recomendamos instalar y sincronizar las bibliotecas requeridas utilizando el archivo `pyproject.toml` incluido en el proyecto, garantizando operar con las dependencias exactas y probadas:

```bash
uv sync
```

### 5. Ejecutar el proyecto

La alternativa recomendada para inicializar y observar el proyecto es emplear **Visual Studio Code (VS Code)** con su extensión de **Jupyter** instalada. Sólo debes abrir la carpeta del repositorio en VS Code, seleccionar tu entorno virtual `.venv` como tu Kernel de ejecución, y abrir el archivo `main.ipynb` para ejecutar el código y visualizar sus correspondientes anotaciones en simultáneo.

_(Otra alternativa válida, desde la consola y con tu entorno activo, es ejecutar el comando `jupyter notebook` para levantar el servidor y entrar a `main.ipynb` directamente mediante tu navegador web)._

---
