# Análisis Estadístico de Matrimonios en Ecuador 2023

Este proyecto realiza un **Análisis Exploratorio de Datos (EDA)** y visualización sobre los registros estadísticos de matrimonios ocurridos en Ecuador durante el año 2023, utilizando datos abiertos proporcionados por el **INEC** (Instituto Nacional de Estadística y Censos).

Dataset extraído de: [https://www.ecuadorencifras.gob.ec/matrimonios-divorcios/](https://www.ecuadorencifras.gob.ec/matrimonios-divorcios/)

## Estructura del Dataset

* **Archivo fuente:** `EMA_2023.csv` (separado por `;`)
* **Dimensiones originales:** 56,546 registros y 43 variables.
* **Variables principales analizadas:** Provincia y fecha de inscripción, edad, sexo, estado civil anterior, nivel de instrucción, autoidentificación étnica, número de matrimonios anteriores, hijos reconocidos y capitulaciones matrimoniales.

---
## Limpieza y Preparación de Datos

Durante el preprocesamiento del dataframe se aplicaron los siguientes criterios para garantizar la calidad del análisis:

1. **Tratamiento de valores faltantes:** Se estandarizaron las cadenas `"Sin información"` como valores nulos (`NaN`) al cargar el dataset.
2. **Depuración de registros:** Se eliminaron las filas correspondientes a columnas que presentaban menos de 10 valores nulos (`nac_1`, `nac_2`, fechas de nacimiento y `edad_1`), conservando más de 56500 registros válidos.
3. **Imputación de datos:**
   * `mcap_bie` (Capitulaciones matrimoniales): Los nulos se registraron con `"No"` (moda predominante).
   * `hijos_rec` (Hijos reconocidos) y `nmatant1`/`nmatant2` (Matrimonios anteriores): Los nulos se registraron con `0` y se convirtieron a tipo entero.
   * `est_civi1`/`est_civi2`: Los nulos se registraron con `"Soltero"`.
   * Variables sociodemográficas (`niv_inst`, `sabe_leer`, `p_etnica`): Los valores faltantes se etiquetaron explícitamente como `"Sin información"`.
4. **Ingeniería de características:**
   * Creación de la columna `tipo_pareja` para clasificar los matrimonios en *Distinto Sexo*, *Entre Hombres* y *Entre Mujeres*.
   * Creación de la columna `region` agrupando las provincias de inscripción en *Costa*, *Sierra*, *Amazonía*, *Insular* y *Exterior*.

---

## Preguntas de Negocio y Hallazgos

El análisis responde mediante visualizaciones gráficas a las siguientes interrogantes:

* **Matrimonios igualitarios:** En 2023 se registraron **342 matrimonios** entre personas del mismo sexo, lo que representa el **0.60%** del total de matrimonios en el país.
* **Rango de edad al contraer matrimonio:** Distribución de frecuencias diferenciada por sexo (hombres y mujeres) mediante histogramas y curvas de densidad.
* **Edad promedio por región:** Comparativa de la edad promedio al casarse por sexo en cada región geográfica del Ecuador frente al promedio nacional.
* **Distribución geográfica:** Identificación de las regiones con mayor volumen de inscripciones matrimoniales.

---

