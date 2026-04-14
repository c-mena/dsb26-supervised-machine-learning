# Reporte Técnico: Predicción inteligente de gasto en clientes e-commerce

## Resumen Ejecutivo de Hallazgos

A lo largo de este proyecto, hemos implementado exitosamente un pipeline de Machine Learning para estimar el gasto anual ("Yearly Amount Spent") de clientes en una plataforma de e-commerce. A continuación, presento los hallazgos y decisiones más relevantes derivados de este ejercicio:

- **Idoneidad del problema**: Se definió el caso de negocio explícitamente como un problema de regresión al ser la variable dependiente de naturaleza continua. El modelamiento predictivo inicial con **Regresión Lineal Simple/Múltiple** demostró ser una línea base muy eficiente.
- **Predictores dominantes**: Las métricas exploratorias y los coeficientes del modelo han revelado que la variable `Length of Membership` (Tiempo siendo asociado) influye positivamente y con mayor fuerza en el gasto anual invertido por los clientes, indicando la rentabilidad de las estrategias dirigidas a la lealtad y retención.
- **Optimización del sesgo-varianza**: La aplicación de K-Folds (Validación cruzada) permitió robustecer nuestras evaluaciones de desempeño y advertir una bajísima inclinación hacia el sobreajuste (overfitting) en los modelos entrenados.
- **Desempeño de modelos de Ensamble**: Al probar algoritmos basados en Gradient Boosting, hemos visto cómo métodos más avanzados, que involucran mayor coste computacional y tiempo de ajuste de hiperparámetros, no siempre pueden corregir iterativamente los residuales, mejorando el desempeño general frente a modelos lineales, cuando la naturaleza de los datos es lineal.

## Justificación de Decisiones Técnicas

### 1. Adecuación del modelo y tipo de problema

El uso de una función continua para predecir dinero obliga a descartar clasificadores, ya que estos tratan de identificar categorías (clases discretas). Un intento simulado de utilizar KNN como clasificador solo pudo lograrse al transformar artificialmente nuestro target en rangos (ej., "Bajo Gasto", "Alto Gasto"), demostrando que la naturaleza original contínua perdía precisión granular.

### 2. Algoritmos seleccionados

1. **Regresión Lineal**: Elegido por su gran interpretabilidad. Como es el primer modelo en nuestra aproximación, nos permite trazar una pendiente e inferir el peso exacto de cada factor sobre el output final.
2. **Gradient Boosting Regressor**: Sirvió como contrapunto avanzado. Al construir árboles de decisión de forma secuencial tratando de mitigar el error del árbol previo, este modelo está intrínsecamente enfocado en la minimización del riesgo, haciéndolo ideal frente a interacciones no lineales latentes en grandes conjuntos de datos de consumidores.

### 3. Elección de Métricas de Evaluación

Para asegurar que los modelos están midiendo nuestro éxito de manera correcta se emplearon las siguientes métricas:

- **MAE (Mean Absolute Error):** Como es un cálculo de la magnitud promedio de nuestros errores asumiendo un peso parejo y expresado en la unidad subyacente del problema (Dólares), resulta idóneo para que los ejecutivos comerciales tengan una interpretación directa del margen de equivocación.
- **RMSE (Root Mean Squared Error):** Es crítico para penalizar severamente a nuestro modelo cuando da predicciones excesivamente lejanas de la realidad (outliers).
- **R² (Coeficiente de Determinación):** Indica cuánta de nuestra varianza en el comportamiento está siendo explicada por las variables de entrada. Obtuvimos valores muy buenos, lo que garantiza la viabilidad de producción.

### 4. Optimizaciones en el preprocesamiento

Durante la preparación de los datos:

- Todas las variables numéricas contínuas fueron sujetas a **Standardized Scaling**. Ésta estandarización remueve distancias de magnitud garantizando de que variables como la *Edad Simulada* y los *Minutos en la App* participen per cápita del análisis sin distorsiones matemáticas y ayudan a converger a nuestros modelos más velozmente.
- Se ha aplicado técnica de ajuste y regularización **Ridge y Lasso**, previniendo que los coeficientes escalen artificialmente hacia variables no determinantes a lo largo del tiempo.

## Conclusiones e Insights de Negocio

Desde una perspectiva analítica en la etapa exploratoria de coeficientes de Regresión, se calculó e interpretó estadísticamente la magnitud de los factores impulsores del comportamiento de gasto del cliente. Encontramos categóricamente que:

- **`Length of Membership` ($\approx 57$) y `Time on App` ($\approx 37$)** ostentan un claro protagonismo. Incrementar estos factores en un individuo sube matemáticamente el volumen de gasto predicho en enormes proporciones positivas.
- En contraste absoluto, el **tiempo navegando por la Web** (`Time on Website` $\approx 0.2$), elementos estadísticos como la **Edad** ($\approx 0.8$) y los proveedores de dominio de email aportaron variaciones minúsculas y nula significancia al negocio.

**Para la audiencia no técnica y decisores de marketing:**
La conclusión principal extraída se traduce en dos grandes acciones apoyadas en nuestra matemática predictora empírica:

1. **Lealtad por sobre volumen:** Enfocar estratégicamente el capital operativo hacia la **retención** antes que la adquisición en otros canales. Dado que el "Tiempo de Membresía" empuja mayormente la ecuación de éxito monetario, sugerimos implementar agresivamente un programa de afiliación por *tiers* o niveles de lealtad incentivando al usuario a no desvincularse con los años.
2. **Prioridad operativa Móvil:** Reducir o auditar las inversiones operativas de interfaz "Web" y destinar ese flujo directamente hacia mejoras integrales en la **App Móvil**, puesto que es únicamente a través de la App donde verdaderamente se rentabilizan y monetizan los minutos interactuados por un cliente e-commerce activo.

---
