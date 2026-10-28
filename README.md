# Análisis Predictivo Empresarial

Práctica académica de Business Analytics sobre análisis predictivo aplicado a datos de clientes, productos y ventas.

**Autores:** Jonathan Ortiz Calderon y Carolina Suarez Castro

**Repositorio:** [TALLER-PRACTICA-ANALISIS-PREDICTIVO](https://github.com/jonathanortizcalderon-droid/TALLER-PRACTICA-AN-LISIS-PREDICTIVO)

## Descripción

El notebook implementa un flujo completo de análisis predictivo:

1. Carga y exploración de los datos.
2. Limpieza y preparación de la información.
3. Integración de clientes, productos y ventas.
4. Construcción del ingreso neto mensual.
5. Selección de variables relevantes.
6. Entrenamiento de un modelo de regresión lineal.
7. Comparación contra un baseline basado en el mes anterior.
8. Evaluación mediante MAE, RMSE y R².
9. Generación de visualizaciones descriptivas, de evaluación y de proyección.
10. Proyección de ingresos para los próximos tres meses.
11. Interpretación de resultados y recomendaciones empresariales.

El archivo principal es:

[`analisis_predictivo_empresarial.ipynb`](./analisis_predictivo_empresarial.ipynb)

## Requisitos

- Python 3.10 o superior.
- Jupyter Notebook, JupyterLab o Visual Studio Code con la extensión **Jupyter**.
- Los siguientes paquetes de Python:

```text
numpy
pandas
matplotlib
seaborn
scikit-learn
openpyxl
```

## Estructura de archivos

Los archivos de datos deben permanecer en la misma carpeta que el notebook:

```text
Trabajo_4/
├── analisis_predictivo_empresarial.ipynb
├── clientes.json
├── productos.xlsx
├── ventas.csv
├── Práctica de Analítica Predictiva Empresarial.pdf
└── README.md
```

El notebook utiliza rutas relativas basadas en la carpeta de ejecución. Por este motivo, no se deben mover los archivos de datos a otra ubicación sin actualizar las rutas.

## Ejecución en Visual Studio Code

1. Instalar Python desde [python.org](https://www.python.org/downloads/) si aún no está instalado.
2. Instalar Visual Studio Code desde [code.visualstudio.com](https://code.visualstudio.com/).
3. Instalar las extensiones:
   - **Python**, de Microsoft.
   - **Jupyter**, de Microsoft.
4. Descargar o clonar este repositorio.
5. Abrir en Visual Studio Code la carpeta `Trabajo_4`.
6. Abrir el archivo `analisis_predictivo_empresarial.ipynb`.
7. Seleccionar un kernel de Python 3.10 o superior.
8. Instalar las dependencias desde la terminal integrada:

   ```powershell
   python -m pip install numpy pandas matplotlib seaborn scikit-learn openpyxl
   ```

9. Ejecutar las celdas en orden utilizando **Run All** o el botón de ejecución de cada celda.
10. Verificar que se muestren:
    - Tablas de exploración y limpieza.
    - Gráficos históricos.
    - Métricas del modelo.
    - Gráfico de evaluación temporal.
    - Proyección de ingresos.
    - Conclusiones y recomendaciones.

## Ejecución con entorno virtual recomendado

Desde PowerShell, ubicarse en la carpeta del proyecto:

```powershell
cd "C:\ruta\Trabajo_4"
```

Crear y activar un entorno virtual:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

Instalar las dependencias:

```powershell
python -m pip install --upgrade pip
python -m pip install numpy pandas matplotlib seaborn scikit-learn openpyxl jupyter
```

Iniciar Jupyter Notebook:

```powershell
jupyter notebook
```

Después, abrir `analisis_predictivo_empresarial.ipynb` y ejecutar todas las celdas.

También se puede iniciar JupyterLab:

```powershell
jupyter lab
```

## Ejecución desde la terminal

Para ejecutar el notebook completo y guardar las salidas, se puede utilizar `nbconvert`:

```powershell
python -m pip install nbconvert nbclient
python -m jupyter nbconvert --to notebook --execute analisis_predictivo_empresarial.ipynb --output analisis_predictivo_empresarial_ejecutado.ipynb
```

El archivo `analisis_predictivo_empresarial_ejecutado.ipynb` contendrá las tablas, métricas y visualizaciones producidas durante la ejecución.

## Flujo de análisis

### Carga y exploración

Se cargan:

- `clientes.json`: información de clientes, ciudades y fechas de registro.
- `productos.xlsx`: catálogo, categorías y precios.
- `ventas.csv`: fechas, clientes, productos, cantidades, descuentos y canales.

La exploración revisa dimensiones, valores faltantes y registros duplicados.

### Limpieza e integración

El notebook:

- Normaliza espacios y mayúsculas en categorías y códigos.
- Convierte fechas con los formatos presentes en los datos.
- Convierte descuentos porcentuales en proporciones numéricas.
- Conserva cantidades negativas como devoluciones.
- Integra las fuentes mediante `id_cliente` e `id_producto`.
- Calcula el ingreso neto:

```text
ingreso_neto = cantidad × precio × (1 - descuento)
```

### Modelo predictivo

El modelo utiliza:

- Tendencia temporal.
- Ingreso del mes anterior.
- Promedio móvil de los tres meses anteriores.

La separación entre entrenamiento y prueba respeta el orden temporal. Se utiliza regresión lineal y se compara con un baseline que pronostica el ingreso del mes anterior.

## Resultados esperados

Al ejecutar correctamente el notebook se generan:

1. Tablas de exploración de los tres archivos.
2. Indicadores de calidad de datos.
3. Serie histórica de ingresos mensuales.
4. Gráfico de ingresos por mes.
5. Gráfico de ingreso acumulado por canal.
6. Tabla de métricas MAE, RMSE y R².
7. Gráfico de valores reales frente a predicciones.
8. Tabla y gráfico de proyección para tres meses.
9. Interpretación de los resultados.
10. Conclusiones y recomendaciones empresariales.

## Solución de problemas

### No se encuentran los archivos de datos

Verificar que `clientes.json`, `productos.xlsx` y `ventas.csv` estén en la misma carpeta que el notebook y que el notebook se ejecute desde esa carpeta.

### Error `ModuleNotFoundError`

Instalar el paquete faltante. Por ejemplo:

```powershell
python -m pip install pandas
```

También se pueden instalar todas las dependencias nuevamente:

```powershell
python -m pip install numpy pandas matplotlib seaborn scikit-learn openpyxl jupyter nbconvert nbclient
```

### No aparecen los gráficos

Ejecutar nuevamente las celdas desde el inicio o utilizar **Run All**. Las visualizaciones se generan después de cargar y limpiar los datos. Si se ejecuta una celda intermedia sin ejecutar las anteriores, las variables necesarias todavía no estarán disponibles.

### El notebook se abre, pero no existe un kernel

En Visual Studio Code, seleccionar **Select Kernel** y elegir el entorno de Python instalado. Si no aparece, instalar la extensión Python y crear un entorno virtual siguiendo las instrucciones anteriores.

## Referencias

- Google Cloud. [¿Qué es el análisis predictivo?](https://cloud.google.com/learn/what-is-predictive-analytics?hl=es)
- *Guía Analítica Empresarial*, capítulo de análisis predictivo. Material suministrado para la actividad.
- Scikit-learn. [LinearRegression](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html)

