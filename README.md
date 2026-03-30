```markdown
# Detección y Análisis Morfológico de Cañas (Sugar Cane)

Este proyecto implementa un sistema para la detección, segmentación, y análisis morfológico de cañas a partir de imágenes. Utiliza técnicas de procesamiento de imágenes con OpenCV y un modelo de aprendizaje profundo (Convolutional Neural Network) entrenado con TensorFlow/Keras para identificar cañas, medir su longitud, y detectar nudos y entrenudos, proporcionando métricas clave para el análisis agrícola.

## Características Principales

*   **Detección de Cañas**: Un modelo de IA clasifica si una imagen contiene una caña o no.
*   **Eliminación de Fondo**: Segmentación automática para aislar la caña del fondo de la imagen.
*   **Detección de Contornos**: Identificación precisa del contorno de la caña.
*   **Medición de Longitud**: Cálculo automático de la longitud aproximada de la caña en metros.
*   **Detección de Nudos y Entrenudos**: Identificación de los nudos a lo largo de la caña y cálculo de las distancias entre ellos, incluyendo la distancia promedio.
*   **Visualización de Resultados**: Generación de imágenes anotadas mostrando la caña detectada, segmentada, con medidas y nudos marcados.
*   **Salida Estructurada**: Exportación de resultados de análisis en formato JSON.

## Tecnologías Utilizadas

*   Python 3.x
*   OpenCV
*   NumPy
*   Matplotlib
*   PIL (Pillow)
*   TensorFlow / Keras
*   Scipy
*   `rembg` (para eliminación de fondo programática)
*   Google Colab (para desarrollo y ejecución)

## Instalación y Configuración

1.  **Clonar el Repositorio**:
    ```bash
    git clone <URL_DE_TU_REPOSITORIO>
    cd <nombre_de_tu_repositorio>
    ```
2.  **Configurar Entorno (Google Colab)**:
    Este proyecto fue desarrollado en Google Colab. Para ejecutarlo:
    *   Abre el archivo `.ipynb` en Google Colab.
    *   Asegúrate de montar tu Google Drive si el modelo o los datasets se encuentran allí:
        ```python
        from google.colab import drive
        drive.mount('/content/drive')
        ```
    *   Instala las dependencias necesarias. Algunas pueden estar preinstaladas en Colab:
        ```bash
        !pip install opencv-python numpy matplotlib pillow tensorflow scipy rembg
        ```

## Uso

El cuaderno está organizado para guiar a través de los pasos de preprocesamiento, entrenamiento del modelo (si es necesario) y la inferencia final. La sección clave para la inferencia y el análisis es la que utiliza el modelo entrenado para procesar una nueva imagen.

### Ejecutar el Análisis

1.  **Cargar el modelo**: Asegúrate de que el modelo `modelo_caña.keras` esté cargado (si no lo has entrenado en esta sesión, cárgalo desde Google Drive).
    ```python
    from tensorflow.keras.models import load_model
    modelo = load_model('/content/drive/MyDrive/modelo_caña.keras')
    ```
2.  **Subir una imagen**: Utiliza el widget de `files.upload()` para subir la imagen de una caña que deseas analizar.
3.  **Ejecutar la celda de análisis**: La celda final (como la celda `XVvKw8S4w9hL` en tu notebook) procesará la imagen, realizará la detección, las mediciones y generará los resultados en JSON.

## Resultados y Ejemplos

A continuación, se muestran ejemplos visuales de las etapas del proceso y los resultados obtenidos.

### Imagen Original

![Imagen Original](assets/cana_original.jpg)
_Una caña lista para ser analizada._

### Caña Recortada (Sin Fondo)

Se utiliza el modelo de segmentación para eliminar el fondo de la imagen, aislando la caña.

![Caña Recortada (Sin Fondo)](assets/cana_sin_fondo.jpg)

### Caña Detectada con Contorno y Medida

Se detecta el contorno principal y se calcula la longitud aproximada de la caña.

![Caña Medida Automáticamente](assets/cana_medida.jpg)
_Largo aproximado de la caña: X.XX metros._

### Nudos y Entrenudos Detectados

Identificación de los nudos (líneas rojas) y los entrenudos (rectángulos verdes) con sus respectivas distancias.

![Nudos Detectados](assets/nudos_detectados.jpg)
![Entrenudos Detectados](assets/entrenudos_detectados.jpg)

### Resultados en JSON

Un ejemplo de la salida estructurada que contiene todas las métricas calculadas:

```json
<!-- Reemplazar con la salida JSON real de '/content/resultados_caña.json' -->
{
    "caña_detectada": true,
    "altura_caña": 1.09,
    "nudos_detectados": 5,
    "distancias_entre_nudos": [
        {
            "nudo": 1,
            "distancia": 0.21
        },
        {
            "nudo": 2,
            "distancia": 0.22
        },
        {
            "nudo": 3,
            "distancia": 0.20
        },
        {
            "nudo": 4,
            "distancia": 0.23
        }
    ],
    "distancia_promedio_nudos": 0.22,
    "entrenudos_detectados": 4,
    "distancias_entre_entrenudos": [
        0.21,
        0.22,
        0.20,
        0.23
    ]
}
```
_**Nota**: Deberás crear una carpeta `assets` en tu repositorio y guardar las imágenes generadas allí, y luego actualizar las rutas en este archivo README para que se muestren correctamente._
```
